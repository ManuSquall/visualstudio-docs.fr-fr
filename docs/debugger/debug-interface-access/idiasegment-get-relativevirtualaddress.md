---
title: IDiaSegment::get_relativeVirtualAddress | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSegment::get_relativeVirtualAddress method
ms.assetid: b6a573a1-3671-4c1c-a5c2-2ab8f07fd510
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7fbb9d2562945bbbce0eea602ffdc1737e8c47c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasegmentgetrelativevirtualaddress"></a>IDiaSegment::get_relativeVirtualAddress
Récupère l’adresse virtuelle relative (RVA) du début de la section.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_relativeVirtualAddress (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne l’adresse RVA du début de la section.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas pris en charge. Sinon, retourne un code d'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)