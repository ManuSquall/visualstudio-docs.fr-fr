---
title: IDebugEngineLaunch2::CanTerminateProcess | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngineLaunch2::CanTerminateProcess
helpviewer_keywords:
- IDebugEngineLaunch2::CanTerminateProcess
ms.assetid: 7973454d-c957-4123-a0ee-80ebcdbbd2d1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: de1fece83161b70a3df6d8faed358ca2d22cd232
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49829896"
---
# <a name="idebugenginelaunch2canterminateprocess"></a>IDebugEngineLaunch2::CanTerminateProcess
Détermine si un processus peut être arrêté.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CanTerminateProcess (   
   IDebugProcess2* pProcess  
);  
```  
  
```csharp  
int CanTerminateProcess (   
   IDebugProcess2 pProcess  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pProcess`  
 [in] Un [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) objet qui représente la fin du processus.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Retourne `S_FALSE` si le moteur ne peut pas mettre fin au processus, par exemple, car l’accès est refusé.  
  
## <a name="remarks"></a>Notes  
 Si cette méthode retourne `S_OK`, puis il la [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md) méthode peut être appelée pour réellement mettre fin au processus.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)