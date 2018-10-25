---
title: Définir un gestionnaire de liaison des éléments de travail | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML API
ms.assetid: d52e0bbf-0166-4bb4-a2e3-cefed6188875
caps.latest.revision: 21
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 25143390085ec0b4d7ab56e0fef9920d7d5eceb8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49914542"
---
# <a name="define-a-work-item-link-handler"></a>Définir un gestionnaire de liens d’éléments de travail
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez créer une extension d’intégration Visual Studio qui répond quand l’utilisateur crée ou supprime un lien entre un élément de modèle ULM et un élément de travail. Par exemple, quand l'utilisateur choisit de lier un nouvel élément de travail à un élément de modèle, votre code peut initialiser les champs de l'élément de travail à partir de valeurs dans le modèle.  
  
## <a name="set-up-a-uml-extension-solution"></a>Configurer une solution d'extension UML  
 Cela vous permet de développer des gestionnaires et de les distribuer à d'autres utilisateurs. Vous devez configurer deux projets Visual Studio :  
  
-   un projet de bibliothèque de classes qui contient le code du gestionnaire de liens ;  
  
-   un projet VSIX qui joue le rôle de conteneur pour l'installation de la commande. Si vous le souhaitez, vous pouvez inclure d'autres composants dans le même VSIX.  
  
#### <a name="to-set-up-the-visual-studio-solution"></a>Pour configurer la solution Visual Studio  
  
1.  Créez un projet de bibliothèque de classes en l’ajoutant à une solution VSIX existante ou en créant une solution.  
  
    1.  Dans le menu **Fichier** , choisissez **Nouveau**, **Projet**.  
  
    2.  Sous **modèles installés**, développez **Visual C#** ou **Visual Basic**, puis, dans la colonne du milieu, cliquez sur **bibliothèque de classes**.  
  
    3.  Définissez **Solution** pour indiquer si vous souhaitez créer une solution ou ajouter un composant à une solution VSIX déjà ouverte.  
  
    4.  Définissez le nom et l’emplacement du projet, puis cliquez sur OK.  
  
2.  Créez un projet VSIX, sauf si votre solution en comporte déjà un.  
  
    1.  Dans l’ **Explorateur de solutions**, dans le menu contextuel de la solution, choisissez **Ajouter**, puis **Nouveau projet**.  
  
    2.  Sous **Modèles installés**, développez **Visual C#** ou **Visual Basic**, puis sélectionnez **Extensibilité**. Dans la colonne du milieu, choisissez **Projet VSIX**.  
  
3.  Définissez le projet VSIX comme projet de démarrage de la solution.  
  
    -   Dans l’Explorateur de solutions, dans le menu contextuel du projet VSIX, choisissez **Définir comme projet de démarrage**.  
  
4.  Dans **source.extension.vsixmanifest**, sous **contenu**, ajoutez le projet de bibliothèque de classes en tant que composant MEF.  
  
    1.  Sous l’onglet **Métadonnées** , nommez le VSIX.  
  
    2.  Sous l’onglet **Cibles d’installation** , définissez les versions de Visual Studio comme cibles.  
  
    3.  Sous l’onglet **Composants** , choisissez **Nouveau**puis, dans la boîte de dialogue, définissez :  
  
         **Type** = **Composant MEF**  
  
         **Source** = **Projet dans la solution actuelle**  
  
         **Projet** = *Votre projet de bibliothèque de classes*  
  
## <a name="defining-the-work-item-link-handler"></a>Définition du gestionnaire de liens d’éléments de travail  
 Effectuez toutes les tâches suivantes dans le projet de bibliothèque de classes.  
  
### <a name="project-references"></a>Références du projet  
 Ajoutez les assemblys [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] suivants à vos références de projet :  
  
 `Microsoft.TeamFoundation.WorkItemTracking.Client.dll`  
  
 `Microsoft.VisualStudio.TeamFoundation.WorkItemTracking.dll Microsoft.VisualStudio.Modeling.Sdk.[version]`  
  
 `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml`  
  
 `Microsoft.VisualStudio.Uml.Interfaces`  
  
 `System.ComponentModel.Composition`  
  
 `System.Drawing` -utilisé par l’exemple de code  
  
 Si vous ne trouvez pas une de ces références sous le **.Net** onglet de la **ajouter une référence** boîte de dialogue, utilisez l’onglet Parcourir pour la rechercher dans \Program Files\Microsoft Visual Studio [version] \Common7\IDE\ PrivateAssemblies\\.  
  
