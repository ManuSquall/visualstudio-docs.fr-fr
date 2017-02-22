---
title: "Int&#233;gration de mod&#232;les &#224; l’aide de Visual Studio Modelbus | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2ff722f3-21d6-44e2-9efd-f6694aee9987
caps.latest.revision: 26
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 26
---
# Int&#233;gration de mod&#232;les &#224; l’aide de Visual Studio Modelbus
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus fournit une méthode de création de liens entre les modèles et d’autres outils dans les modèles. Par exemple, vous pouvez lier des modèles de langage spécifique au domaine \(DSL\) et les modèles UML. Vous pouvez créer un ensemble intégré de DSL.  
  
 ModelBus vous permet de créer une référence unique à un modèle ou à un élément spécifique à l’intérieur d’un modèle. Cette référence peut être stockée en dehors du modèle, par exemple, dans un élément dans un autre modèle. Lorsque, ultérieurement, un outil veut obtenir l’accès à l’élément, l’infrastructure du Bus de modèle se charge le modèle approprié et l’élément. Si vous le souhaitez, vous pouvez afficher le modèle pour l’utilisateur. Si le fichier ne peut pas être accessible dans son emplacement précédent, ModelBus demande à l’utilisateur pour le trouver. Si l’utilisateur trouve le fichier, ModelBus corrige toutes les références à ce fichier.  
  
