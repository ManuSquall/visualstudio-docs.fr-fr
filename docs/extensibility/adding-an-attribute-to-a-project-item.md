---
title: Ajout d’un attribut à un élément de projet | Microsoft Docs
description: Découvrez comment ajouter un attribut à un élément de projet dans Visual Studio à l’aide des méthodes d’interopérabilité de l’interpréteur de commandes GetItemAttribute et SetItemAttribute.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 36fc5905fd2b1423865982a80a6cb2ba6a803cc5
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902018"
---
# <a name="add-an-attribute-to-a-project-item"></a>Ajouter un attribut à un élément de projet
Les méthodes <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> obtiennent et définissent la valeur des attributs d’un élément de projet. SetItemAttribute crée l’attribut s’il n’existe pas déjà, en l’ajoutant aux métadonnées de l’élément de projet.

## <a name="add-an-attribute-to-a-project-item"></a>Ajouter un attribut à un élément de projet

- Le code suivant utilise l' <xref:EnvDTE.DTE> objet Automation et la <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> méthode pour ajouter un attribut à un élément de projet. L’ID d’élément de projet est obtenu à partir du nom d’élément de projet « Program. cs ». L’attribut « MyAttribute » est ajouté à cet élément de projet et reçoit la valeur « MyValue ».

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        uint itemId;
        string fullPath = (string)project.ProjectItems.Item("Program.cs").Properties.Item("FullPath").Value;
        hierarchy.ParseCanonicalName(fullPath, out itemId);
        buildPropertyStorage.SetItemAttribute(itemId, "MyAttribute", "MyValue");
    }

    ```

## <a name="see-also"></a>Voir aussi
- [Conserver les données dans le fichier projet MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
