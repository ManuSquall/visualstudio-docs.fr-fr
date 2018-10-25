---
title: IDiaPropertyStorage::ReadBOOL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBOOL
ms.assetid: ad1822db-4572-48f7-9919-f8137f6701f2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3df4ce44c0cf0b3b09442dc695f73c415035e84a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49904178"
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
  
## <a name="remarks"></a>Notes  
 Pour obtenir des résultats cohérents, interpréter les `BOOL` sorte que les valeurs différentes de zéro sont `TRUE` et zéro est `FALSE`.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)