> [!NOTE]
>  Dans le courant [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] implémentation de ModelBus, les modèles liés doit être des éléments dans le même [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solution.  
  
 Pour plus d’informations et des exemples de code, consultez :  
  
-   [Comment : ajouter un gestionnaire glisser\-déplacer](../modeling/how-to-add-a-drag-and-drop-handler.md)  
  
-   [Modélisation du Kit de développement logiciel pour Visual Studio](http://www.microsoft.com/download/details.aspx?id=40754)  
  
##  <a name="provide"></a> Fournir un accès à une ligne DSL  
 Avant de pouvoir créer les références ModelBus à un modèle ou de ses éléments, vous devez définir un ModelBusAdapter pour le DSL. Le moyen le plus simple pour cela consiste à utiliser le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Extension de Bus de modèle, qui ajoute des commandes au concepteur DSL.  
  
###  <a name="expose"></a> Pour exposer une définition DSL au Bus de modèles  
  
1.  Téléchargez et installez l’extension Visual Studio Model Bus, sauf si vous l’avez déjà installé. Pour plus d’informations, consultez [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
2.  Ouvrez le fichier de définition DSL. Cliquez sur l’aire de conception, puis cliquez sur **Activer Modelbus**.  
  
3.  Dans la boîte de dialogue, choisissez **je veux exposer ce DSL au ModelBus**. Vous pouvez choisir les deux options si vous souhaitez que ce DSL expose ses modèles et d’utiliser des références aux autres DSL.  
  
4.  Cliquez sur **OK**. Un nouveau projet « ModelBusAdapter » est ajouté à la solution DSL.  
  
5.  Si vous souhaitez accéder au DSL à partir d’un modèle de texte, vous devez modifier AdapterManager.tt dans le nouveau projet. Omettre cette étape si vous souhaitez accéder au DSL à partir de tout autre code tels que les commandes et gestionnaires d’événements. Pour plus d'informations, consultez [Utilisation de Visual Studio ModelBus dans un modèle de texte](../modeling/using-visual-studio-modelbus-in-a-text-template.md).  
  
    1.  Modifier la classe de base d’AdapterManagerBase en <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>.  
  
    2.  À la fin du fichier, insérez cet attribut additionnel devant la classe AdapterManager :  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
    3.  Dans le références du projet ModelBusAdapter, ajoutez **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**.  
  
     Si vous souhaitez accéder au DSL à partir des modèles de texte et d’autre code, vous avez besoin de deux cartes, modifié et l’autre non modifié.  
  
6.  Cliquez sur **transformer tous les modèles**.  
  
7.  Régénérez la solution.  
  
 Il est désormais possible pour ModelBus d’ouvrir les instances de cette solution DSL.  
  
 Le dossier `ModelBusAdapters\bin\*` contient les assemblys générés par le `Dsl` projet et le `ModelBusAdapters` projet. Pour faire référence à ce DSL à partir d’un autre DSL, vous devez importer ces assemblys.  
  
### S’assurer que les éléments peuvent être référencés.  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Adaptateurs ModelBus utilisent le guid d’un élément pour l’identifier, par défaut. Ces identificateurs doivent donc être conservées dans le fichier de modèle.  
  
##### Pour vous assurer de cet élément Qu'id sont conservées.  
  
1.  Ouvrez DslDefinition.dsl.  
  
2.  Dans l’Explorateur DSL, développez **comportement de sérialisation Xml**, puis **les données de classe**.  
  
3.  Pour chaque classe à laquelle vous souhaitez créer le Bus de modèle fait référence à :  
  
     Cliquez sur le nœud de classe et dans la fenêtre Propriétés, assurez\-vous que **Id de sérialisation** est défini sur `true`.  
  
 Ou bien, si vous souhaitez utiliser des noms d’élément pour identifier des éléments au lieu de GUID, vous pouvez remplacer les parties des adaptateurs générés. Substituer les méthodes suivantes dans la classe d’adaptateur :  
  
-   Substituer `GetElementId` pour renvoyer l’identificateur que vous souhaitez utiliser. Cette méthode est appelée lors de la création de références.  
  
-   Substituer `ResolveElementReference` pour localiser l’élément approprié à partir d’une référence de Bus de modèle.  
  
##  <a name="editRef"></a> Accès à un DSL à partir d’un autre DSL  
 Vous pouvez stocker les références de bus de modèle dans une propriété de domaine dans un langage DSL, et vous pouvez écrire du code personnalisé qui les utilise. Vous pouvez également laisser à l’utilisateur de créer une référence de bus de modèles en sélectionnant un fichier de modèle et un élément qu’il contient.  
  
 Pour activer un DSL faire référence à un autre DSL, vous devez d’abord le vous un *consommateur* de références de bus de modèle.  
  
#### Pour permettre à un DSL de consommer les références à un DSL exposé  
  
1.  Dans le schéma de définition DSL, avec le bouton droit de la partie principale du diagramme, puis **Activer Modelbus**.  
  
2.  Dans la boîte de dialogue, sélectionnez **Activer ce modèle pour consommer les références de bus de modèles**.  
  
3.  Dans le projet Dsl du DSL consommateur, ajoutez les assemblys suivants aux références du projet. Vous trouverez ces assemblys \(fichiers .dll\) dans le répertoire ModelBusAdapter\\bin\\ \* du DSL exposé.  
  
    -   L’assembly du DSL exposé, par exemple **Fabrikam.FamilyTree.Dsl.dll**  
  
    -   Le modèle exposé bus assembly d’adaptateur, par exemple **Fabrikam.FamilyTree.ModelBusAdapter.dll**  
  
4.  Ajoutez les assemblys .NET suivants aux références du projet du projet DSL consommateur.  
  
    1.  **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**  
  
    2.  **Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0.dll**  
  
#### Pour stocker une référence de Bus de modèle dans une propriété de domaine  
  
1.  Dans la définition DSL du DSL consommateur, ajoutez une propriété de domaine à une classe de domaine et définir son nom.  
  
2.  Dans les fenêtre Propriétés, avec la propriété du domaine sélectionnée, définissez **Type** à `ModelBusReference`.  
  
 À ce stade, le code de programme peut définir la valeur de propriété, mais elle est en lecture seule dans la fenêtre Propriétés.  
  
 Vous pouvez autoriser les utilisateurs à définir la propriété avec un éditeur de références ModelBus spécialisé. Il existe deux versions de cet éditeur ou *sélecteur :* une permet aux utilisateurs de choisir un fichier de modèle, et l’autre permet aux utilisateurs de choisir un fichier de modèle et un élément dans le modèle.  
  
#### Pour autoriser l’utilisateur à définir une référence de Bus de modèle dans une propriété de domaine  
  
1.  Avec le bouton droit de la propriété de domaine, puis cliquez sur **les modifier les propriétés propres**. Une boîte de dialogue s’ouvre. Il s’agit du *sélecteur de Bus de modèle*.  
  
2.  Sélectionnez l’option appropriée **type de ModelBusReference**: à un modèle ou à un élément à l’intérieur d’un modèle.  
  
3.  Dans la chaîne de filtre de boîte de dialogue de fichier, entrez une chaîne, tel que `Family Tree files |*.ftree`. Remplacez l’extension de votre DSL exposé.  
  
4.  Si vous choisissez de faire référence à un élément dans un modèle, vous pouvez ajouter une liste de types que l’utilisateur peut sélectionner, par exemple Company.FamilyTree.Person.  
  
5.  Cliquez sur **OK**, puis cliquez sur **transformer tous les modèles** dans la barre d’outils de l’Explorateur de solutions.  
  
    > [!WARNING]
    >  Si vous n’avez pas sélectionné un modèle valide ou une entité, le bouton OK aura aucun effet, même s’il peut paraître activé.  
  
6.  Si vous avez spécifié une liste de types cibles tels que Company.FamilyTree.Person, puis vous devez ajouter une référence d’assembly à votre projet DSL, faisant référence à la DLL du DSL cible, par exemple Company.FamilyTree.Dsl.dll  
  
#### Pour tester une référence de Bus de modèle  
  
1.  Générez les deux DSL exposé et la consommation.  
  
2.  Exécutez une des DSL en mode expérimental en appuyant sur F5 ou CTRL \+ F5.  
  
3.  Dans le projet de débogage dans l’instance expérimentale de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ajouter des fichiers qui sont des instances de chaque DSL.  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus peut uniquement résoudre les références aux modèles qui sont des éléments de la même [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solution. Par exemple, vous ne peut pas créer une référence à un fichier de modèle dans une autre partie de votre système de fichiers.  
  
4.  Créer des éléments et les liens dans l’instance du DSL exposé et enregistrez\-le.  
  
5.  Ouvrez une instance du DSL consommateur et sélectionnez un élément de modèle qui a une propriété de référence de bus de modèle.  
  
6.  Dans la fenêtre Propriétés, double\-cliquez sur la propriété de référence de bus de modèles. La boîte de dialogue Sélecteur s’ouvre.  
  
7.  Cliquez sur **Parcourir** et sélectionnez l’instance du DSL exposé.  
  
     Le sélecteur vous permettra également choisir un élément dans le modèle, si vous avez spécifié le type spécifique à l’élément de référence de bus de modèle.  
  
## Création de références dans le Code de programme  
 Lorsque vous souhaitez stocker une référence à un modèle ou un élément à l’intérieur d’un modèle, vous créez un `ModelBusReference`. Il existe deux types de `ModelBusReference`: les références et élément de modèle.  
  
 Pour créer une référence de modèle, vous devez l’AdapterManager du DSL dont le modèle est une instance et le nom de fichier ou [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] élément de projet du modèle.  
  
 Pour créer une référence d’élément, vous avez besoin d’un adaptateur pour le fichier de modèle et de l’élément que vous voulez faire.  
  
> [!NOTE]
>  Avec le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus, vous pouvez créer des références à des éléments dans le même [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solution.  
  
### Importer les assemblys DSL exposés  
 Dans le projet consommateur, ajoutez des références de projet aux assemblys DSL et ModelBusAdapter du DSL exposé.  
  
 Par exemple, supposons que vous souhaitez stocker les références ModelBus dans les éléments d’un DSL MusicLibrary. Les références ModelBus feront référence aux éléments du DSL FamilyTree. Dans la `Dsl` projet de la solution MusicLibrary, dans le nœud Références, ajoutez des références aux assemblys suivants :  
  
-   Fabrikam.FamilyTree.Dsl.dll \- le DSL exposé.  
  
-   Fabrikam.FamilyTree.ModelBusAdapters.dll \- l’adaptateur ModelBus du DSL exposé.  
  
-   Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0  
  
-   Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0  
  
 Ces assemblys se trouve dans le `ModelBusAdapters` projet du DSL exposé, sous `bin\*`.  
  
 Dans le fichier de code où vous allez créer des références, vous devrez généralement importer ces espaces de noms :  
  
```  
// The namespace of the DSL you want to reference:  
using Fabrikam.FamilyTree;  // Exposed DSL  
using Fabrikam.FamilyTree.ModelBusAdapters;  
using Microsoft.VisualStudio.Modeling.Integration;  
using System.Linq;  
...  
```  
  
### Pour créer une référence à un modèle  
 Pour créer une référence de modèle, vous accédez à l’AdapterManager du DSL exposé et l’utiliser pour créer une référence au modèle. Vous pouvez spécifier un chemin de fichier, ou un `EnvDTE.ProjectItem`.  
  
 À partir de la classe AdapterManager, vous pouvez obtenir un adaptateur, qui fournit l’accès aux éléments individuels dans le modèle.  
  
> [!NOTE]
>  Vous devez supprimer une carte lorsque vous avez terminé avec lui. La façon la plus pratique pour y parvenir est avec un `using` instruction. L'exemple suivant illustre ce comportement.  
  
```  
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
  
 Si vous souhaitez être en mesure d’utiliser `modelReference` ultérieurement, vous pouvez la stocker dans une propriété de domaine qui possède le Type externe `ModelBusReference`:  
  
```  
using Transaction t = this.Store.TransactionManager  
    .BeginTransaction("keep reference"))  
{  
  artist.FamilyTreeReference = modelReference;  
  t.Commit();  
}  
```  
  
 Pour permettre aux utilisateurs de modifier cette propriété de domaine, utilisez `ModelReferenceEditor` comme paramètre dans l’attribut Editor. Pour plus d’informations, consultez [permet à l’utilisateur à modifier une référence](#editRef).  
  
### Pour créer une référence à un élément  
 L’adaptateur que vous avez créé pour le modèle permet de créer et de résoudre les références.  
  
```  
// person is an element in the FamilyTree model:  
ModelBusReference personReference =   
  adapter.GetElementReference(person);  
```  
  
 Si vous souhaitez être en mesure d’utiliser `elementReference` ultérieurement, vous pouvez la stocker dans une propriété de domaine qui possède le Type externe `ModelBusReference`. Pour permettre aux utilisateurs de le modifier, utilisez `ModelElementReferenceEditor` comme paramètre dans l’attribut Editor. Pour plus d’informations, consultez [permet à l’utilisateur à modifier une référence](#editRef).  
  
### Résolution des références  
 Si vous avez un `ModelBusReference` \(MBR\) que vous pouvez obtenir le modèle ou l’élément de modèle auquel il fait référence. Si l’élément est présenté sur un diagramme ou une autre vue, vous pouvez ouvrir la vue et sélectionnez l’élément.  
  
 Vous pouvez créer une carte à partir d’une MBR. À partir de la carte, vous pouvez obtenir la racine du modèle. Vous pouvez également résoudre les MBR qui font référence à des éléments spécifiques dans le modèle.  
  
```  
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
  
##### Pour résoudre les références ModelBus dans un modèle de texte  
  
1.  Le langage DSL vous voulez accéder doit posséder une carte de ModelBus qui a été configuré pour l’accès à des modèles de texte. Pour plus d'informations, consultez [Fournir un accès à une ligne DSL](#provide).  
  
2.  En règle générale, vous accédez à une cible DSL à l’aide d’une référence de Bus de modèle \(MBR\) stockée dans un DSL source. Par conséquent, votre modèle comprend la directive du DSL source, ainsi que le code pour résoudre la MBR. Pour plus d’informations sur les modèles de texte, consultez la page [Génération de code à partir d'un langage spécifique à un domaine](../modeling/generating-code-from-a-domain-specific-language.md).  
  
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
  
 Pour plus d’informations et une procédure pas à pas, consultez [Utilisation de Visual Studio ModelBus dans un modèle de texte](../modeling/using-visual-studio-modelbus-in-a-text-template.md)  
  
## Sérialisation d’une ModelBusReference  
 Si vous souhaitez stocker un `ModelBusReference` \(MBR\) sous la forme d’une chaîne, vous pouvez sérialiser :  
  
```  
string serialized = modelBus.SerializeReference(elementReference);  
// Store it anywhere, then get it back again:  
ModelBusReference elementReferenceRestored =  
    modelBus.DeserializeReference(serialized, null);  
```  
  
 Une MBR est sérialisée de cette manière est indépendante du contexte. Si vous utilisez l’adaptateur de Bus de modèle basé sur fichier simple, le MBR contient un chemin d’accès absolu. Cela suffit si les fichiers de modèle d’instance ne sont jamais déplacés. Toutefois, les fichiers de modèle seront généralement des éléments dans un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projet. Vos utilisateurs attendent de pouvoir déplacer la totalité du projet aux différentes parties du système de fichiers. Ils s’attendront aussi être en mesure de maintenir le projet sous contrôle de code source et l’ouvrir sur différents ordinateurs. Les noms de chemin d’accès doivent par conséquent être sérialisés par rapport à l’emplacement du projet qui contient les fichiers.  
  
### Sérialisation par rapport à un chemin d’accès de fichier spécifié  
 Un `ModelBusReference` contient un `ReferenceContext`, c'est\-à\-dire un dictionnaire dans lequel vous pouvez stocker des informations telles que le chemin d’accès de fichier par rapport à laquelle il doit être sérialisée.  
  
 Pour sérialiser par rapport à un chemin d’accès :  
  
```  
elementReference.ReferenceContext.Add(  
   ModelBusReferencePropertySerializer.FilePathSaveContextKey,   
   currentProjectFilePath);  
string serialized = modelBus.SerializeReference(elementReference);  
```  
  
 Pour récupérer la référence de la chaîne :  
  
```  
ReferenceContext context = new ReferenceContext();  
context.Add(ModelBusReferencePropertySerializer.FilePathLoadContextKey,  
    currentProjectFilePath);  
ModelBusReference elementReferenceRestored =  
    modelBus.DeserializeReference(serialized, context);  
```  
  
### ModelBusReference créées par d’autres cartes.  
 Les informations suivantes sont utiles si vous souhaitez créer votre propre adaptateur.  
  
 Un `ModelBusReference` \(MBR\) se compose de deux parties : l’en\-tête MBR, désérialisé par le bus de modèles, et spécifique à un adaptateur qui est géré par le Gestionnaire d’adaptateur spécifique. Cela vous permet de fournir votre propre format de sérialisation de l’adaptateur. Par exemple, vous pouvez faire référence à une base de données plutôt qu’un fichier, ou vous pouvez stocker des informations supplémentaires dans la référence d’adaptateur. Votre propre adaptateur peut placer des informations supplémentaires dans le `ReferenceContext`.  
  
 Lorsque vous désérialisez une MBR, vous devez fournir un ReferenceContext, qui est ensuite stocké dans l’objet MBR. Lorsque vous sérialisez une MBR, le ReferenceContext stocké est utilisé par l’adaptateur pour aider à générer la chaîne. La chaîne désérialisée ne contient pas toutes les informations du referencecontext. Par exemple, dans l’adaptateur de fichier simple, le ReferenceContext contient un chemin d’accès racine, qui n’est pas stockée dans la chaîne MBR sérialisée.  
  
 Le MBR est désérialisé en deux étapes :  
  
-   `ModelBusReferencePropertySerializer` est le sérialiseur standard qui traite l’en\-tête MBR. Il utilise le langage DSL standard `SerializationContext` sac de propriétés, qui est stocké dans le `ReferenceContext` à l’aide de la clé `ModelBusReferencePropertySerializer.ModelBusLoadContextKey`. En particulier, la `SerializationContext` doit contenir une instance de `ModelBus`.  
  
-   Votre adaptateur ModelBus porte sur la partie spécifique à l’adaptateur de la MBR. Il peut utiliser les informations supplémentaires stockées dans le ReferenceContext de la MBR. L’adaptateur de fichier simple conserve les chemins d’accès du fichier racine en utilisant les touches `FilePathLoadContextKey` et `FilePathSaveContextKey`.  
  
     Une référence de l’adaptateur dans un fichier de modèle est désérialisée uniquement lorsqu’elle est utilisée.  
  
## Pour créer un modèle  
  
### Création, ouverture et la modification d’un modèle  
 Le fragment suivant provient de l’exemple de Machine d’état sur le site Web VMSDK. Il illustre l’utilisation des ModelBusReference pour créer et ouvrir un modèle et pour obtenir le diagramme associé au modèle.  
  
 Dans cet exemple, le nom du DSL cible est StateMachine. Plusieurs noms sont dérivées, telles que le nom de la classe de modèle et le nom du ModelBusAdapter.  
  
```  
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
  
## Validation des références  
 Le BrokenReferenceDetector teste toutes les propriétés de domaine dans un magasin qui peut contenir les ModelBusReference. Il appelle l’action que vous fournissez pour lesquels une action est trouvée. Cela est particulièrement utile pour les méthodes de validation. La méthode de validation suivante teste le magasin lors d’une tentative d’enregistrement du modèle et signale les références rompues dans la fenêtre des erreurs :  
  
```  
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
  
## Actions effectuées par le ModelBus Extension  
 Les informations suivantes n’est pas indispensable, mais il peuvent être utiles si vous utilisez beaucoup de ModelBus.  
  
 Le ModelBus Extension apporte les modifications suivantes dans votre solution DSL.  
  
 Lorsque vous cliquez sur le diagramme de définition DSL, cliquez sur **Activer Modelbus**, puis sélectionnez **Activer ce DSL consommer le ModelBus**:  
  
-   Dans le projet DSL, une référence est ajoutée au **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**  
  
-   Dans la définition DSL, une référence de Type externe est ajoutée : `Microsoft.VisualStudio.Modeling.Integration.ModelBusReference`.  
  
     Vous pouvez voir la référence dans **Explorateur DSL**, sous **Types de domaines**. Pour ajouter manuellement des références aux types externes, cliquez sur le nœud racine.  
  
-   Un nouveau fichier de modèle est ajouté, **Dsl\\GeneratedCode\\ModelBusReferencesSerialization.tt**.  
  
 Lorsque vous définissez le type d’une propriété de domaine sur ModelBusReference, puis avec le bouton droit de la propriété et cliquez sur **Activer les propriétés propres**:  
  
-   Plusieurs attributs CLR sont ajoutés à la propriété de domaine. Vous pouvez les voir dans le champ attributs personnalisés dans la fenêtre Propriétés. Dans **Dsl\\GeneratedCode\\DomainClasses.cs**, vous pouvez voir les attributs de la déclaration de propriété :  
  
    ```  
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
  
 Lorsque vous avec le bouton droit sur le diagramme de définition DSL, cliquez sur **Activer ModelBus**, puis sélectionnez **exposer ce DSL au ModelBus**:  
  
-   Un nouveau projet `ModelBusAdapter` est ajouté à la solution.  
  
-   Une référence à `ModelBusAdapter` est ajouté à la `DslPackage` projet.`ModelBusAdapter` fait référence à la `Dsl` projet.  
  
-   Dans **DslPackage\\source.extention.tt**, `|ModelBusAdapter|` est ajouté en tant que composant MEF.  
  
## Voir aussi  
 [Comment : ouvrir un modèle depuis un fichier dans le code de programme](../modeling/how-to-open-a-model-from-file-in-program-code.md)   
 [Integrate UML models with other models and tools](../modeling/integrate-uml-models-with-other-models-and-tools.md)   
 [Comment : ajouter un gestionnaire glisser\-déplacer](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Utilisation de Visual Studio ModelBus dans un modèle de texte](../modeling/using-visual-studio-modelbus-in-a-text-template.md)