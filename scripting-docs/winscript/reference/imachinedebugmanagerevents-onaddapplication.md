---
title: 'IMachineDebugManagerEvents :: onAddApplication | Microsoft Docs'
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
ms.openlocfilehash: fe710ce9a126e344fc88024b7bf5fd2b993e31b3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576104"
---
# <a name="imachinedebugmanagereventsonaddapplication"></a>IMachineDebugManagerEvents::onAddApplication
Gère l’événement lorsqu’une application est ajoutée à la liste des applications en cours d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT onAddApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD                     dwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pda`  
 dans Application qui a été ajoutée à la liste des applications en cours d’exécution.  
  
 `dwAppCookie`  
 dans Cookie fourni lorsque l’application a été ajoutée à la liste des applications.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode indique qu’une application a été ajoutée à la liste des applications en cours d’exécution.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IMachineDebugManagerEvents](../../winscript/reference/imachinedebugmanagerevents-interface.md)  
 [IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)