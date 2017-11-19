---
title: IDebugApplicationNode::EnumChildren | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplicationNode.EnumChildren
apilocation: pdm.dll
helpviewer_keywords: IDebugApplicationNode::EnumChildren
ms.assetid: d79b362b-23d5-4a5e-a214-5a78618eaf71
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a8ab13f3a284b1b36550367e68ca5fe600db3be6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnodeenumchildren"></a>IDebugApplicationNode::EnumChildren
Énumère les nœuds enfants de ce nœud de l’application.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumChildren(  
   IEnumDebugApplicationNodes**  pperddp  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pperddp`  
 [out] L’énumération des nœuds d’enfants de ce nœud.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode énumère les nœuds enfants de ce nœud de l’application.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)