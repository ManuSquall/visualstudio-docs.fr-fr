---
title: IDebugApplicationNode::Attach | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNode.Attach
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationNode::Attach
ms.assetid: f4aad4ae-5bb0-4b5e-8f70-912a677f8f7a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 393186330979d464fe54bde339806a5d8335a859
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725929"
---
# <a name="idebugapplicationnodeattach"></a>IDebugApplicationNode::Attach
Ajoute ce nœud de l’application à l’arborescence du projet spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Attach(  
   IDebugApplicationNode*  pdanParent  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pdanParent`  
 [in] L’arborescence du projet où ce nœud de l’application doit être ajouté.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode ajoute ce nœud de l’application au projet d’une arborescence, à l’aide de `pdanParent` comme parent. Si `pdanParent` est `NULL`, ce nœud de l’application sera le nœud de niveau supérieur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)   
 [Interface IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)