---
title: "Ajout d&#39;un attribut &#224; un &#233;l&#233;ment de projet | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "attributs (Visual Studio), ajouter à un élément de projet"
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# Ajout d&#39;un attribut &#224; un &#233;l&#233;ment de projet
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L' <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> et de méthodes get d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> et affectez la valeur des attributs d'un élément de projet.  SetItemAttribute crée l'attribut s'il n'existe pas déjà, l'ajoutant aux métadonnées d'élément de projet.  
  
## ajouter un attribut à un élément de projet  
  
#### pour ajouter un attribut à un élément de projet  
  
-   Le code suivant utilise l'objet Automation <xref:EnvDTE.DTE> et la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> pour ajouter un attribut à un élément de projet.  L'ID d'élément de projet est obtenu à partir de le nom « program.cs » d'élément de projet.  l'attribut « MyAttribute » est ajouté à cet élément de projet et donné la valeur « MyValue ».  
  
    ```  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
    EnvDTE.Project project = dte.Solution.Projects.Item(1);  
  
    string uniqueName = project.UniqueName;  
    IVsSolution solution =     (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
    IVsHierarchy hierarchy;  
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        uint itemId;  
        string fullPath =         (string)project.ProjectItems.Item("Program.cs").Properties.Item("FullPath").Value;  
        hierarchy.ParseCanonicalName(fullPath, out itemId);  
        buildPropertyStorage.SetItemAttribute(  
            itemId, "MyAttribute", "MyValue");  
    }  
  
    ```  
  
## Voir aussi  
 [Données persistantes dans le fichier projet MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)