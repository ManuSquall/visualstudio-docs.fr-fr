---
title: 'IDebugApplicationNode :: Attach | Microsoft Docs'
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
ms.openlocfilehash: 30d4e189ec878def1cfd88517654955cd2d1aa12
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574787"
---
# <a name="idebugapplicationnodeattach"></a>IDebugApplicationNode::Attach
Ajoute ce nœud d’application à l’arborescence de projet spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Attach(  
   IDebugApplicationNode*  pdanParent  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pdanParent`  
 dans Arborescence de projet dans laquelle ce nœud d’application doit être ajouté.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode ajoute ce nœud d’application à l’arborescence de projet, à l’aide de `pdanParent` en tant que parent. Si `pdanParent` est `NULL`, ce nœud d’application sera le nœud de niveau supérieur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugApplicationNode ::D etach](../../winscript/reference/idebugapplicationnode-detach.md)    
 [Interface IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)