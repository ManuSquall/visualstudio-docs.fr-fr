---
title: IDebugApplicationNode::Attach | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: c41d06c116c7c15ad308ce2ace837ea01d90ab1d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155561"
---
# <a name="idebugapplicationnodeattach"></a>IDebugApplicationNode::Attach
Ajoute ce nœud de l’application à l’arborescence du projet spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Attach(  
   IDebugApplicationNode*  pdanParent  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pdanParent`  
 [in] L’arborescence du projet où ce nœud de l’application doit être ajoutée.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode ajoute ce nœud de l’application au projet une arborescence, à l’aide de `pdanParent` comme parent. Si `pdanParent` est `NULL`, ce nœud de l’application sera le nœud de niveau supérieur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)   
 [Interface IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)