---
title: "R&#233;soudre une ambigu&#239;t&#233;, bo&#238;te de dialogue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.Disambig"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Résoudre une ambiguïté (boîte de dialogue)"
  - "débogueur, boîte de dialogue Résoudre une ambiguïté"
  - "déboguer (C++), résolution d’ambiguïté"
ms.assetid: d9f47455-a116-4c84-8bad-2dfbf4d77f74
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# R&#233;soudre une ambigu&#239;t&#233;, bo&#238;te de dialogue
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La boîte de dialogue `Resolve Ambiguity` s'ouvre lorsque le débogueur ne parvient pas à choisir l'emplacement à afficher.  Par exemple, si vous utilisez les modèles C\+\+, vous pouvez créer plusieurs fonctions à partir d'un seul modèle de fonction.  Si le débogueur s'arrête à l'emplacement d'une source dans le modèle et si vous choisissez `Go To Disassembly`, le débogueur a plusieurs options.  Chaque fonction créée à partir du modèle possède son propre code machine et le débogueur ne sait pas celui que vous souhaitez afficher.  La boîte de dialogue `Resolve Ambiguity` vous permet de sélectionner l'emplacement de votre choix dans une liste de tous les emplacements correspondants.  
  
 `Choose the specific location`  
 Répertorie tous les emplacements correspondant à votre commande.  
  
 `Address`  
 Affiche les adresses mémoire de chaque fonction.  
  
 `Function`  
 Affiche le nom de chaque fonction.  
  
 `Module`  
 Affiche le module \(EXE ou DLL\) contenant le code objet de la fonction.  
  
## Voir aussi  
 [Expressions dans le débogueur](../debugger/expressions-in-the-debugger.md)