---
title: "The user options settings file for this project is missing the &#39;section&#39; section | Microsoft Docs"
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
  - "vs.tasklisterror.peruserfile_sectionerr"
ms.assetid: 576070f5-76b6-46e4-8aba-83442521027f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The user options settings file for this project is missing the &#39;section&#39; section
Le nœud Build ne figure pas dans le fichier .vbproj.user ou .csproj.user.  
  
 La section Build contient les paramètres de débogage.  Si cette section est manquante, vos paramètres de débogage ne seront pas chargés et les valeurs par défaut seront adoptées.  
  
 La cause la plus probable de cette situation est la modification manuelle du fichier projet.  
  
 Le système de projet réécrira automatiquement le fichier projet pour chaque utilisateur à la fermeture du projet.  
  
 Il s'agit d'un avertissement d'informations.  
  
## Voir aussi  
 [Fichiers projet](/visual-cpp/ide/project-files)   
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/fr-fr/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)