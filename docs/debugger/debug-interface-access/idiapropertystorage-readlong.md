---
title: IDiaPropertyStorage::ReadLONG | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaPropertyStorage::ReadLONG
ms.assetid: 32054cbc-db55-4513-a1b4-de80e77aac8a
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aba26ae4e2495d8c0a4feb1ff692d90a228e8292
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiapropertystoragereadlong"></a>IDiaPropertyStorage::ReadLONG
Lit `LONG` valeurs dans un jeu de propriétés.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT ReadDLONG (   
   PROPID id,  
   LONG*  pValue  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `id`  
 [in] Identificateur de la propriété à lire (`PROPID` est défini dans WTypes.h comme un `ULONG`).  
  
 `pValue`  
 [out] Retourne la valeur de propriété.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Retourne `E_INVALIDARG` si la propriété n’est pas de type `LONG`.  
  
## <a name="remarks"></a>Remarques  
 A `LONG` est défini par Windows comme un entier signé 32 bits.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)