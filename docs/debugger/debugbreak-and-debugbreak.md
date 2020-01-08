---
title: DebugBreak et __debugbreak | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 097405f98d1a80b8605b6773bdc675ff2c4ab773
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75404657"
---
# <a name="debugbreak-and-__debugbreak"></a>DebugBreak et __debugbreak
Vous pouvez appeler la fonction Win32 [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) ou le [__debugbreak](/cpp/intrinsics/debugbreak) intrinsèque à n’importe quel point de votre code. `DebugBreak` et `__debugbreak` reviennent à définir un point d'arrêt à cet emplacement.

 Étant donné que `DebugBreak` est un appel à une fonction système, les symboles de débogage de système doivent être installés pour vérifier que les informations de pile des appels correctes sont affichées après l’arrêt. À défaut, les informations de la pile des appels affichées par le débogueur peuvent être décalées d'un frame. Si vous utilisez `__debugbreak`, les symboles ne sont pas requis.

## <a name="see-also"></a>Voir aussi
- [compilateur, fonctions intrinsèques](/cpp/intrinsics/compiler-intrinsics)
- [Sécurité du débogueur](../debugger/debugger-security.md)
- [Débogage du code natif](../debugger/debugging-native-code.md)
- [Spécifier les fichiers de symbole (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
