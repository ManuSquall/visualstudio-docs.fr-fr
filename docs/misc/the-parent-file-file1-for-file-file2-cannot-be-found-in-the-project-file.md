---
title: "The parent file, &#39;file1&#39;, for file &#39;file2&#39; cannot be found in the project file | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.projfile_missing_dependency"
ms.assetid: 1902c0b5-d09d-49b9-8f71-e325f7b9cfd7
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The parent file, &#39;file1&#39;, for file &#39;file2&#39; cannot be found in the project file
Le système de projet ne peut pas trouver un nœud correspondant à un fichier.  
  
 Les fichiers dépendants sont rendus persistants dans le fichier projet en ajoutant un attribut `DependentUpon` au nœud `<File>`.  Par exemple :  
  
```  
<File  
    RelPath = "Form1.resx"  
    SubType = "Code"  
    BuildAction = "EmbeddedResource"  
    DependentUpon="Form1.vb"  
/>  
```  
  
 Cela fait apparaître le fichier Form1.resx sous Form1.vb dans la hiérarchie du projet.  
  
 La cause la plus probable de cette erreur est la modification manuelle du fichier projet.  
  
### Pour corriger cette erreur  
  
-   Modifiez et mettez à jour le fichier projet.  
  
     Les fichiers affectés seront ajoutés au projet ; cependant, la dépendance ne sera pas préservée.  
  
## Voir aussi  
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/fr-fr/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)