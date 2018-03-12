---
title: "Comment puis-je savoir si mes pointeurs endommagent une adresse mémoire ? | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- addresses, pointers corrupting memory address
- memory, corruption
- pointers, corrupting memory addresses
- memory address corruption by pointers
- debugging [C++], memory corruption
- corrupted memory address
ms.assetid: a147c939-4fb1-415c-8410-cf303781e9e8
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a57b36fc1d1dd25f439f65fe9d72cec6aab63471
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>Comment puis-je savoir si mes pointeurs endommagent une adresse mémoire ?
## <a name="problem-description"></a>Description du problème  
 Je pense que l'un de mes pointeurs endommage la mémoire à l'adresse 0x00408000. Comment puis-je savoir ce qui se passe à cet endroit ?  
  
## <a name="solution"></a>Solution  
  
#### <a name="check-for-heap-corruption"></a>Vérifier l'altération du tas  
  
-   La plus grande partie de l'altération de la mémoire est provoquée par l'altération du tas. Servez-vous de l'utilitaire Global Flags (gflags.exe) ou de pageheap.exe. Consultez [http://support.microsoft.com/default.aspx?scid=kb;en-us;286470](http://support.microsoft.com/default.aspx?scid=kb;en-us;286470).  
  
#### <a name="to-find-where-the-memory-address-is-modified"></a>Pour rechercher la modification de l'adresse mémoire :  
  
1.  Définissez un point d'arrêt sur variable à l'adresse 0x00408000. Consultez [définir un point d’arrêt de modification de données (C++ natif uniquement)](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus_only).  
  
2.  Lorsque vous atteignez le point d’arrêt, utilisez la **mémoire** contenu de la fenêtre pour afficher la mémoire en commençant à l’adresse 0 x 00408000. Pour plus d’informations, consultez [mémoire Windows](../debugger/memory-windows.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Foire aux questions de débogage du Code natif](../debugger/debugging-native-code-faqs.md)   
 [Débogage du code natif](../debugger/debugging-native-code.md)