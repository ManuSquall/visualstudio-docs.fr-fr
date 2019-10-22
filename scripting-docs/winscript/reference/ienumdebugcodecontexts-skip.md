---
title: 'IEnumDebugCodeContexts :: Skip | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugCodeContexts.Skip
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugCodeContexts::Skip
ms.assetid: ba917f57-f7a9-419f-96d6-8f4378b12c57
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a16343b24a640341009758345b17f86e94b7b2ed
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577202"
---
# <a name="ienumdebugcodecontextsskip"></a>IEnumDebugCodeContexts::Skip
Ignore un nombre spécifié de segments dans une séquence d’énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Skip(  
   ULONG  celt  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `celt`  
 dans Nombre de segments dans la séquence d’énumération à ignorer.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode ignore un nombre spécifié de segments dans une séquence d’énumération.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IEnumDebugCodeContexts](../../winscript/reference/ienumdebugcodecontexts-interface.md)