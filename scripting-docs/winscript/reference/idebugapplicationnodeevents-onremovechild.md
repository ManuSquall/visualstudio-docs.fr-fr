---
title: 'IDebugApplicationNodeEvents :: onRemoveChild | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNodeEvents.onRemoveChild
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugApplicationNodeEvents::onRemoveChild
ms.assetid: 2e025d29-b8c0-4793-a2d3-c20d548d6386
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0ff7b28f14c26029d64197ba919cc97c90a856c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574670"
---
# <a name="idebugapplicationnodeeventsonremovechild"></a>IDebugApplicationNodeEvents::onRemoveChild
Gère l’événement lorsqu’un nœud enfant est supprimé d’un objet de nœud d’application de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT onRemoveChild(  
   IDebugApplicationNode*  prddpChild  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `prddpChild`  
 dans Nœud d’application enfant qui a été supprimé.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode gère l’événement lorsqu’un nœud enfant est supprimé d’un objet de nœud d’application de débogage.  
  
 Les implémenteurs de l’interface `IDebugApplicationNode` déclenchent cet événement.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IDebugApplicationNodeEvents](../../winscript/reference/idebugapplicationnodeevents-interface.md)  
 [IDebugApplicationNodeEvents :: onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)    
 [Interface IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)