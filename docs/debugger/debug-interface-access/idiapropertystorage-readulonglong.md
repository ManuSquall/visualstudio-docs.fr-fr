---
title: IDiaPropertyStorage::ReadULONGLONG | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadULONGLONG
ms.assetid: f80a2e24-5744-4fec-bab0-3ed51aef6e58
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5dea61b14cdee1ac260e4a21db0056abbdcad74f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54977380"
---
# <a name="idiapropertystoragereadulonglong"></a>IDiaPropertyStorage::ReadULONGLONG
Lit `ULONGLONG` valeurs dans un jeu de propriétés.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT ReadULONGLONG (   
   PROPID     id,  
   ULONGLONG* pValue  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `id`  
 [in] Identificateur de la propriété à lire (`PROPID` est défini dans WTypes.h comme un `ULONG`).  
  
 `pValue`  
 [out] Retourne la valeur de propriété.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Retourne `E_INVALIDARG` si la propriété n’est pas de type `ULONGLONG`.  
  
## <a name="remarks"></a>Notes  
 Un `ULONGLONG` est défini par Windows comme un entier non signé 64 bits.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)