---
title: IDiaPropertyStorage::ReadBSTR | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaPropertyStorage::ReadBSTR
ms.assetid: 7214643b-3286-48ed-90aa-0fe95b4cae5b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93ab7271ccef1819e16e4cdb4c690f82bfaeec35
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiapropertystoragereadbstr"></a>IDiaPropertyStorage::ReadBSTR
Lit `BSTR` valeurs dans un jeu de propriétés.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT ReadBSTR (   
   PROPID id,  
   BSTR*  pValue  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `id`  
 [in] Identificateur de la propriété à lire (`PROPID` est défini dans WTypes.h comme un `ULONG`).  
  
 `pValue`  
 [out] Retourne la valeur de propriété.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Retourne `E_INVALIDARG` si la propriété n’est pas de type `BSTR`.  
  
## <a name="remarks"></a>Remarques  
 A `BSTR` est défini par Windows en tant qu’une chaîne de caractères de large terminant par zéro.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)