---
title: Où puis-je trouver les codes des erreurs Win32 ? | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ecddd2a8ca87d4c86b3cdf776fcf2e475efb8836
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056922"
---
# <a name="where-can-i-look-up-win32-error-codes"></a>Où puis-je trouver les codes des erreurs Win32 ?
WINERROR.H, dans le répertoire INCLUDE de votre installation de système par défaut, contient les définitions des codes d'erreur correspondant aux fonctions API Win32.  
  
 Vous pouvez rechercher un code d’erreur en tapant le code dans le **espion** fenêtre ou le **Espion express** boîte de dialogue. Exemple :  
  
`0x80000004,hr` 

  
## <a name="see-also"></a>Voir aussi  
 [Forum aux questions de débogage du Code natif](../debugger/debugging-native-code-faqs.md)   
 [Débogage du code natif](../debugger/debugging-native-code.md)