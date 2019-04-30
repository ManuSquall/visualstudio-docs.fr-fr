---
title: Vérification des sous-types d’un projet en cours d’exécution | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ec71ce9be704566640a90c9187abe77f5cc3fe3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62553986"
---
# <a name="verify-subtypes-of-a-project-at-run-time"></a>Vérifiez les sous-types d’un projet en cours d’exécution
Un VSPackage qui dépend d’un sous-type de projet personnalisé doit inclure une logique à rechercher qui sous-type afin qu’elle peut échouer normalement si le sous-type n’est pas présent. La procédure suivante montre comment vérifier la présence d’un sous-type spécifié.

### <a name="to-verify-the-presence-of-a-subtype"></a>Pour vérifier la présence d’un sous-type

1. Obtenir la hiérarchie de projet à partir des objets en tant que projet et solution un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objet en ajoutant le code suivant à votre VSPackage.

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

2. Effectuer un cast de la hiérarchie pour le <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> interface.

    ```csharp
    IVsAggregatableProjectCorrected AP;
    AP = hierarchy as IVsAggregatableProjectCorrected;

    ```

3. Obtenir la liste des GUID de type de projet en appelant le <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>.

    ```csharp
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();

    ```

4. Vérifiez la liste pour le GUID du sous-type spécifié.

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