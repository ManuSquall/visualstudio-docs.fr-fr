---
title: "At least one folder is missing the &#39;attribute&#39; attribute | Microsoft Docs"
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
  - "vs.tasklisterror.projfile_missing_fold_attrib"
ms.assetid: 3a0498a9-df61-47d8-a228-f88f4f138df8
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# At least one folder is missing the &#39;attribute&#39; attribute
Certains attributs nécessaires au système de projet sont manquants dans un nœud de dossier qui a été lu à partir du fichier .vbproj ou .csproj.  L'attribut **RelPath** constitue à l'heure actuelle le seul attribut de ce type, qui spécifie l'endroit où se trouve le dossier donné sous le dossier du projet.  
  
 La cause la plus probable de cette erreur est la modification manuelle du fichier projet.  
  
 **Pour corriger cette erreur**  
  
-   Supprimez le nœud de dossier affecté du fichier projet.  De plus, si le dossier se trouve toujours sur le disque, vous pouvez basculer en mode Afficher tous les fichiers \(en cliquant sur le bouton correspondant dans la barre d'outils de l'Explorateur de solutions\), cliquer avec le bouton droit sur le dossier affecté, puis sélectionner **Inclure dans le projet**.  
  
     Tout dossier pour lequel un attribut est manquant ne sera pas ajouté au projet.  
  
## Voir aussi  
 [Fichiers projet](/visual-cpp/ide/project-files)   
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/fr-fr/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)