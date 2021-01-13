---
title: Où puis-je trouver les codes des erreurs Win32 ? | Microsoft Docs
description: Pour rechercher un code d’erreur Win32, entrez-le dans Watch ou espion Express. Par exemple, « 0x80000004, HR ». Les définitions des codes d’erreur se trouvent dans INCLUDE\WINERROR.H.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 44a006be3b6ecad3ef723c00154354cb35df0049
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149285"
---
# <a name="where-can-i-look-up-win32-error-codes"></a>Où puis-je trouver les codes des erreurs Win32 ?
WINERROR.H, dans le répertoire INCLUDE de votre installation de système par défaut, contient les définitions des codes d'erreur correspondant aux fonctions API Win32.

 Vous pouvez rechercher un code d’erreur en tapant ce code dans la fenêtre **Espion** ou dans la boîte de dialogue **Espion express**. Par exemple :

`0x80000004,hr`

## <a name="see-also"></a>Voir aussi
- [FAQ sur le débogage du code natif](../debugger/debugging-native-code-faqs.md)
- [Débogage du code natif](../debugger/debugging-native-code.md)