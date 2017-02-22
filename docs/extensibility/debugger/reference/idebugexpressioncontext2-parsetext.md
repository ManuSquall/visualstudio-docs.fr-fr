---
title: "IDebugExpressionContext2::ParseText | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionContext2::ParseText"
helpviewer_keywords: 
  - "IDebugExpressionContext2::ParseText"
ms.assetid: f58575db-f926-4ac8-83ff-7b3b86ab61e2
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugExpressionContext2::ParseText
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Analyse une expression sous forme de texte pour une évaluation ultérieure.  
  
## Syntaxe  
  
```cpp#  
HRESULT ParseText(   
   LPCOLESTR           pszCode,  
   PARSEFLAGS          dwFlags,  
   UINT                nRadix,  
   IDebugExpression2** ppExpr,  
   BSTR*               pbstrError,  
   UINT*               pichError  
);  
```  
  
```c#  
int ParseText(   
   string                pszCode,  
   enum_PARSEFLAGS       dwFlags,  
   uint                  nRadix,  
   out IDebugExpression2 ppExpr,  
   out string            pbstrError,  
   out uint              pichError  
);  
```  
  
#### Paramètres  
 `pszCode`  
 \[in\]  l'expression à analyser.  
  
 `dwFlags`  
 \[in\]  Une combinaison des indicateurs d'énumération de [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) qui contrôle l'analyse.  
  
 `nRadix`  
 \[in\]  La base à utiliser lors de l'analyse des informations numériques dans `pszCode`.  
  
 `ppExpr`  
 \[out\]  Retourne l'objet d' [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) qui représente l'expression analysée, qui est prête pour la liaison et évaluation.  
  
 `pbstrError`  
 \[out\]  Retourne le message d'erreur si l'expression contient une erreur.  
  
 `pichError`  
 \[out\]  Retourne l'index du caractère de l'erreur dans `pszCode` si l'expression contient une erreur.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Lorsque cette méthode est appelée, un moteur \(DE\) de débogage doit analyser l'expression et la validation pour l'exactitude.  Les paramètres d' `pbstrError` et d' `pichError` peuvent être remplis si l'expression est valide.  
  
 Notez que l'expression n'est pas évaluée, uniquement analysé.  Un appel ultérieur aux méthodes d' [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou d' [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) évalue l'expression analysée.  
  
## Exemple  
 L'exemple de code suivant montre comment appliquer cette méthode d'un objet simple d' `CEnvBlock` qui expose l'interface d' [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) .  Cet exemple considère l'expression à analyser comme nom d'une variable d'environnement et récupère la valeur de cette variable.  
  
```cpp#  
HRESULT CEnvBlock::ParseText(  
   LPCOLESTR           pszCode,  
   PARSEFLAGS          dwFlags,  
   UINT                nRadix,  
   IDebugExpression2 **ppExpr,  
   BSTR               *pbstrError,  
   UINT               *pichError)  
{  
   HRESULT hr = E_OUTOFMEMORY;    
   // Create an integer variable with a value equal to one plus    
   // twice the length of the passed expression to be parsed.    
   int iAnsiLen      = 2 * (wcslen(pszCode)) + 1;    
   // Allocate a character string of the same length.    
   char *pszAnsiCode = (char *) malloc(iAnsiLen);    
  
   // Check for successful memory allocation.    
   if (pszAnsiCode) {    
      // Map the wide-character pszCode string to the new pszAnsiCode character string.    
      WideCharToMultiByte(CP_ACP, 0, pszCode, -1, pszAnsiCode, iAnsiLen, NULL, NULL);    
      // Check to see if the app can succesfully get the environment variable.    
      if (GetEnv(pszAnsiCode)) {    
  
         // Create and initialize a CExpression object.    
         CComObject<CExpression> *pExpr;    
         CComObject<CExpression>::CreateInstance(&pExpr);    
            pExpr->Init(pszAnsiCode, this, NULL);    
  
         // Assign the pointer to the new object to the passed argument  
         // and AddRef the object.    
         *ppExpr = pExpr;    
         (*ppExpr)->AddRef();    
         hr = S_OK;    
      // If the program cannot succesfully get the environment variable.    
      } else {    
         // Set the errror message and return E_FAIL.    
         *pbstrError = SysAllocString(L"No such environment variable.");    
         hr = E_FAIL;    
      }    
      // Free the local character string.    
      free(pszAnsiCode);    
   }    
   return hr;    
}    
```  
  
## Voir aussi  
 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)   
 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)   
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)