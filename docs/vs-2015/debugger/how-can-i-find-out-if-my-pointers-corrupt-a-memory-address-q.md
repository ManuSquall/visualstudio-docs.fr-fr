---
title: Comment puis-je savoir si mes pointeurs endommagent une adresse mémoire ? | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 8da16e806b8c4bb9bb29251184a5a45c566e9f25
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58954127"
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>Comment puis-je savoir si mes pointeurs endommagent une adresse mémoire ?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Description du problème  
 Je pense que l'un de mes pointeurs endommage la mémoire à l'adresse 0x00408000. Comment puis-je savoir ce qui se passe à cet endroit ?  
  
## <a name="solution"></a>Solution  
  
#### <a name="check-for-heap-corruption"></a>Vérifier l'altération du tas  
  
-   La plus grande partie de l'altération de la mémoire est provoquée par l'altération du tas. Servez-vous de l'utilitaire Global Flags (gflags.exe) ou de pageheap.exe. Consultez [ http://support.microsoft.com/default.aspx?scid=kb; en-us ; 286470](http://support.microsoft.com/default.aspx?scid=kb;en-us;286470).  
  
#### <a name="to-find-where-the-memory-address-is-modified"></a>Pour rechercher la modification de l'adresse mémoire :  
  
1.  Définissez un point d'arrêt sur variable à l'adresse 0x00408000. Consultez [Définir un point d’arrêt de modification de données (C++ natif uniquement)](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus_only).  
  
2.  Quand vous atteignez le point d’arrêt, utilisez la fenêtre **Mémoire** pour afficher le contenu de la mémoire à partir de l’adresse 0x00408000. Pour plus d’informations, consultez [mémoire Windows](../debugger/memory-windows.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Questions fréquentes (FAQ) sur le débogage du code natif](../debugger/debugging-native-code-faqs.md)   
 [Débogage du code natif](../debugger/debugging-native-code.md)
