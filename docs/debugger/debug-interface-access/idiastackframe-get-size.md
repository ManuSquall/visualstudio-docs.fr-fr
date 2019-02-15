---
title: IDiaStackFrame::get_size | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_size method
ms.assetid: 71e2f5ab-4aa8-4922-aa8a-b7db97ee143c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 71fbcc3e47b0748c46f7094e1c512289253ab8fe
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54916597"
---
# <a name="idiastackframegetsize"></a>IDiaStackFrame::get_size
Récupère la taille du frame de pile en octets.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_size (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne la taille du frame de pile en octets.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si la propriété n’est pas pris en charge. Sinon, retourne un code d'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)