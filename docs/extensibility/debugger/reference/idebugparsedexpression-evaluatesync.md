---
title: IDebugParsedExpression::EvaluateSync | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugParsedExpression::EvaluateSync
helpviewer_keywords: IDebugParsedExpression::EvaluateSync method
ms.assetid: 0ea04cfa-de87-4b6c-897e-4572c1a28942
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 261359ae3dc82f8544d0f48cf0e8f1103ccedd5b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugparsedexpressionevaluatesync"></a>IDebugParsedExpression::EvaluateSync
Cette méthode évalue l’expression analysée et éventuellement convertit le résultat à un autre type de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EvaluateSync(   
   DWORD                 dwEvalFlags,  
   DWORD                 dwTimeout,  
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   BSTR                  bstrResultType,  
   IDebugProperty2**     ppResult  
);  
```  
  
```csharp  
int EvaluateSync(  
   uint                 dwEvalFlags,   
   uint                 dwTimeout,   
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   string               bstrResultType,   
   out IDebugProperty2  ppResult  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwEvalFlags`  
 [in] Une combinaison de [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) constantes pour contrôlent la manière dont l’expression à évaluer.  
  
 `dwTimeout`  
 [in] Spécifie la durée maximale, en millisecondes, à attendre avant de retourner à partir de cette méthode. Utilisez `INFINITE` pour attendre indéfiniment.  
  
 `pSymbolProvider`  
 [in] Le fournisseur de symboles, exprimée sous la forme un [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) interface.  
  
 `pAddress`  
 [in] L’emplacement actuel de l’exécution d’une méthode, exprimée sous la forme un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface.  
  
 `pBinder`  
 [in] Le classeur, exprimée sous la forme un [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interface.  
  
 `bstrResultType`  
 [in] Le type du résultat doit être converti en. Cet argument peut être une valeur null.  
  
 `ppResult`  
 [out] Retourne le [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interface qui représente les résultats de l’évaluation.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Le contexte d’évaluation de l’expression est donné par `pAddress`, ce qui rend possible déterminer la méthode qui le contient et puis utiliser la portée du langage des règles pour déterminer la valeur des symboles dans l’expression.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)