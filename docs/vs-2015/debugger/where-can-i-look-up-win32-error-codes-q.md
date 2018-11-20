---
title: Où puis-je trouver les codes des erreurs Win32 ? | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vc.errors
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- error codes, Win32
- Win32, error codes
ms.assetid: 8fb4ff42-b8eb-4152-b49e-b802d194b05e
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0606463eafc5c681aacaef9fb4111f71260ecb7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51723734"
---
# <a name="where-can-i-look-up-win32-error-codes"></a>Où puis-je trouver les codes des erreurs Win32 ?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

WINERROR.H, dans le répertoire INCLUDE de votre installation de système par défaut, contient les définitions des codes d'erreur correspondant aux fonctions API Win32.  
  
 Vous pouvez rechercher un code d’erreur en tapant le code dans le **espion** fenêtre ou le **Espion express** boîte de dialogue. Exemple :  
  
```  
0x80000004,hr  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Forum aux questions de débogage du Code natif](../debugger/debugging-native-code-faqs.md)   
 [Débogage du code natif](../debugger/debugging-native-code.md)



