---
title: DebugBreak et __debugbreak | Microsoft Docs
description: Découvrez comment utiliser la fonction DebugBreak et le __debugbreak intrinsèques pour provoquer l’arrêt de votre programme, tout comme si un point d’arrêt était défini.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DebugBreak
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], DebugBreak function
- DebugBreak function
- breakpoints, DebugBreak function
ms.assetid: 9787c795-df94-4f48-bc8d-3bf899b67421
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f4fb03cf4d45e367f0d7a99dbe26705475652651
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873143"
---
# <a name="debugbreak-and-__debugbreak"></a>DebugBreak et __debugbreak
Vous pouvez appeler la fonction Win32 [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) ou le [__debugbreak](/cpp/intrinsics/debugbreak) intrinsèque à n’importe quel point de votre code. `DebugBreak` et `__debugbreak` reviennent à définir un point d'arrêt à cet emplacement.

 Étant donné que `DebugBreak` est un appel à une fonction système, les symboles de débogage de système doivent être installés pour vérifier que les informations de pile des appels correctes sont affichées après l’arrêt. À défaut, les informations de la pile des appels affichées par le débogueur peuvent être décalées d'un frame. Si vous utilisez `__debugbreak`, les symboles ne sont pas requis.

## <a name="see-also"></a>Voir aussi
- [Intrinsèques du compilateur](/cpp/intrinsics/compiler-intrinsics)
- [Sécurité du débogueur](../debugger/debugger-security.md)
- [Débogage du code natif](../debugger/debugging-native-code.md)
- [Spécifier les fichiers de symboles (.pdb) et les fichiers source](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
