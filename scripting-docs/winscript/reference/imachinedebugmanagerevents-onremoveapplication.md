---
title: IMachineDebugManagerEvents::onRemoveApplication | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: b4cc2412f88eb4a4224dc96ebc1b993729169071
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088944"
---
# <a name="imachinedebugmanagereventsonremoveapplication"></a>IMachineDebugManagerEvents::onRemoveApplication
Gère l’événement lorsqu’une application est supprimée de l’exécution liste d’applications.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT onRemoveApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD                     dwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pda`  
 [in] Application qui a été supprimée de l’exécution liste d’applications.  
  
 `dwAppCookie`  
 [in] Le cookie fourni lors de l’application a été ajoutée dans la liste des applications.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode indique qu’une application a été supprimée de l’exécution liste d’applications.  
  
## <a name="see-also"></a>Voir aussi  
 [IMachineDebugManagerEvents (Interface)](../../winscript/reference/imachinedebugmanagerevents-interface.md)   
 [IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)