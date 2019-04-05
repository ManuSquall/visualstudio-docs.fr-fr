---
title: IDebugEngineLaunch2::CanTerminateProcess | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::CanTerminateProcess
helpviewer_keywords:
- IDebugEngineLaunch2::CanTerminateProcess
ms.assetid: 7973454d-c957-4123-a0ee-80ebcdbbd2d1
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c46332f024f883183e4fa10321e1ecdcc8961c69
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58938674"
---
# <a name="idebugenginelaunch2canterminateprocess"></a>IDebugEngineLaunch2::CanTerminateProcess
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Détermine si un processus peut être arrêté.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
