---
title: 'IDebugApplicationNode :: GetParent | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNode.GetParent
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationNode::GetParent
ms.assetid: 88ba3a53-0cd7-4e1f-8558-79c20ac76cc9
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c887e61652da8780012d98354f028f3e5cb005c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574771"
---
# <a name="idebugapplicationnodegetparent"></a>IDebugApplicationNode::GetParent
Retourne le nœud parent de ce nœud d’application.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetParent(  
   IDebugApplicationNode**  pprddp  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pprddp`  
 à Nœud d’application parente de ce nœud d’application.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne le nœud parent de ce nœud d’application.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)