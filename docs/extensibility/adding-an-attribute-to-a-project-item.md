---
title: Ajout d’un attribut à un élément de projet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8524ebc866d92cfe39a19dc79165da7c38025628
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352378"
---
# <a name="add-an-attribute-to-a-project-item"></a>Ajouter un attribut à un élément de projet
Les méthodes <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> obtenir et définir la valeur des attributs d’un élément de projet. SetItemAttribute crée l’attribut si elle n’existe pas déjà, ajoutez-la aux métadonnées d’élément de projet.

## <a name="add-an-attribute-to-a-project-item"></a>Ajouter un attribut à un élément de projet

- Le code suivant utilise la <xref:EnvDTE.DTE> objet automation et la <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> méthode pour ajouter un attribut à un élément de projet. L’ID d’élément de projet est obtenu à partir du nom d’élément projet « program.cs ». L’attribut « MyAttribute » est ajouté à cet élément de projet et la valeur « MyValue ».

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
