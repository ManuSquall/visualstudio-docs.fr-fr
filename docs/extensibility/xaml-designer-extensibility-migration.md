---
title: Migration de l’extensibilité de Concepteur XAML
ms.date: 07/09/2019
ms.topic: conceptual
author: lutzroeder
ms.author: lutzr
manager: jillfra
dev_langs:
- csharp
- vb
monikerRange: vs-2019
ms.openlocfilehash: 6ffa8888529586e23d6f9762c3ec5b724c708ca5
ms.sourcegitcommit: ab2c49ce72ccf44b27b5c8852466d15a910453a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69024556"
---
# <a name="xaml-designer-extensibility-migration"></a>Migration de l’extensibilité du concepteur XAML

Dans Visual Studio 2019, le concepteur XAML prend en charge deux architectures différentes: l’architecture d’isolation du concepteur et l’architecture d’isolation de surface la plus récente. Cette transition d’architecture est requise pour prendre en charge des runtimes cibles qui ne peuvent pas être hébergés dans un processus de .NET Framework. Le passage à l’architecture d’isolation de surface introduit des modifications avec rupture dans le modèle d’extensibilité tiers. Cet article décrit ces modifications, qui sont disponibles dans Visual Studio 2019 à partir de la version 16,3.

L' **isolation du concepteur** est utilisée par le Concepteur WPF pour les projets qui ciblent le .NET Framework et prend en charge les extensions *. Design. dll* . Le code utilisateur, les bibliothèques de contrôles et les extensions tierces sont chargés dans un processus externe (*XDesProc. exe*), ainsi que le code du concepteur et les panneaux du concepteur réels.

L' **isolation de surface** est utilisée par le concepteur UWP. Il est également utilisé par le Concepteur WPF pour les projets qui ciblent .NET Core. Dans l’isolation d’aire, seules les bibliothèques de code utilisateur et de contrôle sont chargées dans un processus distinct, tandis que le concepteur et ses panneaux sont chargés dans le processus Visual Studio (*devenv. exe*). Le runtime utilisé pour l’exécution du code utilisateur et des bibliothèques de contrôles est différent de celui utilisé par le .NET Framework pour le concepteur réel et le code d’extensibilité tiers.

![extensibility-migration-architecture](media/xaml-designer-extensibility-migration-architecture.png)

En raison de cette transition d’architecture, les extensions tierces ne sont plus chargées dans le même processus que les bibliothèques de contrôles tiers. Les extensions ne peuvent plus avoir de dépendances directes sur les bibliothèques de contrôles ou accéder directement aux objets Runtime. Les extensions écrites précédemment pour l’architecture d’isolation du concepteur à l’aide de l’API *Microsoft. Windows. Extensibility. dll* doivent être migrées vers une nouvelle approche pour fonctionner avec l’architecture d’isolation de surface. Dans la pratique, une extension existante doit être compilée avec les nouveaux assemblys d’API d’extensibilité. L’accès aux types de contrôle d’exécution via les instances [typeof](/dotnet/csharp/language-reference/keywords/typeof) ou Runtime doit être remplacé ou supprimé, car les bibliothèques de contrôles sont maintenant chargées dans un processus différent.

## <a name="new-extensibility-api-assemblies"></a>Nouveaux assemblys d’API d’extensibilité

Les nouveaux assemblys d’API d’extensibilité sont similaires aux assemblys d’API d’extensibilité existants, mais suivent un schéma d’affectation de noms différent afin de les différencier. De même, les noms d’espaces de noms ont été modifiés pour refléter les nouveaux noms d’assemblys.

| Assembly d’API d’isolation du concepteur            | Assembly d’API d’isolation de surface                       |
|:------------------------------------------ |:---------------------------------------------------- |
| Microsoft.Windows.Design.Extensibility.dll | Microsoft.VisualStudio.DesignTools.Extensibility.dll |
| Microsoft.Windows.Design.Interaction.dll   | Microsoft.VisualStudio.DesignTools.Interaction.dll   |

## <a name="new-file-extension-and-discovery"></a>Nouvelle extension de fichier et découverte

Au lieu d’utiliser l’extension de fichier *. Design. dll* , les nouvelles extensions de surface sont découvertes à l’aide de l’extension de fichier *. Designtools. dll* . les extensions *. Design. dll* et *. Designtools. dll* peuvent exister dans le même sous-dossier de *conception* .

Alors que les bibliothèques de contrôles tiers sont compilées pour le runtime cible réel (.NET Core ou UWP), l’extension *. Designtools. dll* doit toujours être compilée en tant qu’assembly .NET Framework.

## <a name="decouple-attribute-tables-from-runtime-types"></a>Dissocier les tables d’attributs des types au moment de l’exécution

Le modèle d’extensibilité de l’isolation de l’aire ne permet pas aux extensions de dépendre de bibliothèques de contrôles réelles. par conséquent, les extensions ne peuvent pas référencer des types de la bibliothèque de contrôles. Par exemple, *MyLibrary. Designtools. dll* ne doit pas avoir de dépendance sur *MyLibrary. dll*.

Ces dépendances étaient les plus courantes lors de l’inscription de métadonnées pour les types via des tables d’attributs. Le code d’extension qui référence directement les types de bibliothèque de contrôle via [typeof](/dotnet/csharp/language-reference/keywords/typeof) ou [GetType](/dotnet/visual-basic/language-reference/operators/gettype-operator) est substitué dans les nouvelles API en utilisant des noms de types basés sur une chaîne:

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
      var builder = new AttributeTableBuilder();
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

