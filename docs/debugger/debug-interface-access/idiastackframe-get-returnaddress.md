---
title: IDiaStackFrame::get_returnAddress | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaStackFrame::get_returnAddress method
ms.assetid: 0df91981-919f-48ed-9c70-4121567d645b
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c97a5dbc0ff85f538092f0bcf56c212010c4febe
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiastackframegetreturnaddress"></a>IDiaStackFrame::get_returnAddress
Récupère l’adresse de retour de l’image.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_returnAddress (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne l’adresse de retour de l’image.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si la propriété n’est pas pris en charge. Sinon, retourne un code d'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)