---
title: Persistance de la propriété d’un élément de projet (fr) Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- properties, adding to a project item
- project items, adding properties
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15c280f15436a5e27bcc0dcc4d2fb9e9bdd82933
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702208"
---
# <a name="persist-the-property-of-a-project-item"></a>Persévérer dans la propriété d’un élément de projet
Vous pouvez persister une propriété que vous ajoutez à un élément de projet, comme l’auteur d’un fichier source. Vous pouvez le faire en stockant la propriété dans le dossier du projet.

 La première étape pour persévérer une propriété dans un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> fichier de projet est d’obtenir la hiérarchie du projet comme interface. Vous pouvez obtenir cette interface soit <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>en utilisant Automation ou en utilisant . Une fois que vous avez obtenu l’interface, vous pouvez l’utiliser pour déterminer quel élément de projet est actuellement sélectionné. Une fois que vous avez l’ID d’élément de projet, vous pouvez utiliser <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> pour ajouter la propriété.

 Dans les procédures suivantes, vous persistez `Author` la `Tom` *VsPkg.cs* propriété avec la valeur dans le fichier du projet.

## <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>Pour obtenir la hiérarchie du projet avec l’objet DTE

1. Ajoutez le code suivant à votre VSPackage :

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    ```

## <a name="to-persist-the-project-item-property-with-the-dte-object"></a>Pour persévérer la propriété de l’article du projet avec l’objet DTE

1. Ajoutez le code suivant au code donné dans la méthode dans la procédure précédente :

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        uint itemId;
        string fullPath = (string)project.ProjectItems.Item(
            "VsPkg.cs").Properties.Item("FullPath").Value;
        hierarchy.ParseCanonicalName(fullPath, out itemId);
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

## <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>Pour obtenir la hiérarchie du projet à l’aide d’IVsMonitorSelection

1. Ajoutez le code suivant à votre VSPackage :

    ```csharp
    IVsHierarchy hierarchy = null;
    IntPtr hierarchyPtr = IntPtr.Zero;
    IntPtr selectionContainer = IntPtr.Zero;
    uint itemid;

    // Retrieve shell interface in order to get current selection
    IVsMonitorSelection monitorSelection =     Package.GetGlobalService(typeof(SVsShellMonitorSelection)) as     IVsMonitorSelection;
    if (monitorSelection == null)
        throw new InvalidOperationException();

    try
    {
        // Get the current project hierarchy, project item, and selection container for the current selection
        // If the selection spans multiple hierachies, hierarchyPtr is Zero
        IVsMultiItemSelect multiItemSelect = null;
        ErrorHandler.ThrowOnFailure(
            monitorSelection.GetCurrentSelection(
                out hierarchyPtr, out itemid,
                out multiItemSelect, out selectionContainer));

        // We only care if there is only one node selected in the tree
        if (!(itemid == VSConstants.VSITEMID_NIL ||
            hierarchyPtr == IntPtr.Zero ||
            multiItemSelect != null ||
            itemid == VSConstants.VSITEMID_SELECTION))
        {
            hierarchy = Marshal.GetObjectForIUnknown(hierarchyPtr)
                as IVsHierarchy;
        }
    }
    finally
    {
        if (hierarchyPtr != IntPtr.Zero)
            Marshal.Release(hierarchyPtr);
        if (selectionContainer != IntPtr.Zero)
            Marshal.Release(selectionContainer);
    }
    ```

## <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>Pour poursuivre la propriété de l’élément de projet sélectionné, compte tenu de la hiérarchie du projet

1. Ajoutez le code suivant au code donné dans la méthode dans la procédure précédente :

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

## <a name="to-verify-that-the-property-is-persisted"></a>Pour vérifier que la propriété est persistée

1. Démarrez, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] puis ouvrez ou créez une solution.

2. Sélectionnez l’élément du projet VsPkg.cs dans **Solution Explorer**.

3. Utilisez un point d’arrêt ou déterminez autrement que votre VSPackage est chargé et que SetItemAttribute s’exécute.

   > [!NOTE]
   > Vous pouvez recharger automatiquement un VSPackage dans le contexte <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>de l’interface utilisateur . Pour plus d’informations, voir [Load VSPackages](../extensibility/loading-vspackages.md).

4. Fermez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] puis ouvrez le dossier du projet dans Notepad. Vous devriez \<voir l’auteur> tag avec la valeur Tom, comme suit:

   ```xml
   <Compile Include="VsPkg.cs">
       <Author>Tom</Author>
   </Compile>
   ```

## <a name="see-also"></a>Voir aussi

- [Outils personnalisés](../extensibility/internals/custom-tools.md)
