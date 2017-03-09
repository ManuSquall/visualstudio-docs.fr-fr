---
title: "The folder &#39;folder&#39; could not be added to the project. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.projfile_no_add_folder"
ms.assetid: 3f6a5aa7-17cc-4e78-93b7-96e0970e111e
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The folder &#39;folder&#39; could not be added to the project. &lt;reason&gt;
Un dossier lu à partir du fichier .vbproj ou .csproj ne peut pas être ajouté au projet.  Cet échec peut être dû aux raisons ci\-dessous.  
  
-   Le nom n'est pas valide.  
  
-   Fichier dans un chemin d'accès,  par exemple, si vous avez un chemin d'accès relatif au projet Dossier1\\Dossier2\\Dossier3, mais qu'il existe également un fichier avec un chemin d'accès relatif Dossier1\\Dossier2.  
  
-   L'élément existe déjà.  Cela se produit lorsqu'un dossier est répertorié deux fois dans le fichier projet.  
  
 La cause la plus probable de cette erreur est la modification manuelle du fichier projet.  
  
 **Pour corriger cette erreur**  
  
-   Supprimez le nœud de dossier affecté du fichier projet.  
  
     Tout dossier, ainsi que tous les fichiers situés sous ce dossier, pour lequel ce diagnostic est affiché ne sera pas ajouté au projet.  
  
## Voir aussi  
 [Fichiers projet](/visual-cpp/ide/project-files)   
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/fr-fr/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)