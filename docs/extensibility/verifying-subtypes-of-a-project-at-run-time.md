---
title: Vérification des sous-types d’un projet à l’heure de l’exécution (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f0d739a9f8734dd8941e3254d03364cbf4c77350
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698183"
---
# <a name="verify-subtypes-of-a-project-at-run-time"></a>Vérifier les sous-types d’un projet à l’heure de l’exécution
Un VSPackage qui dépend d’un sous-type de projet personnalisé devrait inclure la logique de rechercher ce sous-type afin qu’il puisse échouer gracieusement si le sous-type n’est pas présent. La procédure suivante montre comment vérifier la présence d’un sous-type spécifié.

### <a name="to-verify-the-presence-of-a-subtype"></a>Vérifier la présence d’un sous-type

1. Obtenez la hiérarchie du projet et <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> les objets de solution comme objet en ajoutant le code suivant à votre VSPackage.

    ```csharp
    EnvDTE.DTE dte;
    dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));

    EnvDTE.Project project;
    project = dte.Solution.Projects.Item(1);

    IVsSolution solution;
    solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));

    IVsHierarchy hierarchy;
    hierarchy = solution.GetProjectOfUniqueName(project.UniqueName);

    ```

2. Jetez la <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> hiérarchie à l’interface.

    ```csharp
    IVsAggregatableProjectCorrected AP;
    AP = hierarchy as IVsAggregatableProjectCorrected;

    ```

3. Obtenez la liste des GUIDs de <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>type projet en invoquant le .

    ```csharp
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();

    ```

4. Consultez la liste pour le GUID du sous-type spécifié.

    ```csharp
    // Replace the string "MyGUID" with the GUID of the subtype.
    string guidMySubtype = "MyGUID";
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)
    {
        // The specified subtype is present.
    }
    ```

## <a name="see-also"></a>Voir aussi
- [Sous-types de projets](../extensibility/internals/project-subtypes.md)
- [Conception de sous-types de projet](../extensibility/internals/project-subtypes-design.md)
- [Propriétés et méthodes étendues par des sous-types de projet](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)
