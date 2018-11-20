---
title: Comment puis-je savoir si mes pointeurs endommagent une adresse mémoire ? | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- addresses, pointers corrupting memory address
- memory, corruption
- pointers, corrupting memory addresses
- memory address corruption by pointers
- debugging [C++], memory corruption
- corrupted memory address
ms.assetid: a147c939-4fb1-415c-8410-cf303781e9e8
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 013b88bcaa0d0cf9dc8ff308f43f3191ed2d0334
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734233"
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>Comment puis-je savoir si mes pointeurs endommagent une adresse mémoire ?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Description du problème  
 Je pense que l'un de mes pointeurs endommage la mémoire à l'adresse 0x00408000. Comment puis-je savoir ce qui se passe à cet endroit ?  
  
## <a name="solution"></a>Solution  
  
#### <a name="check-for-heap-corruption"></a>Vérifier l'altération du tas  
  
-   La plus grande partie de l'altération de la mémoire est provoquée par l'altération du tas. Servez-vous de l'utilitaire Global Flags (gflags.exe) ou de pageheap.exe. Consultez [ http://support.microsoft.com/default.aspx?scid=kb; en-us ; 286470](http://support.microsoft.com/default.aspx?scid=kb;en-us;286470).  
  
#### <a name="to-find-where-the-memory-address-is-modified"></a>Pour rechercher la modification de l'adresse mémoire :  
  
1.  Définissez un point d'arrêt sur variable à l'adresse 0x00408000. Consultez [définir un point d’arrêt de modification de données (natif C++ uniquement)](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus_only).  
  
2.  Lorsque vous atteignez le point d’arrêt, utilisez la **mémoire** contenu de la fenêtre pour afficher la mémoire en commençant à 0 x 00408000. Pour plus d’informations, consultez [mémoire Windows](../debugger/memory-windows.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Forum aux questions de débogage du Code natif](../debugger/debugging-native-code-faqs.md)   
 [Débogage du code natif](../debugger/debugging-native-code.md)