Les fournisseurs de fonctionnalités sont implémentés dans les assemblys d’extension et chargés dans le processus Visual Studio. `FeatureAttribute`continuera à référencer directement les types de fournisseur de fonctionnalités à l’aide de [typeof](/dotnet/csharp/language-reference/keywords/typeof).

Actuellement, les fournisseurs de fonctionnalités suivants sont pris en charge:

* `DefaultInitializer`
* `AdornerProvider`
* `ContextMenuProvider`
* `ParentAdapter`
* `PlacementAdapter`

Étant donné que les fournisseurs de fonctionnalités sont désormais chargés dans un processus différent du code d’exécution réel et des bibliothèques de contrôles, ils ne sont plus en mesure d’accéder directement aux objets de Runtime. Au lieu de cela, toutes ces interactions doivent être converties pour utiliser les API basées sur un modèle correspondantes. L’API de modèle a été mise à jour et <xref:System.Type> l' <xref:System.Object> accès à ou n’est plus disponible ou a été `TypeIdentifier` remplacé `TypeDefinition`par et.

`TypeIdentifier`représente une chaîne sans nom d’assembly identifiant un type. Une `TypeIdenfifier` peut être résolue `TypeDefinition` en pour demander des informations supplémentaires sur le type. `TypeDefinition`les instances ne peuvent pas être mises en cache dans le code d’extension.

```csharp
TypeDefinition type = ModelFactory.ResolveType(
    item.Context, new TypeIdentifier("MyLibrary.MyControl"));
TypeDefinition buttonType = ModelFactory.ResolveType(
    item.Context, new TypeIdentifier("System.Windows.Controls.Button"));
if (type?.IsSubclassOf(buttonType) == true)
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

API supprimées de l’ensemble d’API d’extensibilité de l’isolation de l’aire:

* `ModelFactory.CreateItem(EditingContext context, object item)`
* `ViewItem.PlatformObject`
* `ModelProperty.DefaultValue`

API qui utilisent `TypeIdentifier` à la <xref:System.Type>place de:

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

Les API qui `TypeIdentifier` utilisent à <xref:System.Type> la place de et ne prennent plus en charge les arguments de constructeur:

* `ModelFactory.CreateItem(EditingContext context, TypeIdentifier typeIdentifier, params object[] arguments)`
* `ModelFactory.CreateItem(EditingContext context, TypeIdentifier typeIdentifier, CreateOptions options, params object[] arguments)`

API qui utilisent `TypeDefinition` à la <xref:System.Type>place de:

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

API qui utilisent `ModelItem` à la <xref:System.Object>place de:

* `ModelItemCollection.Insert(int index, object value)`
* `ModelItemCollection.Remove(object value)`
* `ModelItemDictionary.Add(object key, object value)`
* `ModelItemDictionary.ContainsKey(object key)`
* `ModelItemDictionary.Remove(object key)`
* `ModelItemDictionary.TryGetValue(object key, out ModelItem value)`

En outre `ModelItem` , les `SetValue` API telles que ne prennent en charge que les instances de types primitifs ou les types de .NET Framework intégrés qui peuvent être convertis pour le runtime cible. Actuellement, ces types sont pris en charge:

* Types de `Boolean`.NET Framework primitifs: `Char`, `DateTime` `Byte`, `Double`, `Enum`,, ,`Int16` ,,`Int32` ,`SByte` ,, `Guid` `Int64` `Nullable` , `Single`, `String`, `Type`, `UInt16`, `UInt32`, `UInt64`,`Uri`
* Types de .NET Framework WPF connus (et types dérivés `Brush`) `Color`: `CompositeTransform`, `CornerRadius`, `Duration`, `EasingFunctionBase`, `EasingMode`, `EllipseGeometry`, `FontFamily`, `GeneralTransform`, `Geometry` ,, , `GradientStopCollection`, `GradientStop`, `GridLength`, `ImageSource`, `InlineCollection`, `Inline`, `KeySpline`, `Material`, `Matrix`, `PathFigureCollection`, `PathFigure`, `PathSegmentCollection`, `PathSegment`, `Path`, `PointCollection`, `Point`, `PropertyPath`, `Rect`, `RepeatBehavior`, `Setter`, `Size`, `StaticResource`, `TextAlignment`, `TextDecorationCollection`, `ThemeResourceExtension`, `Thickness`, `TimeSpan`, `Transform3D`,`TransformCollection`

Par exemple :

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

D’autres exemples de code sont disponibles dans le référentiel [XAML-Designer-Extensibility-Samples](https://github.com/microsoft/xaml-designer-extensibility-samples) .

## <a name="limited-support-for-designdll-extensions"></a>Prise en charge limitée des extensions. Design. dll

Si une extension *. Designtools. dll* est détectée pour une bibliothèque de contrôles, elle est chargée en premier et la découverte des extensions *. Design. dll* est ignorée.

Si aucune extension *. Designtools. dll* n’est présente mais qu’une extension *. Design. dll* est trouvée, le service de langage XAML tente de charger cet assembly pour extraire les informations de la table d’attributs afin de prendre en charge les scénarios de l’éditeur de base et de l’inspecteur de propriété. Ce mécanisme est limité dans l’étendue. Il n’autorise pas le chargement des extensions d’isolation du concepteur pour exécuter des fournisseurs de fonctionnalités, mais il peut fournir une prise en charge de base pour les bibliothèques de contrôles WPF existantes.
