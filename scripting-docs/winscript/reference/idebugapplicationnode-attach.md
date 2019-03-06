---
title: IDebugApplicationNode::Attach | Microsoft Docs
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
ms.openlocfilehash: 49df95e2c5298fc9bb7025982e75a90548d9613f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094950"
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