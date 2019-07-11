---
title: Migration d’extensibilité du concepteur XAML
ms.date: 07/09/2019
ms.topic: conceptual
author: lutzroeder
ms.author: lutzr
manager: jillfra
dev_langs:
- csharp
- vb
monikerRange: vs-2019
ms.openlocfilehash: 52bc8a6a0097d255891f4b6111a27bff85091bec
ms.sourcegitcommit: 208395bc122f8d3dae3f5e5960c42981cc368310
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67784489"
---
# <a name="xaml-designer-extensibility-migration"></a>Migration d’extensibilité du concepteur XAML

À partir de Visual Studio 2019 version 16.1 en version préliminaire publique, le concepteur XAML prend en charge les deux architectures différentes : l’architecture du Concepteur d’isolation et l’architecture de surface d’isolation plus récente. Cette transition de l’architecture est nécessaire pour prendre en charge les runtimes de cibles qui ne peut pas être hébergés dans un processus de .NET Framework. Passage à l’architecture d’isolation surface introduit des changements majeurs au modèle d’extensibilité de fournisseurs tiers. Cet article décrit les modifications.

**Isolation concepteur** est utilisé par le Concepteur WPF pour les projets qui ciblent le .NET Framework et prend en charge *. design.dll* extensions. Code utilisateur, des bibliothèques de contrôles et des extensions tierces sont chargées dans un processus externe (*XDesProc.exe*), ainsi que les panneaux de concepteur et le code concepteur réel.

**Isolation de la surface** est utilisé par le concepteur UWP. Il est également utilisé par le Concepteur WPF pour les projets qui ciblent .NET Core. Dans l’isolation de l’aire de conception, les bibliothèques de code et le contrôle utilisateur uniquement sont chargés dans un processus séparé, tandis que le concepteur et ses panneaux est chargés dans le processus de Visual Studio (*DevEnv.exe*). Le runtime utilisé pour l’exécution des bibliothèques de code et le contrôle utilisateur est différent de celle utilisée par le .NET Framework pour le concepteur réel et d’un code d’extensibilité par des tiers.

![extensibility-migration-architecture](media/xaml-designer-extensibility-migration-architecture.png)

En raison de cette transition de l’architecture, des extensions tierces ne sont plus chargées dans le même processus que les bibliothèques de contrôle tiers. Les extensions peuvent ne plus ont des dépendances directes sur les bibliothèques de contrôles ou accéder directement aux objets d’exécution. Les extensions qui ont été écrits précédemment pour l’architecture de concepteur d’isolation à l’aide de la *Microsoft.Windows.Extensibility.dll* API doit être migré vers une nouvelle approche pour travailler avec l’architecture d’isolation aire de conception. Dans la pratique, une extension existante sera doivent être compilées par rapport à nouveaux assemblys d’API d’extensibilité. Types d’accès au contrôle de l’exécution [typeof](/dotnet/csharp/language-reference/keywords/typeof) ou instances d’exécution doivent être remplacés ou supprimés, car les bibliothèques de contrôles sont désormais chargés dans un processus différent.

## <a name="new-extensibility-api-assemblies"></a>Nouveaux assemblys de l’API d’extensibilité

Les nouveaux assemblys d’API d’extensibilité sont similaires aux assemblys de l’API d’extensibilité existants mais suivent un schéma d’affectation de noms différent afin de les différencier. De même, les noms de l’espace de noms ont changé pour refléter les nouveaux noms d’assembly.

| Concepteur isolation d’assembly de l’API            | Ensemble d’isolation surface API                       |
|:------------------------------------------ |:---------------------------------------------------- |
| Microsoft.Windows.Design.Extensibility.dll | Microsoft.VisualStudio.DesignTools.Extensibility.dll |
| Microsoft.Windows.Design.Interaction.dll   | Microsoft.VisualStudio.DesignTools.Interaction.dll   |

## <a name="new-file-extension-and-discovery"></a>Découverte et la nouvelle extension de fichier

Au lieu d’utiliser le *. design.dll* extension, nouvelle surface extensions seront découverts à l’aide du fichier le *. designtools.dll* extension de fichier. *. design.dll* et *. designtools.dll* extensions peuvent exister dans le même *conception* sous-dossier.

Bien que les bibliothèques de contrôle tiers sont compilés pour le runtime cible réelle (.NET Core ou UWP), le *. designtools.dll* extension doit toujours être compilée comme un assembly .NET Framework.

## <a name="decouple-attribute-tables-from-runtime-types"></a>Dissocier les tables d’attributs à partir des types de runtime

