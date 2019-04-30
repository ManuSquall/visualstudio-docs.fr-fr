---
title: IMachineDebugManagerEvents::onAddApplication | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManagerEvents.onAddApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManagerEvents::onAddApplication
ms.assetid: 00a54b91-36d5-430d-b654-5e2abe5300cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f063e36296d6a5a77208bac2fe533274a6f9c07f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62965788"
---
# <a name="imachinedebugmanagereventsonaddapplication"></a>IMachineDebugManagerEvents::onAddApplication
Gère l’événement lorsqu’une application est ajoutée à l’exécution liste d’applications.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT onAddApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD                     dwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pda`  
 [in] Application qui a été ajoutée à l’exécution liste d’applications.  
  
 `dwAppCookie`  
 [in] Le cookie fourni lors de l’application a été ajoutée à la liste des applications.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode indique qu’une application a été ajoutée à l’exécution liste d’applications.  
  
## <a name="see-also"></a>Voir aussi  
 [IMachineDebugManagerEvents (Interface)](../../winscript/reference/imachinedebugmanagerevents-interface.md)   
 [IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)