---
title: 'IDebugApplicationNodeEvents :: onDetach | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNodeEvents.onDetach
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugApplicationNodeEvents::onDetach
ms.assetid: ef0cbe40-8c52-4bc9-bed0-9fc508abec6e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb1a33cbec8ef032c1c4fedba28ad4013e676f0d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574679"
---
# <a name="idebugapplicationnodeeventsondetach"></a>IDebugApplicationNodeEvents::onDetach
Gère un événement qui signifie que l’objet de nœud d’application de débogage a été détaché d’un nœud parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT onDetach();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode n’accepte aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode gère un événement qui signifie que l’objet de nœud d’application de débogage a été détaché d’un nœud parent.  
  
 Les implémenteurs de l’interface `IDebugApplicationNode` déclenchent cet événement.  
  
## <a name="see-also"></a>Voir aussi  
   de l' [interface IDebugApplicationNodeEvents](../../winscript/reference/idebugapplicationnodeevents-interface.md)  
 [IDebugApplicationNodeEvents::onAttach](../../winscript/reference/idebugapplicationnodeevents-onattach.md)   
 [Interface IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)