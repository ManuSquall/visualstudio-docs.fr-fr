---
title: Intégration de modèles à l’aide de ModelBus
description: Découvrez que Visual Studio ModelBus fournit une méthode pour créer des liens entre des modèles et d’autres outils dans des modèles.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 350398d91d73a722956d195b300311f313ff34db
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112391060"
---
# <a name="integrate-models-by-using-visual-studio-modelbus"></a>Intégrer des modèles à l’aide de Visual Studio Modelbus

Visual Studio ModelBus fournit une méthode pour créer des liens entre des modèles et d’autres outils dans des modèles. Par exemple, vous pouvez lier des modèles DSL et des modèles UML. Vous pouvez créer un ensemble intégré de DSL.

ModelBus vous permet de créer une référence unique à un modèle ou à un élément spécifique à l'intérieur d'un modèle. Cette référence peut être stockée en dehors du modèle : dans un élément d'un autre modèle, par exemple. Quand, en une occasion ultérieure, un outil veut obtenir un accès à l'élément, l'infrastructure de bus de modèles charge le modèle approprié et retourne l'élément. Si vous le désirez, vous pouvez afficher le modèle pour l'utilisateur. S'il n'est pas possible d'accéder au fichier dans son emplacement précédent, ModelBus demande à l'utilisateur de le rechercher. Si l'utilisateur trouve le fichier, ModelBus corrige toutes les références au fichier.

> [!NOTE]
> Dans l’implémentation actuelle de Visual Studio de ModelBus, les modèles liés doivent être des éléments dans la même solution Visual Studio.

Pour obtenir plus d'informations et des exemples de code, voir :

- [Guide pratique pour ajouter un gestionnaire de glisser-déplacer](../modeling/how-to-add-a-drag-and-drop-handler.md)

