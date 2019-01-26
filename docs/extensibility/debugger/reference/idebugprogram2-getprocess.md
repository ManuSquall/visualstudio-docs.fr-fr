---
title: IDebugProgram2::GetProcess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1dcfc207a485a3b1eb5ec24930f613692fac69e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54962980"
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
 Sauf si un moteur de débogage (dé) implémente la [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) interface, l’implémentation de l’Allemagne de cette méthode doit retourner toujours `E_NOTIMPL` , car un DE ne peut pas déterminer quel processus, il s’exécute dans et par conséquent ne peut pas répondre à une implémentation de cette méthode.  
  
 Implémentation de la `IDebugEngineLaunch2` interface signifie que le DE doive savoir comment créer un processus ; par conséquent, de la DE mise en œuvre de la [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interface est en mesure de savoir à quel processus, il est en cours d’exécution dans.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)