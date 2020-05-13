---
title: Ajout d’un attribut à un élément de projet (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 059eef0b6a215f1f02c77df63f777fbfda5dff19
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740188"
---
# <a name="add-an-attribute-to-a-project-item"></a>Ajouter un attribut à un élément de projet
Les <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> méthodes <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> et obtenir et définir la valeur des attributs d’un élément de projet. SetItemAttribute crée l’attribut s’il n’existe pas déjà, l’ajoutant aux métadonnées de l’élément du projet.

## <a name="add-an-attribute-to-a-project-item"></a>Ajouter un attribut à un élément de projet

- Le code suivant <xref:EnvDTE.DTE> utilise l’objet d’automatisation et la <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> méthode pour ajouter un attribut à un élément de projet. L’ID de l’élément du projet est obtenu à partir du nom de l’élément du projet « program.cs ». L’attribut "MyAttribute" est ajouté à cet élément de projet et compte tenu de la valeur "MyValue".

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
- [Données persistantes dans le fichier du projet MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