- [SDK Modeling pour Visual Studio](https://www.microsoft.com/download/details.aspx?id=48148)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="providing-access-to-a-dsl"></a><a name="provide"></a> Fournir l’accès à un DSL
 Avant de créer les références ModelBus à un modèle ou à ses éléments, vous devez définir un ModelBusAdapter pour le DSL. Le moyen le plus simple consiste à utiliser l’extension Visual Studio Model bus, qui ajoute des commandes au Concepteur DSL.

### <a name="to-expose-a-dsl-definition-to-model-bus"></a><a name="expose"></a> Pour exposer une définition DSL à Model bus

1. Ouvrez le fichier de définition DSL. Cliquez avec le bouton droit sur l’aire de conception, puis cliquez sur **activer ModelBus**.

2. Dans la boîte de dialogue, choisissez **je souhaite exposer ce DSL au ModelBus**. Vous pouvez choisir les deux options si vous voulez que ce DSL expose ses modèles et consomme les références aux autres DSL.

3. Cliquez sur **OK**. Un nouveau projet « ModelBusAdapter » vient s'ajouter à la solution DSL.

4. Si vous voulez accéder au DSL à partir d'un modèle de texte, vous devez modifier AdapterManager.tt dans le nouveau projet. Ignorez cette étape si vous voulez accéder au DSL à partir d'un autre code, tel que celui des commandes ou gestionnaires d'événements. Pour plus d’informations, consultez [utilisation de Visual Studio Modelbus dans un modèle de texte](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

   1. Remplacez la classe de base de AdapterManagerBase par [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)).

   2. Vers la fin du fichier, insérez cet attribut additionnel devant la classe AdapterManager :

       `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

   3. Dans les références du projet ModelBusAdapter, ajoutez **Microsoft. VisualStudio. TextTemplating. Modeling. 11.0**.

      Pour accéder au DSL à partir de modèles de texte et d'un autre code, vous avez besoin de deux adaptateurs, l'un modifié et l'autre non modifié.

5. Cliquez sur **transformer tous les modèles**.

6. Régénérez la solution.

   Il est désormais possible pour ModelBus d'ouvrir des instances de ce DSL.

   Le dossier `ModelBusAdapters\bin\*` contient les assemblys générés par les projets `Dsl` et `ModelBusAdapters`. Pour faire référence à ce DSL à partir d'un autre DSL, vous devez importer ces assemblys.

### <a name="ensure-that-elements-can-be-referenced"></a>S’assurer que les éléments peuvent être référencés

Les adaptateurs Visual Studio ModelBus utilisent le GUID d’un élément pour l’identifier, par défaut. Par conséquent, ces identificateurs doivent être conservés dans le fichier de modèle.

Pour garantir la persistance des ID d’élément :

1. Ouvrez DslDefinition.dsl.

2. Dans l’Explorateur DSL, développez **comportement de sérialisation XML**, puis **données de classe**.

3. Pour chaque classe pour laquelle vous voulez créer des références de bus de modèles :

    Cliquez sur le nœud de la classe, et dans le Fenêtre Propriétés, assurez-vous que l' **ID de sérialisation** est défini sur `true` .

   Sinon, si vous souhaitez utiliser des noms d’élément pour identifier des éléments au lieu de GUID, vous pouvez remplacer des parties des adaptateurs générés. Remplacez les méthodes suivantes dans la classe d'adaptateur :

- Remplacez `GetElementId` pour retourner l'identificateur que vous voulez utiliser. Cette méthode est appelée lors de la création de références.

- Remplacez `ResolveElementReference` pour rechercher l'élément approprié à partir d'une référence de bus de modèles.

## <a name="accessing-a-dsl-from-another-dsl"></a><a name="editRef"></a> Accès à un DSL à partir d’un autre DSL

Vous pouvez stocker les références de bus de modèles dans une propriété de domaine d'un DSL et vous pouvez écrire le code personnalisé qui les utilise. Vous pouvez aussi laisser l'utilisateur créer une référence de bus de modèles en sélectionnant un fichier de modèle, ainsi qu'un élément à l'intérieur du modèle.

Pour permettre à un DSL d’utiliser des références à un autre DSL, vous devez d’abord en faire un *consommateur* de références de bus de modèles.

### <a name="to-enable-a-dsl-to-consume-references-to-an-exposed-dsl"></a>Pour permettre à un DSL de consommer les références à un DSL exposé

1. Dans le diagramme de définition DSL, cliquez avec le bouton droit sur la partie principale du diagramme, puis cliquez sur **activer ModelBus**.

2. Dans la boîte de dialogue, sélectionnez **je souhaite activer ce modèle pour utiliser les références de bus de modèles**.

3. Dans le projet DSL du DSL consommateur, ajoutez les assemblys suivants aux références du projet. Ces assemblys (.dll fichiers) se trouvent dans le répertoire ModelBusAdapter\bin \\ * du DSL exposé.

    - Assembly DSL exposé, par exemple **Fabrikam.FamilyTree.Dsl.dll**

    - Assembly de l’adaptateur de bus de modèles exposé, par exemple **Fabrikam.FamilyTree.ModelBusAdapter.dll**

4. Ajoutez les assemblys .NET suivants aux références de projet du projet DSL consommateur.

    1. **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**

    2. **Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0.dll**

### <a name="to-store-a-model-bus-reference-in-a-domain-property"></a>Pour stocker une référence de bus de modèles dans une propriété de domaine

1. Dans la définition DSL du DSL consommateur, ajoutez une propriété de domaine à une classe de domaine et définissez son nom.

2. Dans le Fenêtre Propriétés, avec la propriété de domaine sélectionnée, définissez **type** sur `ModelBusReference` .

   À ce stade, le code de programme peut définir la valeur de la propriété, mais elle est en lecture seule dans la fenêtre Propriétés.

   Vous pouvez permettre aux utilisateurs de définir la propriété avec un éditeur de références ModelBus spécialisé. Il existe deux versions de cet éditeur ou *Sélecteur :* l’une permet aux utilisateurs de choisir un fichier de modèle et l’autre permet aux utilisateurs de choisir un fichier de modèle et un élément dans le modèle.

### <a name="to-allow-the-user-to-set-a-model-bus-reference-in-a-domain-property"></a>Pour permettre à l'utilisateur de définir une référence de bus de modèles dans une propriété de domaine

1. Cliquez avec le bouton droit sur la propriété de domaine, puis cliquez sur **modifier les propriétés spécifiques d’ModelBusReference**. Une boîte de dialogue s'ouvre. Il s’agit du *Sélecteur de bus de modèle*.

2. Sélectionnez le **type approprié de ModelBusReference**: à un modèle ou à un élément à l’intérieur d’un modèle.

3. Dans la chaîne de filtre de la boîte de dialogue Fichier, entrez une chaîne telle que `Family Tree files |*.ftree`. Remplacez l’extension de fichier de votre DSL exposé.

4. Si vous choisissez de référencer un élément dans un modèle, vous pouvez ajouter une liste de types que l'utilisateur peut sélectionner, par exemple Company.FamilyTree.Person.

5. Cliquez sur **OK**, puis sur **transformer tous les modèles** dans la barre d’outils **Explorateur de solutions** .

    > [!WARNING]
    > Si vous n'avez pas sélectionné un modèle ou une entité valide, le bouton OK sera sans effet, même s'il peut paraître activé.

6. Si vous avez spécifié une liste de types cibles tels que Company.FamilyTree.Person, vous devez ajouter une référence d'assembly à votre projet DSL, en faisant référence à la DLL du DSL cible : Company.FamilyTree.Dsl.dll, par exemple.

### <a name="to-test-a-model-bus-reference"></a>Pour tester une référence de bus de modèles

1. Générez à la fois le DSL exposé et le DSL consommateur.

2. Exécutez l'un des DSL en mode expérimental en appuyant sur F5 ou CTRL+F5.

3. Dans le projet de débogage de l’instance expérimentale de Visual Studio, ajoutez des fichiers qui sont des instances de chaque DSL.

    > [!NOTE]
    > Visual Studio ModelBus pouvez uniquement résoudre les références aux modèles qui sont des éléments dans la même solution Visual Studio. Par exemple, vous ne pouvez pas créer de référence à un fichier de modèle dans une autre partie de votre système de fichiers.

4. Créez quelques éléments et liens dans l'instance du DSL exposé, puis enregistrez-les.

5. Ouvrez une instance du DSL consommateur et sélectionnez un élément de modèle qui possède une propriété de référence de bus de modèles.

6. Dans la fenêtre Propriétés, double-cliquez sur la propriété de référence de bus de modèles. La boîte de dialogue du sélecteur s'ouvre.

7. Cliquez sur **Parcourir** et sélectionnez l’instance du DSL exposé.

     Le sélecteur vous permettra aussi de choisir un élément du modèle, si vous avez spécifié le type propre à l'élément de la référence de bus de modèles.

## <a name="creating-references-in-program-code"></a>Création de références dans le code de programme

Lorsque vous voulez stocker une référence à un modèle ou à un élément à l'intérieur d'un modèle, vous créez une `ModelBusReference`. Il existe deux sortes de `ModelBusReference` : les références de modèle et les références d'élément.

Pour créer une référence de modèle, vous avez besoin de la AdapterManager du DSL dont le modèle est une instance, et du nom de fichier ou de l’élément de projet Visual Studio du modèle.

Pour créer une référence d'élément, vous avez besoin d'un adaptateur pour le fichier de modèle et de l'élément auquel vous voulez faire référence.

> [!NOTE]
> Avec l’Visual Studio ModelBus, vous pouvez créer des références uniquement aux éléments de la même solution Visual Studio.

### <a name="import-the-exposed-dsl-assemblies"></a>Importer les assemblys DSL exposés

Dans le projet consommateur, ajoutez les références de projet aux assemblys DSL et ModelBusAdapter du DSL exposé.

Par exemple, imaginez que vous vouliez stocker les références ModelBus dans les éléments d'un DSL MusicLibrary. Les références ModelBus feront référence aux éléments du DSL FamilyTree. Dans le projet `Dsl` de la solution MusicLibrary, dans le nœud Références, ajoutez les références aux assemblys suivants :

- Fabrikam.FamilyTree.Dsl.dll - le DSL exposé.

- Fabrikam.FamilyTree.ModelBusAdapters.dll - l'adaptateur ModelBus du DSL exposé.

- Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0

- Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0

  Ces assemblys sont disponibles dans le projet `ModelBusAdapters` du DSL exposé, sous `bin\*`.

  Dans le fichier de code où vous allez créer les références, vous devez généralement importer ces espaces de noms :

```csharp
// The namespace of the DSL you want to reference:
using Fabrikam.FamilyTree;  // Exposed DSL
using Fabrikam.FamilyTree.ModelBusAdapters;
using Microsoft.VisualStudio.Modeling.Integration;
using System.Linq;
...
```

### <a name="to-create-a-reference-to-a-model"></a>Pour créer une référence à un modèle

Pour créer une référence de modèle, vous accédez à l'AdapterManager du DSL exposé et l'utilisez pour créer une référence au modèle. Vous pouvez spécifier un chemin d'accès du fichier ou un `EnvDTE.ProjectItem`.

À partir de la classe AdapterManager, vous pouvez obtenir un adaptateur, qui fournit l'accès aux éléments individuels du modèle.

> [!NOTE]
> Lorsque vous avez fini d'utiliser l'adaptateur, vous devez le supprimer. La solution la plus pratique pour y parvenir consiste à utiliser une instruction `using`. L'exemple suivant illustre ce comportement.

```csharp
// The file path of a model instance of the FamilyTree DSL:
string targetModelFile = "TudorFamilyTree.ftree";
// Get the ModelBus service:
IModelBus modelBus =
    this.Store.GetService(typeof(SModelBus)) as IModelBus;