N’autorise pas le modèle d’extensibilité d’isolation de surface d’exposition pour les extensions dépendent des bibliothèques de contrôles réels, et par conséquent, les extensions ne peuvent pas référencer des types à partir de la bibliothèque de contrôles. Par exemple, *MyLibrary.designtools.dll* ne doit pas avoir une dépendance *MyLibrary.dll*.

Ces dépendances ont été plus courantes lors de l’enregistrement des métadonnées pour les types par le biais de tables d’attributs. Types de code d’extension qui fait référence de bibliothèque de contrôles directement par le biais de [typeof](/dotnet/csharp/language-reference/keywords/typeof) ([GetType](/dotnet/visual-basic/language-reference/operators/gettype-operator) en Visual Basic) est substituée dans les nouvelles API en utilisant des noms de type basé sur chaîne :

```csharp
using Microsoft.VisualStudio.DesignTools.Extensibility.Metadata;
using Microsoft.VisualStudio.DesignTools.Extensibility.Features;
using Microsoft.VisualStudio.DesignTools.Extensibility.Model;

[assembly: ProvideMetadata(typeof(AttributeTableProvider))]

public class AttributeTableProvider : IProvideAttributeTable
{
  public AttributeTable AttributeTable
  {
    get
    {
      AttributeTableBuilder builder = new AttributeTableBuilder();
      builder.AddCustomAttributes("MyLibrary.MyControl", new DescriptionAttribute(Strings.MyControlDescription);
      builder.AddCustomAttributes("MyLibrary.MyControl", new FeatureAttribute(typeof(MyControlDefaultInitializer));
      return builder.CreateTable();
    }
  }
}
```

```vb
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Metadata
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Features
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Model

<Assembly: ProvideMetadata(GetType(AttributeTableProvider))>

Public Class AttributeTableProvider
    Implements IProvideAttributeTable

    Public ReadOnly Property AttributeTable As AttributeTable Implements IProvideAttributeTable.AttributeTable
        Get
            Dim builder As New AttributeTableBuilder
            builder.AddCustomAttributes("MyLibrary.MyControl", New DescriptionAttribute(Strings.MyControlDescription))
            builder.AddCustomAttributes("MyLibrary.MyControl", New FeatureAttribute(GetType(MyControlDefaultInitializer)))
            Return builder.CreateTable()
        End Get
    End Property
End Class
```

## <a name="feature-providers-and-model-api"></a>Fournisseurs de fonctionnalités et API de modèle

Fournisseurs de fonctionnalités sont implémentées dans des assemblys d’extension et chargées dans le processus de Visual Studio. `FeatureAttribute` continueront de référencer des types de fournisseur de fonctionnalité directement à l’aide [typeof](/dotnet/csharp/language-reference/keywords/typeof).

Étant donné que les fournisseurs de fonctionnalités sont désormais chargés dans un processus différent dans les bibliothèques de code et le contrôle réel à l’exécution, ils ne sont plus en mesure d’accéder directement aux objets d’exécution. Au lieu de cela, toutes les interactions de ce type doivent être converties pour utiliser les API basée sur le modèle correspondants. L’API du modèle a été mis à jour et l’accès aux <xref:System.Type> ou <xref:System.Object> est soit n’est plus disponible ou a été remplacé par `TypeIdentifier` et `TypeDefinition`.

`TypeIdentifier` représente une chaîne sans un nom d’assembly qui identifie un type. Un `TypeIdenfifier` peut être résolue en un `TypeDefinition` pour demander des informations supplémentaires sur le type. `TypeDefinition` instances ne peut pas être mis en cache dans le code d’extension.

```csharp
TypeDefinition type = ModelFactory.ResolveType(
    item.Context, new TypeIdentifier("MyLibrary.MyControl"));
TypeDefinition buttonType = ModelFactory.ResolveType(
    item.Context, new TypeIdentifier("System.Windows.Controls.Button"));
if (type != null && buttonType != type.IsSubclassOf(buttonType))
{
}
```

```vb
Dim type As TypeDefinition = ModelFactory.ResolveType(
    item.Context, New TypeIdentifier("MyLibrary.MyControl"))
Dim buttonType As TypeDefinition = ModelFactory.ResolveType(
    item.Context, New TypeIdentifier("System.Windows.Controls.Button"))
If type?.IsSubclassOf(buttonType) Then

End If
```

API supprimée du jeu d’API d’extensibilité de surface d’isolation :

* `ModelFactory.CreateItem(EditingContext context, object item)`
* `ViewItem.PlatformObject`
* `ModelProperty.DefaultValue`

Les API qui utilisent `TypeIdentifier` au lieu de <xref:System.Type>:

