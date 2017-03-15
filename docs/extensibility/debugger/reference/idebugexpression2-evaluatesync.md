---
title: "IDebugExpression2::EvaluateSync | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpression2::EvaluateSync"
helpviewer_keywords: 
  - "IDebugExpression2::EvaluateSync"
ms.assetid: 88964915-dce3-4005-b4f3-9f37415e41e4
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# IDebugExpression2::EvaluateSync
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode évalue l'expression de façon synchrone.  
  
## Syntaxe  
  
```cpp#  
HRESULT EvaluateSync(   
   EVALFLAGS             dwFlags,  
   DWORD                 dwTimeout,  
   IDebugEventCallback2* pExprCallback,  
   IDebugProperty2**     ppResult  
);  
```  
  
```c#  
int EvaluateSync(  
   enum_EVALFLAGS       dwFlags,   
   uint                 dwTimeout,   
   IDebugEventCallback2 pExprCallback,   
   out IDebugProperty2  ppResult  
);  
```  
  
#### Paramètres  
 `dwFlags`  
 \[in\]  Une combinaison des indicateurs d'énumération d' [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) qui évaluation de l'expression de contrôle.  
  
 `dwTimeout`  
 \[in\]  Durée maximale, en millisecondes, d'attendre avant le retour de cette méthode.  Utilisation `INFINITE` d'attente dure indéfiniment.  
  
 `pExprCallback`  
 \[in\]ce paramètre est toujours une valeur NULL.  
  
 `ppResult`  
 \[out\]  Retourne l'objet d' [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) qui contient le résultat de l'évaluation d'une expression.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon retourne un code d'erreur.  Certains codes d'erreur classiques sont :  
  
|Erreur|Description|  
|------------|-----------------|  
|E\_EVALUATE\_BUSY\_WITH\_EVALUATION|Une autre expression actuellement est évaluée, et l'évaluation d'une expression simultanée n'est pas prise en charge.|  
|E\_EVALUATE\_TIMEOUT|Évaluation a expiré.|  
  
## Notes  
 Pour l'évaluation synchrone, il n'est pas nécessaire d'envoyer un événement vers Visual Studio au terme de l'évaluation.  
  
## Exemple  
 L'exemple de code suivant montre comment appliquer cette méthode d'un objet simple d' `CExpression` qui implémente l'interface d' [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) .  
  
```cpp#  
HRESULT CExpression::EvaluateSync(EVALFLAGS dwFlags,  
                                  DWORD dwTimeout,  
                                  IDebugEventCallback2* pExprCallback,  
                                  IDebugProperty2** ppResult)  
{  
    // Set the aborted state to FALSE.    
    m_bAborted = FALSE;    
    // Delegate the evaluation to EvalExpression.    
    return EvalExpression(TRUE, ppResult);    
}  
  
HRESULT CExpression::EvalExpression(BOOL bSynchronous,  
                                    IDebugProperty2** ppResult)  
{  
    HRESULT hr;  
  
    // Get the value of an environment variable.  
    PCSTR pszVal = m_pEnvBlock->GetEnv(m_pszVarName);  
    // Create and initialize a CEnvVar object with the retrieved value.  
    // CEnvVar implements the IDebugProperty2 interface.  
    CComObject<CEnvVar> *pEnvVar;  
    CComObject<CEnvVar>::CreateInstance(&pEnvVar);  
    pEnvVar->Init(m_pszVarName, pszVal, m_pDoc);  
  
    if (pszVal) {  
        // Check for synchronous evaluation.  
        if (bSynchronous) {  
            // Set and AddRef the result, IDebugProperty2 interface.  
            *ppResult = pEnvVar;  
            (*ppResult)->AddRef();  
            hr = S_OK;  
        } else {  
            //For asynchronous evaluation, send an evaluation complete event.  
            CExprEvalEvent *pExprEvent = new CExprEvalEvent(this, pEnvVar);  
            pExprEvent->SendEvent(m_pExprCallback, NULL, NULL, NULL);  
        }  
    } else {  
        // If a valid value is not retrieved, return E_FAIL.  
        hr = E_FAIL;  
    }  
    return hr;  
}  
```  
  
## Voir aussi  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)