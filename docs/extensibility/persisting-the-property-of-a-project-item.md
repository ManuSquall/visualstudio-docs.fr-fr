---
title: Persistance de la propriété d’un élément de projet | Microsoft Docs
description: Découvrez comment rendre persistant une propriété que vous ajoutez à un élément de projet en stockant la propriété dans le fichier projet dans votre type de projet étendu.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: how-to
helpviewer_keywords:
- properties, adding to a project item
- project items, adding properties
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 72de98e08581b105322b07390d85b95c06b1083c
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97862698"
---
# <a name="persist-the-property-of-a-project-item"></a>Rendre persistante la propriété d’un élément de projet
Vous pouvez conserver une propriété que vous ajoutez à un élément de projet, telle que l’auteur d’un fichier source. Pour ce faire, vous pouvez stocker la propriété dans le fichier projet.

 La première étape de la persistance d’une propriété dans un fichier projet consiste à obtenir la hiérarchie du projet en tant qu' <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interface. Vous pouvez obtenir cette interface à l’aide de l’Automation ou à l’aide de <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> . Une fois que vous obtenez l’interface, vous pouvez l’utiliser pour déterminer l’élément de projet actuellement sélectionné. Une fois que vous disposez de l’ID d’élément de projet, vous pouvez utiliser <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> pour ajouter la propriété.

 Dans les procédures suivantes, vous conservez la propriété *vspkg.cs* `Author` avec la valeur `Tom` dans le fichier projet.

## <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>Pour obtenir la hiérarchie du projet avec l’objet DTE

1. Ajoutez le code suivant à votre VSPackage :

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    ```

## <a name="to-persist-the-project-item-property-with-the-dte-object"></a>Pour rendre la propriété d’élément de projet persistante avec l’objet DTE

1. Ajoutez le code suivant au code donné dans la méthode de la procédure précédente :

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

## <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>Pour obtenir la hiérarchie de projet à l’aide de IVsMonitorSelection

1. Ajoutez le code suivant à votre VSPackage :

    ```csharp
    IVsHierarchy hierarchy = null;
    IntPtr hierarchyPtr = IntPtr.Zero;
    IntPtr selectionContainer = IntPtr.Zero;
    uint itemid;

    // Retrieve shell interface in order to get current selection
    IVsMonitorSelection monitorSelection =     Package.GetGlobalService(typeof(SVsShellMonitorSelection)) as     IVsMonitorSelection;
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

## <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>Pour rendre persistante la propriété d’élément de projet sélectionnée, en fonction de la hiérarchie de projet

1. Ajoutez le code suivant au code donné dans la méthode de la procédure précédente :

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

## <a name="to-verify-that-the-property-is-persisted"></a>Pour vérifier que la propriété est persistante

1. Démarrez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , puis ouvrez ou créez une solution.

2. Sélectionnez l’élément de projet VsPkg.cs dans **Explorateur de solutions**.

3. Utilisez un point d’arrêt ou déterminez si votre VSPackage est chargé et que SetItemAttribute s’exécute.

   > [!NOTE]
   > Vous pouvez charger un VSPackage en autoload dans le contexte de l’interface utilisateur <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid> . Pour plus d’informations, consultez [charger des VSPackages](../extensibility/loading-vspackages.md).

4. Fermez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , puis ouvrez le fichier projet dans le bloc-notes. Vous devez voir la \<Author> balise avec la valeur Tom, comme suit :

   ```xml
   <Compile Include="VsPkg.cs">
       <Author>Tom</Author>
   </Compile>
   ```

## <a name="see-also"></a>Voir aussi

- [Outils personnalisés](../extensibility/internals/custom-tools.md)
