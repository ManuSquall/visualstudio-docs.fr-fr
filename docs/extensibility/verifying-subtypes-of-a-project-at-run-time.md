---
title: Vérification des sous-types d’un projet au moment de l’exécution | Microsoft Docs
description: Découvrez comment faire en sorte que votre VSPackage vérifie la présence d’un sous-type de projet personnalisé spécifié dont il dépend.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 621a40e1857d7c78ec4c5be08a3b7c3808a0d48b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905471"
---
# <a name="verify-subtypes-of-a-project-at-run-time"></a>Vérifier les sous-types d’un projet au moment de l’exécution
Un VSPackage qui dépend d’un sous-type de projet personnalisé doit inclure une logique pour rechercher ce sous-type afin qu’il puisse échouer correctement si le sous-type n’est pas présent. La procédure suivante montre comment vérifier la présence d’un sous-type spécifié.

### <a name="to-verify-the-presence-of-a-subtype"></a>Pour vérifier la présence d’un sous-type

1. Obtenir la hiérarchie de projet à partir des objets projet et solution en tant qu' <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objet en ajoutant le code suivant à votre VSPackage.

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

2. Effectuez un cast de la hiérarchie en <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> interface.

    ```csharp
    IVsAggregatableProjectCorrected AP;
    AP = hierarchy as IVsAggregatableProjectCorrected;

    ```

3. Obtient la liste des GUID de type de projet en appelant <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A> .

    ```csharp
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();

    ```

4. Vérifiez la liste du GUID du sous-type spécifié.

    ```csharp
    // Replace the string "MyGUID" with the GUID of the subtype.
    string guidMySubtype = "MyGUID";
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)
    {
        // The specified subtype is present.
    }
    ```

## <a name="see-also"></a>Voir aussi
- [Sous-types de projet](../extensibility/internals/project-subtypes.md)
- [Conception de sous-types de projet](../extensibility/internals/project-subtypes-design.md)
- [Propriétés et méthodes étendues par les sous-types de projet](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)
