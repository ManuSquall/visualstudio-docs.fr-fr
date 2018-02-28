---
title: IDebugProgram2::GetProcess | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 0202433bdae8583eaab6cbca2fbf1e2c9cde08bc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
Obtenir le processus de ce programme est en cours d’exécution dans.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetProcess(  
   IDebugProcess2** ppProcess  
);  
```  
  
```csharp  
int GetProcess(  
   out IDebugProcess2 ppProcess  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppProcess`  
 [out] Retourne le [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) interface qui représente le processus.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Sauf si un moteur de débogage (DE) implémente la [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) interface, la mise en œuvre de la DE cette méthode doit toujours renvoyer `E_NOTIMPL` car un DE ne peut pas déterminer quel processus, il s’exécute dans et, par conséquent ne peut pas répondent à une implémentation de cette méthode.  
  
 Implémentation de la `IDebugEngineLaunch2` interface signifie que le DE doit savoir comment créer un processus ; par conséquent, de la DE mise en oeuvre de la [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interface est en mesure de savoir quel processus, il est en cours d’exécution dans.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)