---
title: "Aucune source disponible | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.nosource"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Il n'y a pas de code source disponible pour l'emplacement en cours (boîte de dialogue)"
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Aucune source disponible
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Votre projet ne contient pas de code source pour le code que vous essayez d'afficher.  La cause habituelle est le double\-clic sur un module qui n'a pas de code source dans la **fenêtre Pile des appels** ou la **Fenêtre Threads**.  Vous pouvez poursuivre le débogage, mais vous ne pouvez pas utiliser la fenêtre source pour définir les points d'arrêt et accomplir d'autres actions à cet emplacement.  Si vous avez besoin de définir un point d'arrêt, utilisez plutôt la **fenêtre Code Machine**.  
  
 Dans les pages de propriétés de la solution, vous pouvez changer les répertoires dans lesquels le débogueur recherche des fichiers sources et demander au débogueur d'ignorer les fichiers sources sélectionnés.  Consultez [Fichiers sources pour le débogage, Propriétés communes, boîte de dialogue Pages de propriétés de Solution](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md).  
  
 **Parcourir pour rechercher du code source**  
 Cliquez sur ce lien pour ouvrir une boîte de dialogue où vous pouvez rechercher le code source.  
  
 **Afficher le code machine**  
 Lance la **Fenêtre Code Machine**.  
  
 **Toujours afficher le code machine pour les fichiers sources manquants**  
 Sélectionnez cette option pour afficher automatiquement la **Fenêtre Code Machine** lorsqu'aucune source n'est disponible.  Ce paramètre peut également être modifié dans la boîte de dialogue **Options**, catégorie **Débogage**, page **Général**, en activant ou en désactivant **Afficher le code machine si la source n'est pas disponible**.  
  
## Voir aussi  
 [Fichiers sources pour le débogage, Propriétés communes, boîte de dialogue Pages de propriétés de Solution](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)   
 [Spécifier les fichiers de symbole \(.pdb\) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [SOS.dll \(SOS Debugging Extension\)](../Topic/SOS.dll%20\(SOS%20Debugging%20Extension\).md)