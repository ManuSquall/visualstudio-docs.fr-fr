---
title: Déterminer si mes pointeurs endommagent une adresse mémoire | Microsoft Docs
description: Pour déterminer si votre pointeur endommage la mémoire, vous pouvez rechercher une altération du tas, et vous pouvez définir un point d’arrêt sur variable pour déterminer comment une valeur est modifiée.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: how-to
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d95e38c6393d6576f2867aad5d1224940f33cebc
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155198"
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>Comment puis-je savoir si mes pointeurs endommagent une adresse mémoire ?
## <a name="problem-description"></a>Description du problème
 Je pense que l'un de mes pointeurs endommage la mémoire à l'adresse 0x00408000. Comment puis-je savoir ce qui se passe à cet endroit ?

## <a name="solution"></a>Solution

#### <a name="check-for-heap-corruption"></a>Vérifier l'altération du tas

- La plus grande partie de l'altération de la mémoire est provoquée par l'altération du tas. Servez-vous de l'utilitaire Global Flags (gflags.exe) ou de pageheap.exe. Consultez [/Windows-Hardware/drivers/Debugger/Gflags-and-pageheap](/windows-hardware/drivers/debugger/gflags-and-pageheap).

#### <a name="to-find-where-the-memory-address-is-modified"></a>Pour rechercher la modification de l'adresse mémoire :

1. Définissez un point d'arrêt sur variable à l'adresse 0x00408000. Consultez [Définir un point d’arrêt de modification de données (C++ natif uniquement)](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus).

2. Quand vous atteignez le point d’arrêt, utilisez la fenêtre **Mémoire** pour afficher le contenu de la mémoire à partir de l’adresse 0x00408000. Pour plus d’informations, consultez [mémoire Windows](../debugger/memory-windows.md).

## <a name="see-also"></a>Voir aussi
- [FAQ sur le débogage du code natif](../debugger/debugging-native-code-faqs.md)
- [Débogage du code natif](../debugger/debugging-native-code.md)
