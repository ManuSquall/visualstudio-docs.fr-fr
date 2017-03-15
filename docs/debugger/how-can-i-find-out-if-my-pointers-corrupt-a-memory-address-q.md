---
title: "Comment puis-je savoir si mes pointeurs endommagent une adresse m&#233;moire&#160;? | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "adresses, pointeurs qui endommagent l'adresse mémoire"
  - "adresse mémoire endommagée"
  - "déboguer (C++), altération de la mémoire"
  - "adresse mémoire endommagée par des pointeurs"
  - "mémoire, altération"
  - "pointeurs, endommager les adresses mémoire"
ms.assetid: a147c939-4fb1-415c-8410-cf303781e9e8
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Comment puis-je savoir si mes pointeurs endommagent une adresse m&#233;moire&#160;?
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## Description du problème  
 Je pense que l'un de mes pointeurs endommage la mémoire à l'adresse 0x00408000.  Comment puis\-je savoir ce qui se passe à cet endroit ?  
  
## Solution  
  
#### Vérifier l'altération du tas  
  
-   La plus grande partie de l'altération de la mémoire est provoquée par l'altération du tas.  Servez\-vous de l'utilitaire Global Flags \(gflags.exe\) ou de pageheap.exe.  Consultez [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;286470](http://support.microsoft.com/default.aspx?scid=kb;en-us;286470).  
  
#### Pour rechercher la modification de l'adresse mémoire :  
  
1.  Définissez un point d'arrêt sur variable à l'adresse 0x00408000.  Voir la rubrique sur la [définition d'un point d'arrêt de modification de données \(natif C\+\+ uniquement\)](../debugger/using-breakpoints.md#BKMK_Set_a_data_change_breakpoint__native_C___only_).  
  
2.  Lorsque vous atteignez le point d'arrêt, utilisez la fenêtre **Mémoire** pour afficher le contenu de la mémoire à partir de l'adresse 0x00408000.  Pour plus d'informations, consultez [Fenêtres Mémoire](../debugger/memory-windows.md).  
  
## Voir aussi  
 [Forum Aux Questions sur le débogage du code natif](../debugger/debugging-native-code-faqs.md)   
 [Débogage du code natif](../debugger/debugging-native-code.md)