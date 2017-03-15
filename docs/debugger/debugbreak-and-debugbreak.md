---
title: "DebugBreak et __debugbreak | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DebugBreak"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "points d'arrêt, DebugBreak (fonction)"
  - "DebugBreak (fonction)"
  - "déboguer (C++), DebugBreak (fonction)"
ms.assetid: 9787c795-df94-4f48-bc8d-3bf899b67421
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# DebugBreak et __debugbreak
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez appeler la fonction Win32 DebugBreak ou l'objet intrinsèque [\_\_debugbreak](/visual-cpp/intrinsics/debugbreak) à n'importe quel endroit de votre code.  `DebugBreak` et `__debugbreak` reviennent à définir un point d'arrêt à cet emplacement.  
  
 Étant donné que `DebugBreak` est un appel à une fonction système, les symboles de débogage de système doivent être installés pour vérifier que les informations de pile des appels correctes sont affichées après l'arrêt.  À défaut, les informations de la pile des appels affichées par le débogueur peuvent être décalées d'un frame.  Si vous utilisez `__debugbreak`, les symboles ne sont pas requis.  
  
## Voir aussi  
 [compilateur, intrinsèques](/visual-cpp/intrinsics/compiler-intrinsics)   
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Débogage du code natif](../debugger/debugging-native-code.md)   
 [Spécifier les fichiers de symbole \(.pdb\) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)