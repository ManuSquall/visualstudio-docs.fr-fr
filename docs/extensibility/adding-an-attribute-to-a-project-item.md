---
title: "Ajout d’un attribut à un élément de projet | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fce6b9770703afda8e8c1af6e17c10287625f647
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="adding-an-attribute-to-a-project-item"></a>Ajout d’un attribut à un élément de projet
Les méthodes <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> obtenir et définir la valeur des attributs d’un élément de projet. SetItemAttribute crée l’attribut si elle n’existe pas, ajoutez-le à la métadonnée d’élément de projet.  
  
## <a name="adding-an-attribute-to-a-project-item"></a>Ajout d’un attribut à un élément de projet  
  
#### <a name="to-add-an-attribute-to-a-project-item"></a>Pour ajouter un attribut à un élément de projet  
  
-   Le code suivant utilise la <xref:EnvDTE.DTE> objet automation et le <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> méthode pour ajouter un attribut à un élément de projet. L’ID d’élément de projet est obtenu à partir du projet élément nom « program.cs ». L’attribut « MyAttribute » est ajoutée à cet élément de projet et la valeur « MyValue ».  
  
    ```  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
    EnvDTE.Project project = dte.Solution.Projects.Item(1);  
  
    string uniqueName = project.UniqueName;  
    IVsSolution solution =     (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
    IVsHierarchy hierarchy;  
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        uint itemId;  
        string fullPath =         (string)project.ProjectItems.Item("Program.cs").Properties.Item("FullPath").Value;  
        hierarchy.ParseCanonicalName(fullPath, out itemId);  
        buildPropertyStorage.SetItemAttribute(  
            itemId, "MyAttribute", "MyValue");  
    }  
  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Données persistantes dans le fichier projet MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)