// Get an adapterManager for the target DSL:
FamilyTreeAdapterManager manager =
    (modelbus.GetAdapterManager(FamilyTreeAdapter.AdapterId)
     as FamilyTreeAdapterManager;
// or: (modelBus.FindAdapterManagers(targetModelFile).First())
// or could provide an EnvDTE.ProjectItem

// Create a reference to the target model:
// NOTE: the target model must be a file in this project.
ModelBusReference modelReference =
     manager.CreateReference(targetModelFile);
// or can use an EnvDTE.ProjectItem instead of the filename

// Get the root element of this model:
using (FamilyTreeAdapter adapter =
     modelBus.CreateAdapter(modelReference) as FamilyTreeAdapter)
{
  FamilyTree modelRoot = adapter.ModelRoot;
  // Access elements under the root in the usual way:
  foreach (Person p in modelRoot.Persons) {...}
  // You can create adapters for individual elements:
  ModelBusReference elementReference =
     adapter.GetElementReference(person);
  ...
} // Dispose adapter
```

Si vous souhaitez pouvoir utiliser la `modelReference` ultérieurement, vous pouvez la stocker dans une propriété de domaine qui possède le type externe `ModelBusReference` :

```csharp
using Transaction t = this.Store.TransactionManager
    .BeginTransaction("keep reference"))
{
  artist.FamilyTreeReference = modelReference;
  t.Commit();
}
```

Pour permettre aux utilisateurs de modifier cette propriété de domaine, utilisez `ModelReferenceEditor` comme paramètre de l'attribut Editor. Pour plus d’informations, consultez [autoriser l’utilisateur à modifier une référence](#editRef).

### <a name="to-create-a-reference-to-an-element"></a>Pour créer une référence à un élément

L'adaptateur que vous avez créé pour le modèle peut être utilisé pour créer et résoudre les références.

```csharp
// person is an element in the FamilyTree model:
ModelBusReference personReference =
  adapter.GetElementReference(person);