* `ModelFactory.CreateItem(EditingContext context, Type itemType, params object[] arguments)`
* `ModelFactory.CreateItem(EditingContext context, Type itemType, CreateOptions options, params object[] arguments)`
* `ModelFactory.CreateStaticMemberItem(EditingContext context, Type type, string memberName)`
* `ViewItem.ItemType`
* `ModelEvent.EventType`
* `ModelEvent.IsEventOfType(Type type)`
* `ModeItem.IsItemOfType(Type type)`
* `ModelParent.CanParent(EditingContext context, ModelItem parent, Type childType)`
* `ModelParent.FindParent(EditingContext context, Type childType, ModelItem startingItem)`
* `ModelParent.FindParent(Type childType, GestureData gestureData)`
* `ModelProperty.IsPropertyOfType(Type type)`
* `ParentAdpater.CanParent(ModelItem parent, Type childType)`
* `ParentAdapter.RedirectParent(ModelItem parent, Type childType)`

Les API qui utilisent `TypeIdentifier` au lieu de <xref:System.Type> et n’est plus prise en charge des arguments de constructeur :

* `ModelFactory.CreateItem(EditingContext context, TypeIdentifier typeIdentifier, params object[] arguments)`
* `ModelFactory.CreateItem(EditingContext context, TypeIdentifier typeIdentifier, CreateOptions options, params object[] arguments)`

Les API qui utilisent `TypeDefinition` au lieu de <xref:System.Type>:

* `ModelFactory.ResolveType(EditingContext context, TypeIdentifier typeIdentifier)`
* `ValueTranslationService.GetProperties(Type itemType)`
* `ValueTranslationService.HasValueTranslation(Type itemType, PropertyIdentifier identifier)`
* `ValueTranslationService.TranslatePropertyValue(Type itemType, ModelItem item, PropertyIdentifier identifier, object value)`
* `ModelService.Find(ModelItem startingItem, Type type)`
* `ModelService.Find(ModelItem startingItem, Predicate<Type> match)`
* `ModelItem.ItemType`
* `ModelProperty.AttachedOwnerType`
* `ModelProperty.PropertyType`
* `FeatureManager.CreateFeatureProviders(Type featureProviderType, Type type)`
* `FeatureManager.CreateFeatureProviders(Type featureProviderType, Type type, Predicate<Type> match)`
* `FeatureManager.InitializeFeatures(Type type)`
* `FeatureManager.GetCustomAttributes(Type type, Type attributeType)`
* `AdapterService.GetAdapter<TAdapterType>(Type itemType)`
* `AdapterService.GetAdapter(Type adapterType, Type itemType)`

Les API qui utilisent `ModelItem` au lieu de <xref:System.Object>:

* `ModelItemCollection.Insert(int index, object value)`
* `ModelItemCollection.Remove(object value)`
* `ModelItemDictionary.Add(object key, object value)`
* `ModelItemDictionary.ContainsKey(object key)`
* `ModelItemDictionary.Remove(object key)`
* `ModelItemDictionary.TryGetValue(object key, out ModelItem value)`

Connus comme des types primitifs `Int32`, `String`, ou `Thickness` peuvent être passés à l’API de modèle en tant qu’instances de .NET Framework et passera à l’objet correspondant dans le processus du runtime cible. Par exemple :

```csharp
using Microsoft.VisualStudio.DesignTools.Extensibility.Features;
using Microsoft.VisualStudio.DesignTools.Extensibility.Model;

public class MyControlDefaultInitializer : DefaultInitializer
{
  public override void InitializeDefaults(ModelItem item)
  {
    item.Properties["Width"].SetValue(800d);
    base.InitializeDefaults(item);
  }
}
```

```vb
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Features
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Model

Public Class MyControlDefaultInitializer
    Inherits DefaultInitializer

    Public Overrides Sub InitializeDefaults(item As ModelItem)
        item.Properties!Width.SetValue(800.0)
        MyBase.InitializeDefaults(item)
    End Sub
End Class
```

## <a name="limited-support-for-designdll-extensions"></a>Prise en charge pour limitée. les extensions design.dll

Le cas échéant *. designtools.dll* extension est découvert pour une bibliothèque de contrôles, il est chargé des première et la découverte *. design.dll* extensions est ignorée.

Si aucun *. designtools.dll* extensions sont présentes, mais aucun *. design.dll* extension est trouvée, le Service de langage XAML tente de charger cet assembly pour extraire les informations de table d’attribut pour prendre en charge éditeur de base et les scénarios d’inspecteur de propriété. Ce mécanisme est limité dans la portée. Il n’autorise pas le chargement des extensions de concepteur d’isolation pour exécuter des fournisseurs de fonctionnalités, mais peut fournir le support de base pour les bibliothèques de contrôles WPF existants.
