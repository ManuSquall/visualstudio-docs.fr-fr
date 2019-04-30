---
title: Où puis-je trouver les codes des erreurs Win32 ? | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vc.errors
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- error codes, Win32
- Win32, error codes
ms.assetid: 8fb4ff42-b8eb-4152-b49e-b802d194b05e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7299139d05a47c079e1aeb29f3b61433cff33bb6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62929186"
---
# <a name="where-can-i-look-up-win32-error-codes"></a>Où puis-je trouver les codes des erreurs Win32 ?
WINERROR.H, dans le répertoire INCLUDE de votre installation de système par défaut, contient les définitions des codes d'erreur correspondant aux fonctions API Win32.

 Vous pouvez rechercher un code d’erreur en tapant ce code dans la fenêtre **Espion** ou dans la boîte de dialogue **Espion express**. Exemple :

`0x80000004,hr`

## <a name="see-also"></a>Voir aussi
- [Forum Aux Questions sur le débogage du code natif](../debugger/debugging-native-code-faqs.md)
- [Débogage du code natif](../debugger/debugging-native-code.md)