```

Si vous souhaitez pouvoir utiliser la `elementReference` ultérieurement, vous pouvez la stocker dans une propriété de domaine qui possède le type externe `ModelBusReference`. Pour permettre aux utilisateurs de la modifier, utilisez `ModelElementReferenceEditor` comme paramètre de l'attribut Editor. Pour plus d’informations, consultez [autoriser l’utilisateur à modifier une référence](#editRef).

### <a name="resolving-references"></a>Résolution des références

Si vous avez une `ModelBusReference` (MBR), vous pouvez obtenir le modèle ou l'élément du modèle auquel elle fait référence. Si l'élément est présenté sur un diagramme ou une autre vue, vous pouvez ouvrir la vue et sélectionner l'élément.

Vous pouvez créer un adaptateur à partir d'une MBR. À partir de l'adaptateur, vous pouvez obtenir la racine du modèle. Vous pouvez aussi résoudre les MBR qui font référence à des éléments spécifiques à l'intérieur du modèle.

```csharp
using Microsoft.VisualStudio.Modeling.Integration; ...
ModelBusReference elementReference = ...;

// Get the ModelBus service:
IModelBus modelBus =
    this.Store.GetService(typeof(SModelBus)) as IModelBus;
// Use a model reference or an element reference
// to obtain an adapter for the target model:
using (FamilyTreeAdapter adapter =
   modelBus.CreateAdapter(elementReference) as FamilyTreeAdapter)
   // or CreateAdapter(modelReference)
{
  // Get the root of the model:
  FamilyTree tree = adapter.ModelRoot;

  // Get a model element:
  MyDomainClass mel =
    adapter.ResolveElementReference<MyDomainClass>(elementReference);
  if (mel != null) {...}

  // Get the diagram or other view, if there is one:
  ModelBusView view = adapter.GetDefaultView();
  if (view != null)
  {
   view.Open();
   // Display the diagram:
   view.Show();
   // Attempt to select the shape that presents the element:
   view.SetSelection(elementReference);
  }
} // Dispose the adapter.
```

#### <a name="to-resolve-modelbus-references-in-a-text-template"></a>Pour résoudre les références ModelBus dans un modèle de texte

1. Le DSL auquel vous voulez accéder doit avoir un adaptateur ModelBus configuré pour être accessible par les modèles de texte. Pour plus d’informations, consultez [fourniture d’un accès à une solution DSL](#provide).

2. Généralement, vous accèderez à un DSL cible à l'aide d'une référence de bus de modèles (MBR) stockée dans un DSL source. Par conséquent, votre modèle inclut la directive du DSL source, plus le code pour résoudre la MBR. Pour plus d’informations sur les modèles de texte, consultez [génération de code à partir d’un langage de Domain-Specific](../modeling/generating-code-from-a-domain-specific-language.md).

   ```
   <#@ template debug="true" hostspecific="true"
   inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>
   <#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>
   <#@ output extension=".txt" #>
   <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>
   <#@ assembly name = "System.Core" #>
   <#@ assembly name = "Company.CompartmentDragDrop.Dsl.dll" #>
   <#@ assembly name = "Company.CompartmentDragDrop.ModelBusAdapter.dll" #>
   <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>
   <#@ import namespace="System.Linq" #>
   <#@ import namespace="Company.CompartmentDragDrop" #>
   <#@ import namespace="Company.CompartmentDragDrop.ModelBusAdapters" #>
   <# // Get source root from directive processor:
     ExampleModel source = this.ExampleModel;
     // This DSL has a MBR in its root:
   using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as ModelBusAdapter)
     {
     ModelBusAdapterManager manager = this.ModelBus.FindAdapterManagers(this.Host.ResolvePath("Sample.compDD1")).FirstOrDefault();
     ModelBusReference modelReference =
       manager.CreateReference(this.Host.ResolvePath("Sample.compDD1"));

     // Get the root element of this model:
     using (CompartmentDragDropAdapter adapter =
        this.ModelBus.CreateAdapter(modelReference) as CompartmentDragDropAdapter)
     {
       ModelRoot root = adapter.ModelRoot;
   #>
   [[<#= root.Name #>]]
   <#
     }
   #>
   ```

   Pour plus d’informations et pour obtenir une procédure pas à pas, consultez [utilisation de Visual Studio Modelbus dans un modèle de texte](../modeling/using-visual-studio-modelbus-in-a-text-template.md)

## <a name="serializing-a-modelbusreference"></a>Sérialisation d'une ModelBusReference

Si vous voulez stocker une `ModelBusReference` (MBR) sous la forme d'une chaîne, vous pouvez la sérialiser :

```csharp
string serialized = modelBus.SerializeReference(elementReference);
// Store it anywhere, then get it back again:
ModelBusReference elementReferenceRestored =
    modelBus.DeserializeReference(serialized, null);
```

Une MBR ainsi sérialisée est indépendante du contexte. Si vous utilisez l'adaptateur de bus de modèles basé sur un fichier simple, la MBR contient un chemin d'accès au fichier absolu. Cela suffit si les fichiers du modèle d'instance ne sont jamais déplacés. Toutefois, les fichiers de modèle sont généralement des éléments dans un projet Visual Studio. Vos utilisateurs attendront de pouvoir déplacer la totalité du projet vers différentes parties du système de fichiers. Ils s'attendront aussi à pouvoir maintenir le projet sous contrôle du code source et à l'ouvrir sur différents ordinateurs. Les noms des chemins d'accès doivent par conséquent être sérialisés par rapport à l'emplacement du projet qui contient les fichiers.

### <a name="serializing-relative-to-a-specified-file-path"></a>Sérialisation par rapport à un chemin de fichier spécifié

Une `ModelBusReference` contient un `ReferenceContext`, lequel est un dictionnaire où vous pouvez stocker des informations telles que le chemin d'accès par rapport auquel la sérialisation doit être effectuée.

Pour sérialiser par rapport à un chemin d'accès :

```csharp
elementReference.ReferenceContext.Add(
   ModelBusReferencePropertySerializer.FilePathSaveContextKey,
   currentProjectFilePath);
string serialized = modelBus.SerializeReference(elementReference);
```

Pour extraire la référence de la chaîne :

```csharp
ReferenceContext context = new ReferenceContext();
context.Add(ModelBusReferencePropertySerializer.FilePathLoadContextKey,
    currentProjectFilePath);
ModelBusReference elementReferenceRestored =
    modelBus.DeserializeReference(serialized, context);
```

### <a name="modelbusreferences-created-by-other-adapters"></a>ModelBusReference créées par d'autres adaptateurs
 Les informations suivantes sont utiles si vous désirez créer votre propre adaptateur.

 Une `ModelBusReference` (MBR) se compose de deux parties : l'en-tête MBR, désérialisé par le bus de modèles, et une partie propre à l'adaptateur et gérée par le gestionnaire de l'adaptateur spécifique. Vous pouvez ainsi fournir votre propre format de sérialisation de l'adaptateur. Par exemple, vous pouvez référencer une base de données plutôt qu'un fichier ou stocker des informations supplémentaires dans la référence de l'adaptateur. Votre propre adaptateur peut placer des informations supplémentaires dans le `ReferenceContext`.

 Lorsque vous désérialisez une MBR, vous devez fournir un ReferenceContext, qui est alors stocké dans l'objet MBR. Lorsque vous sérialisez une MBR, le ReferenceContext stocké est utilisé par l'adaptateur pour aider à générer la chaîne. La chaîne désérialisée ne contient pas toutes les informations du ReferenceContext. Par exemple, dans l'adaptateur basé sur un fichier simple, le ReferenceContext contient un chemin de fichier racine, qui n'est pas stocké dans la chaîne MBR sérialisée.

 La désérialisation de la MBR s'effectue en deux étapes :

- `ModelBusReferencePropertySerializer` est le sérialiseur standard qui gère l’en-tête MBR. Il utilise le conteneur de propriétés `SerializationContext` DSL standard, stocké dans le `ReferenceContext` à l'aide de la clé `ModelBusReferencePropertySerializer.ModelBusLoadContextKey`. En particulier, le `SerializationContext` doit contenir une instance du `ModelBus`.

- Votre adaptateur ModelBus gère la partie spécifique à l'adaptateur de la MBR. Il peut utiliser les informations supplémentaires stockées dans le ReferenceContext de la MBR. L’adaptateur simple basé sur des fichiers conserve les chemins d’accès aux fichiers racine à l’aide des clés `FilePathLoadContextKey` et `FilePathSaveContextKey` .

     Une référence d'adaptateur d'un fichier de modèle n'est désérialisée que lorsqu'elle est utilisée.

## <a name="to-create-a-model"></a>Pour créer un modèle

### <a name="creating-opening-and-editing-a-model"></a>Création, ouverture et modification d'un modèle
 Le fragment suivant est extrait de l’exemple d’ordinateur d’État sur le site Web VMSDK. Il illustre l'utilisation des ModelBusReference pour créer et ouvrir un modèle, et pour obtenir le diagramme associé au modèle.

 Dans cet exemple, le nom du DSL cible est StateMachine. Plusieurs noms en sont dérivés, tels que le nom de la classe de modèle et le nom du ModelBusAdapter.

```csharp
using Fabrikam.StateMachine.ModelBusAdapters;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Integration;
using Microsoft.VisualStudio.Modeling.Integration.Shell;
using Microsoft.VisualStudio.Modeling.Shell;
...
// Create a new model.
ModelBusReference modelReference =
   StateMachineAdapterManager    .CreateStateMachineModel(modelName, fileName);
//Keep reference of new model in this model.
using (Transaction t = ...)
{
  myModelElement.ReferenceProperty = modelReference;
  t.Commit();
}
// Get the ModelBus service from Visual Studio.
IModelBus modelBus = Microsoft.VisualStudio.Shell.Package.
    GetGlobalService(typeof(SModelBus)) as IModelBus;
// Get a modelbus adapter on the new model.
ModelBusAdapter modelBusAdapter;
modelBus.TryCreateAdapter(modelReference,
    this.ServiceProvider, out modelBusAdapter);
using (StateMachineAdapter adapter =
      modelBusAdapter as StateMachineAdapter)
{
    if (adapter != null)
    {
        // Obtain a Diagram from the adapter.
        Diagram targetDiagram =
           ((StandardVsModelingDiagramView)
                 adapter.GetDefaultView()
            ).Diagram;

        using (Transaction t =
             targetDiagram.Store.TransactionManager
                .BeginTransaction("Update diagram"))
        {
            DoUpdates(targetDiagram);
            t.Commit();
        }

        // Display the new diagram.
        adapter.GetDefaultView().Show();
    }
}
```

## <a name="validating-references"></a>Validation des références
 Le BrokenReferenceDetector teste toutes les propriétés de domaine d'un magasin qui peut contenir les ModelBusReference. Il appelle l'action que vous fournissez quand une action est trouvée. Ceci est particulièrement utile pour les méthodes de validation. La méthode de validation suivante teste le magasin lors de la tentative d'enregistrement du modèle et signale les références rompues dans la fenêtre des erreurs :

```csharp
[ValidationMethod(ValidationCategories.Save)]
public void ValidateModelBusReferences(ValidationContext context)
{
  BrokenReferenceDetector.DetectBrokenReferences(this.Store,
    delegate(ModelElement element, // parent of property
             DomainPropertyInfo property, // identifies property
             ModelBusReference reference) // invalid reference
    {
      context.LogError(string.Format(INVALID_REF_FORMAT,
             property.Name,
             referenceState.Name,
             new ModelBusReferenceTypeConverter().
                 ConvertToInvariantString(reference)),
         "Reference",
         element);
      });
}}
private const string INVALID_REF_FORMAT =
    "The '{0}' domain property of ths ReferenceState instance "
  + "named '{1}' contains reference value '{2}' which is invalid";
```

## <a name="actions-performed-by-the-modelbus-extension"></a>Actions exécutées par l'extension ModelBus

Les informations suivantes ne sont pas essentielles, mais peuvent être utiles si vous utilisez intensivement ModelBus.

L'extension ModelBus apporte les modifications suivantes dans votre solution DSL.

Lorsque vous cliquez avec le bouton droit sur le diagramme de définition DSL, cliquez sur **activer ModelBus**, puis sélectionnez **activer ce DSL pour utiliser le ModelBus**:

- Dans le projet DSL, une référence est ajoutée à **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**

- Dans la définition DSL, une référence de type externe est ajoutée : `Microsoft.VisualStudio.Modeling.Integration.ModelBusReference`.

   Vous pouvez voir la référence dans l' **Explorateur DSL**, sous **types de domaines**. Pour ajouter manuellement des références de type externe, cliquez avec le bouton droit sur le nœud racine.

- Un nouveau fichier de modèle est ajouté, **Dsl\GeneratedCode\ModelBusReferencesSerialization.TT**.

Lorsque vous définissez le type d’une propriété de domaine sur ModelBusReference, puis cliquez avec le bouton droit sur la propriété et cliquez sur **activer les propriétés spécifiques ModelBusReference**:

- Plusieurs attributs CLR sont ajoutés à la propriété de domaine. Vous pouvez les voir dans le champ Attributs personnalisés de la fenêtre Propriétés. Dans **Dsl\GeneratedCode\DomainClasses.cs**, vous pouvez voir les attributs sur la déclaration de propriété :

  ```csharp
  [System.ComponentModel.TypeConverter(typeof(
  Microsoft.VisualStudio.Modeling.Integration.ModelBusReferenceTypeConverter))]
  [System.ComponentModel.Editor(typeof(
    Microsoft.VisualStudio.Modeling.Integration.Picker
    .ModelReferenceEditor // or ModelElementReferenceEditor
    ), typeof(System.Drawing.Design.UITypeEditor))]
  [Microsoft.VisualStudio.Modeling.Integration.Picker
    .SupplyFileBasedBrowserConfiguration
    ("Choose a model file", "Target model|*.target")]
  ```

Lorsque vous cliquez avec le bouton droit sur le diagramme de définition DSL, cliquez sur **activer ModelBus**, puis sélectionnez **exposer ce DSL au ModelBus**:

- Un nouveau projet `ModelBusAdapter` est ajouté à la solution.

- Une référence à `ModelBusAdapter` est ajoutée au projet `DslPackage`. `ModelBusAdapter` a une référence au `Dsl` projet.

- Dans **DslPackage\source.extention.TT**, `|ModelBusAdapter|` est ajouté en tant que composant MEF.

## <a name="see-also"></a>Voir aussi

- [Comment : ouvrir un modèle depuis un fichier dans le code de programme](../modeling/how-to-open-a-model-from-file-in-program-code.md)
- [Guide pratique pour ajouter un gestionnaire de glisser-déplacer](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Utilisation de Visual Studio ModelBus dans un modèle de texte](../modeling/using-visual-studio-modelbus-in-a-text-template.md)
