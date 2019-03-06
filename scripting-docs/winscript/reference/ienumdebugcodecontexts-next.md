---
title: IEnumDebugCodeContexts::Next | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugCodeContexts.Next
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugCodeContexts::Next
ms.assetid: 844cc353-ae0b-45e1-84a6-32b0bb67f57f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 113f5a25a4bae4279281bbfdcfacce9efee3f2b6
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097238"
---
# <a name="ienumdebugcodecontextsnext"></a>IEnumDebugCodeContexts::Next
Récupère un nombre spécifié de segments dans la séquence d’énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Next(  
   ULONG                celt,  
   IDebugCodeContext**  pscc,  
   ULONG*               pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `celt`  
 [in] Le nombre de segments à récupérer.  
  
 `pscc`  
 [out] Retourne un tableau de `IDebugCodeContext` interfaces qui représente les segments en cours de récupération.  
  
 `pceltFetched`  
 [out] Le nombre réel de segments extraites par l’énumérateur.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode récupère un nombre spécifié de segments dans la séquence d’énumération.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IEnumDebugCodeContexts](../../winscript/reference/ienumdebugcodecontexts-interface.md)