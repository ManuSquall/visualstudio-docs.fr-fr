---
title: 'IDebugProgram2 :: GetProcess | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 366b35a90eb44496dc1b50cd85dfa0fef5656ddb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148657"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtient le processus dans lequel ce programme s’exécute.  
  
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
 à Retourne l’interface [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) qui représente le processus.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 À moins qu’un moteur de débogage (DE) n’implémente l’interface [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) , l’implémentation de de cette méthode doit toujours retourner, `E_NOTIMPL` car un de ne peut pas déterminer le processus dans lequel il s’exécute et, par conséquent, ne peut pas satisfaire à une implémentation de cette méthode.  
  
 L’implémentation de l' `IDebugEngineLaunch2` interface signifie que le de doit savoir comment créer un processus ; par conséquent, l’implémentation de de l’interface [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) est en mesure de connaître le processus dans lequel elle s’exécute.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
