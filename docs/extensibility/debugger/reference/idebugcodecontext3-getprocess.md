---
title: IDebugCodeContext3::GetProcess | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugCodeContext3::GetProcess
ms.assetid: e082e494-2255-4d9d-a5a9-6dadd904bea8
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4689a8fb1cb546187d33cc2aefcbb9d8141fa42f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcodecontext3getprocess"></a>IDebugCodeContext3::GetProcess
Récupère une référence à l’interface du processus de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetProcess(   
   IDebugProcess2 **ppProcess  
);  
```  
  
```csharp  
public int GetProcess(   
   out IDebugProcess2 ppProcess  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppProcess`  
 [out] Référence à l’interface de processus de débogage.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment implémenter cette méthode pour un **CDebugCodeContext** objet qui expose la [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) interface.  
  
```cpp  
HRESULT CDebugCodeContext::GetProcess(IDebugProcess2** ppProcess)  
{  
    HRESULT hr = S_OK;  
    CComPtr<CDebugEngine> pEngine;  
    CComPtr<IDebugPort2> pPort2;  
  
    IfFalseGo( ppProcess, E_INVALIDARG );  
    *ppProcess = NULL;  
  
    IfFalseGo( m_pProgram, E_FAIL );  
    IfFailGo( ((CDebugProgram *)m_pProgram)->GetEngine(&pEngine) );  
    IfFailGo( pEngine->GetSDMProcess(ppProcess) );  
  
Error:  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)