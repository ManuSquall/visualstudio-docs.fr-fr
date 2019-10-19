---
title: 'IMachineDebugManagerEvents :: onRemoveApplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManagerEvents.onRemoveApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManagerEvents::onRemoveApplication
ms.assetid: 3ba71bd8-fd69-4a41-99c6-c736c416f227
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b50d91a75a8f251ad04b456b179fdd0ba0d1dc32
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571478"
---
# <a name="imachinedebugmanagereventsonremoveapplication"></a>IMachineDebugManagerEvents::onRemoveApplication
Gère l’événement lorsqu’une application est supprimée de la liste des applications en cours d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT onRemoveApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD                     dwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pda`  
 dans Application qui a été supprimée de la liste des applications en cours d’exécution.  
  
 `dwAppCookie`  
 dans Cookie fourni lorsque l’application a été ajoutée à partir de la liste des applications.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode indique qu’une application a été supprimée de la liste des applications en cours d’exécution.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IMachineDebugManagerEvents](../../winscript/reference/imachinedebugmanagerevents-interface.md)  
 [IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)