---
title: IDiaStackFrame::get_maxStack | Microsoft Docs
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
- C++
helpviewer_keywords:
- IDiaStackFrame::get_maxStack method
ms.assetid: 6352e972-7105-4d0e-aeba-b8fc16d62dec
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6ee403138139003bb33c12eef85e51afab0e3ef5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49948237"
---
# <a name="idiastackframegetmaxstack"></a>IDiaStackFrame::get_maxStack
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère le nombre maximal d’octets ajoutée à la pile dans le frame.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_maxStack (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne le nombre maximal d’octets est ajouté à la pile.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si la propriété n’est pas pris en charge. Sinon, retourne un code d'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)



