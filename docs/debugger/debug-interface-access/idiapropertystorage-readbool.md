---
title: IDiaPropertyStorage::ReadBOOL | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaPropertyStorage::ReadBOOL
ms.assetid: ad1822db-4572-48f7-9919-f8137f6701f2
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9632ada4b3e19013f05006d22770c08e83eac5ba
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiapropertystoragereadbool"></a>IDiaPropertyStorage::ReadBOOL
Lit `BOOL` valeurs dans un jeu de propriétés.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT ReadBOOL (   
   PROPID id,  
   BOOL*  pValue  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `id`  
 [in] Identificateur de la propriété à lire (`PROPID` est défini dans WTypes.h comme un `ULONG`).  
  
 `pValue`  
 [out] Retourne la valeur de propriété.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Retourne `E_INVALIDARG` si la propriété n’est pas de type `BOOL`.  
  
## <a name="remarks"></a>Remarques  
 Pour obtenir des résultats cohérents, interpréter la `BOOL` valeur afin que les valeurs différentes de zéro sont `TRUE` et zéro est `FALSE`.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)