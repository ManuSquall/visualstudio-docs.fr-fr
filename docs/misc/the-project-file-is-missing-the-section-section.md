---
title: "The project file is missing the &#39;section&#39; section | Microsoft Docs"
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
  - "vs.tasklisterror.projfile_sectionerr"
ms.assetid: 516ab410-1b73-4539-9654-6323af6135b2
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The project file is missing the &#39;section&#39; section
Le fichier .vbproj ou .csproj est endommagé.  L'une des sections ci\-dessous est manquante :  
  
-   Générer  
  
-   Fichiers  
  
-   VisualStudio  
  
-   VisualBasic ou CSHARP.  
  
 Si la section VisualStudio, VisualBasic ou CSHARP est manquante, le projet ne sera pas chargé.  Si la section Build ou Files est manquante, le fichier projet sera chargé comme suit :  
  
-   Si la section Build est manquante, tous les paramètres de génération et les informations de configuration seront perdus.  
  
-   Si la section Files est manquante, le projet ne contiendra pas de fichier.  
  
 **Pour corriger cette erreur**  
  
-   Recréez votre projet.  
  
## Voir aussi  
 [Fichiers projet](/visual-cpp/ide/project-files)   
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/fr-fr/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)