### <a name="import-the-work-item-namespace"></a>Importer l’espace de noms de l’élément de travail  
 Dans votre [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projet **références**, ajoutez des références aux assemblys suivants :  
  
- Microsoft.TeamFoundation.WorkItemTracking.Client.dll  
  
- Microsoft.VisualStudio.TeamFoundation.WorkItemTracking.dll  
  
  Dans le code de votre programme, importez les espaces de noms suivants :  
  
```  
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.Uml.Classes;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.TeamFoundation.WorkItemTracking;  
using System.Linq;  
```  
  
### <a name="define-the-linked-work-item-event-handler"></a>Définir le gestionnaire d'événements de l'élément de travail lié  
 Ajoutez un fichier de classe au projet de bibliothèque de classes et définissez son contenu comme indiqué ci-dessous. Adaptez le nom de la classe et de l'espace de noms à vos besoins.  
  
```  
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.Uml.Classes;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.TeamFoundation.WorkItemTracking;  
using System.Linq;  
  
namespace WorkItems  
{  
  [Export(typeof(ILinkedWorkItemExtension))]  
  public class MyWorkItemExtension : ILinkedWorkItemExtension  
  {  
    // Called before a new work item is edited by the user.  
    // Use this to initialize work item fields from the model element.  
    public void OnWorkItemCreated(System.Collections.Generic.IEnumerable<IElement> elementsToBeLinked, IWorkItemDocument workItemDocument)  
    {  
      INamedElement namedElement =  
            elementsToBeLinked.First() as INamedElement;  
      if (namedElement != null)  
        workItemDocument.Item.Title = namedElement.Name;  
  
    }  
  
    // Called when any work item is linked to a model element.  
    public void OnWorkItemLinked(System.Collections.Generic.IEnumerable<IElement> elements, string serverUri, int workItemId)  
    {  
      foreach (IElement element in elements)  
        foreach (IShape shape in element.Shapes())  
          shape.Color = System.Drawing.Color.Red;  
    }  
  
    // Called when a work item is unlinked from a model element.  
    public void OnWorkItemRemoved(IElement element, string serverUri, int workItemId)  
    {  
      foreach (IShape shape in element.Shapes())  
        shape.Color = System.Drawing.Color.White;  
    }  
  }  
}  
```  
  
## <a name="testing-the-link-handler"></a>Test du gestionnaire de liens  
 À des fins de test, exécutez votre gestionnaire de liens en mode débogage.  
  
> [!WARNING]
>  Vous devez être connecté à un contrôle de code source (SSC, Source Code Control) TFS pour créer un élément de travail ou un lien vers celui-ci. Si vous essayez d'ouvrir une connexion à un autre contrôle de code source TFS, Visual Studio ferme automatiquement la solution actuelle. Vérifiez que vous êtes connecté au contrôle de code source TFS approprié avant d'essayer de créer un élément de travail ou un lien vers celui-ci. Dans les versions ultérieures de Visual Studio, les commandes de menu ne sont pas disponibles si vous n'êtes pas connecté à un contrôle de code source.  
  
#### <a name="to-test-the-link-handler"></a>Pour tester le gestionnaire de liens  
  
1.  Appuyez sur **F5**, ou dans le menu **Déboguer** , choisissez **Démarrer le débogage**.  
  
     Une instance expérimentale de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] démarre.  
  
     **Résolution des problèmes**: si un nouveau [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ne démarre pas, vérifiez que le projet VSIX est défini comme projet de démarrage de la solution.  
  
2.  Dans l’instance expérimentale de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ouvrez ou créez un projet de modélisation, puis ouvrez ou créez un diagramme de modélisation.  
  
3.  Créez un élément de modèle tel qu'une classe UML, et attribuez-lui un nom.  
  
4.  Cliquez sur l’élément, puis cliquez sur **créer un élément de travail**.  
  
    -   Si le sous-menu affiche **ouvrir la connexion Team Foundation Server**, vous devez fermer le projet, vous connecter au TFS approprié et recommencer cette procédure.  
  
    -   Si le sous-menu affiche une liste de types d’éléments de travail, cliquez sur l’un d’entre eux.  
  
         Un nouveau formulaire d'élément de travail s'ouvre.  
  
5.  Vérifiez que le titre de l'élément de travail est le même que celui de l'élément de modèle si vous avez utilisé l'exemple de code donné dans la section précédente. Cela prouve que `OnWorkItemCreated()` a correctement fonctionné.  
  
6.  Complétez le formulaire, puis enregistrez et fermez l'élément de travail.  
  
7.  Vérifiez que l'élément de travail est maintenant de couleur rouge. Cela met en évidence `OnWorkItemLinked()` dans l'exemple de code.  
  
     **Résolution des problèmes**: si les méthodes de gestionnaire n’ont pas été exécutés, vérifiez que :  
  
    -   Le projet de bibliothèque de classes est répertorié en tant que composant MEF dans le **contenu** liste **source.extensions.manifest** dans le projet VSIX.  
  
    -   l'attribut `Export` approprié est associé à la classe de gestionnaire et la classe implémente `ILinkedWorkItemExtension` ;  
  
    -   les paramètres de tous les attributs `Import` et `Export` sont valides.  
  
## <a name="about-the-work-item-handler-code"></a>À propos du code du gestionnaire d'éléments de travail  
  
### <a name="listening-for-new-work-items"></a>Écoute de nouveaux éléments de travail  
 `OnWorkItemCreated` est appelé quand l'utilisateur choisit de créer un élément de travail à lier aux éléments de modèle. Votre code peut initialiser les champs d'éléments de travail. L'élément de travail est ensuite présenté à l'utilisateur, qui peut mettre à jour les champs et enregistrer l'élément de travail. Le lien vers un élément de modèle n'est pas créé tant que l'élément de travail n'a pas été enregistré avec succès.  
  
```  
public void OnWorkItemCreated(  
    IEnumerable<IElement> elementsToBeLinked,  
    IWorkItemDocument workItem)  
{  
  INamedElement namedElement =   
         elementsToBeLinked.First() as INamedElement;  
  if (namedElement != null)  
      workItem.Item.Title = namedElement.Name;  
}  
```  
  
### <a name="listening-for-link-creation"></a>Écoute de la création de liens  
 `OnWorkItemLinked` est appelé juste après la création d'un lien. Il est appelé que le lien pointe vers un nouvel élément de travail ou un élément existant. Il est appelé une fois pour chaque élément de travail.  
  
```  
public void OnWorkItemLinked  
        (IEnumerable<IElement> elements,   
         string serverUri, // TFS server  
         int workItemId)  
{  
  foreach (IElement element in elements)  
    foreach (IShape shape in element.Shapes())  
         shape.Color = System.Drawing.Color.Red;  
}  
```  
  
> [!NOTE]
>  Pour que cet exemple fonctionne, vous devez ajouter une référence de projet à `System.Drawing.dll` et importer l'espace de noms `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation`. Toutefois, ces ajouts ne sont pas obligatoires pour d'autres implémentations d'`OnWorkItemLinked`.  
  
### <a name="listening-for-link-removal"></a>Écoute de la suppression de liens  
 `OnWorkItemRemoved` est appelé une fois juste avant la suppression de chaque lien d'élément de travail. Si un élément de modèle est supprimé, tous ses liens sont supprimés.  
  
```  
public void OnWorkItemRemoved  
         (IElement element, string serverUri, int workItemId)  
{...}  
```  
  
## <a name="updating-a-work-item"></a>Mise à jour d'un élément de travail  
 Vous pouvez manipuler un élément de travail à l'aide des espaces de noms Team Foundation.  
  
 Pour utiliser l'exemple suivant, ajoutez ces assemblys .NET aux références de votre projet :  
  
-   Microsoft.TeamFoundation.Client.dll  
  
-   Microsoft.TeamFoundation.WorkItemTracking.Client.dll  
  
```  
  
using Microsoft.TeamFoundation.Client;  
using Microsoft.TeamFoundation.WorkItemTracking.Client;  
...  
public void OnWorkItemLinked  
        (IEnumerable<IElement> elements,   
         string serverUri, // TFS server  
         int workItemId)  
{  
  TfsTeamProjectCollection tfs =  
        TfsTeamProjectCollectionFactory  
            .GetTeamProjectCollection(new Uri(serverUri));  
  WorkItemStore workItemStore = new WorkItemStore(tfs);  
  WorkItem item = workItemStore.GetWorkItem(workItemId);  
  item.Open();  
  item.Title = "something";  
  item.Save();  
}   
```  
  
## <a name="accessing-the-work-item-reference-links"></a>Accès aux liens de la référence de l'élément de travail  
 Vous pouvez accéder aux liens comme suit :  
  
```  
//Get:  
string linkString = element.GetReference(ReferenceConstants.WorkItem);  
// Set:  
element.AddReference(ReferenceConstants.WorkItem, linkString, true);  
  
```  
  
 Le format de `linkString` est le suivant :  
  
 `string.Format(@"%{0}\{1}#{1}${2}", tfServer, projectCollection, RepositoryGuid, workItem.Id);`  
  
 où :  
  
- L'URI de votre serveur est :  
  
   `http://tfServer:8080/tfs/projectCollection`  
  
   La casse est importante dans `projectCollection`.  
  
- Vous pouvez obtenir `RepositoryGuid` à partir de votre connexion TFS :  
  
  ```csharp  
  TfsTeamProjectCollection tpc = TfsTeamProjectCollectionFactory...;  
  RepositoryGuid= tpc.InstanceId;  
  
  ```  
  
  Pour plus d’informations sur les références, consultez [attacher des chaînes de référence pour UML les éléments de modèle](../modeling/attach-reference-strings-to-uml-model-elements.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.TeamFoundation.WorkItemTracking.Client.WorkItemStore?displayProperty=fullName>   
 [Lier des éléments de modèle et des éléments de travail](../modeling/link-model-elements-and-work-items.md)   
 [Attacher des chaînes de référence à des éléments de modèle UML](../modeling/attach-reference-strings-to-uml-model-elements.md)   
 [Définir et installer une extension de modélisation](../modeling/define-and-install-a-modeling-extension.md)   
 [Programmation avec l’API UML](../modeling/programming-with-the-uml-api.md)



