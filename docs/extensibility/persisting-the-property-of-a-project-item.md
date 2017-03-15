---
title: "Conserver la propri&#233;t&#233; d&#39;un &#233;l&#233;ment de projet | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "propriétés, ajouter à un élément de projet"
  - "éléments de projet, ajouter des propriétés"
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Conserver la propri&#233;t&#233; d&#39;un &#233;l&#233;ment de projet
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Voulez\-vous conserver une propriété que vous ajoutez à un élément de projet, telles que l'auteur d'un fichier source. Pour cela, en stockant la propriété dans le fichier projet.  
  
 Pour conserver une propriété dans un fichier de projet la première étape consiste à obtenir la hiérarchie du projet comme une <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interface. Vous pouvez obtenir cette interface en utilisant l'automatisation ou à l'aide de <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>. Une fois que vous obtenez l'interface, vous pouvez l'utiliser pour déterminer quel élément de projet est sélectionné. Une fois que vous avez l'ID d'élément de projet, vous pouvez utiliser <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> pour ajouter la propriété.  
  
 Dans les procédures suivantes, vous rendre persistante la propriété VsPkg.cs `Author` avec la valeur `Tom` dans le fichier projet.  
  
### Pour obtenir la hiérarchie de projet avec l'objet DTE  
  
1.  Ajoutez le code suivant à votre package VS :  
  
    ```c#  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE)); EnvDTE.Project project = dte.Solution.Projects.Item(1); string uniqueName = project.UniqueName; IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution)); IVsHierarchy hierarchy; solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    ```  
  
### Pour conserver la propriété d'élément de projet avec l'objet DTE  
  
1.  Le code dans la méthode dans la procédure précédente, ajoutez le code suivant :  
  
    ```c#  
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage; if (buildPropertyStorage != null) { uint itemId; string fullPath = (string)project.ProjectItems.Item( "VsPkg.cs").Properties.Item("FullPath").Value; hierarchy.ParseCanonicalName(fullPath, out itemId); buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom"); }  
    ```  
  
### Pour obtenir la hiérarchie de projet à l'aide de IVsMonitorSelection  
  
1.  Ajoutez le code suivant à votre package VS :  
  
    ```c#  
    IVsHierarchy hierarchy = null; IntPtr hierarchyPtr = IntPtr.Zero; IntPtr selectionContainer = IntPtr.Zero; uint itemid; // Retrieve shell interface in order to get current selection IVsMonitorSelection monitorSelection =     Package.GetGlobalService(typeof(SVsShellMonitorSelection)) as     IVsMonitorSelection; if (monitorSelection == null) throw new InvalidOperationException(); try { // Get the current project hierarchy, project item, and selection container for the current selection // If the selection spans multiple hierachies, hierarchyPtr is Zero IVsMultiItemSelect multiItemSelect = null; ErrorHandler.ThrowOnFailure( monitorSelection.GetCurrentSelection( out hierarchyPtr, out itemid, out multiItemSelect, out selectionContainer)); // We only care if there is only one node selected in the tree if (!(itemid == VSConstants.VSITEMID_NIL || hierarchyPtr == IntPtr.Zero || multiItemSelect != null || itemid == VSConstants.VSITEMID_SELECTION)) { hierarchy = Marshal.GetObjectForIUnknown(hierarchyPtr) as IVsHierarchy; } } finally { if (hierarchyPtr != IntPtr.Zero) Marshal.Release(hierarchyPtr); if (selectionContainer != IntPtr.Zero) Marshal.Release(selectionContainer); }  
    ```  
  
2.  
  
### Pour conserver la propriété d'élément de projet sélectionné, étant donné la hiérarchie de projet  
  
1.  Le code dans la méthode dans la procédure précédente, ajoutez le code suivant :  
  
    ```  
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage; if (buildPropertyStorage != null) { buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom"); }  
    ```  
  
### Pour vérifier que la propriété est conservée.  
  
1.  Démarrer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] puis ouvrez ou créez une solution.  
  
2.  Sélectionnez le projet élément VsPkg.cs dans **l'Explorateur de solutions**.  
  
3.  Utilisez un point d'arrêt ou sinon déterminer que votre VSPackage est chargé et que SetItemAttribute s'exécute.  
  
    > [!NOTE]
    >  Vous pouvez charger automatiquement un VSPackage dans le contexte de l'interface utilisateur <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionExists>. Pour plus d'informations, consultez [Chargement des packages VS](../extensibility/loading-vspackages.md).  
  
4.  Fermer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] puis ouvrez le fichier de projet dans le bloc\-notes. Vous devez voir la balise \< Author \> avec la valeur Tom, comme suit :  
  
    ```  
    <Compile Include="VsPkg.cs"> <Author>Tom</Author> </Compile>  
    ```  
  
## Voir aussi  
 [Outils personnalisés](../extensibility/internals/custom-tools.md)