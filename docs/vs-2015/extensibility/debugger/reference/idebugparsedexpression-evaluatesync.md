---
title: IDebugParsedExpression::EvaluateSync | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugParsedExpression::EvaluateSync
helpviewer_keywords:
- IDebugParsedExpression::EvaluateSync method
ms.assetid: 0ea04cfa-de87-4b6c-897e-4572c1a28942
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 01c75f47d2014ab833e7d213bdd871fbb8c4f1a2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49236819"
---
# <a name="idebugparsedexpressionevaluatesync"></a>IDebugParsedExpression::EvaluateSync
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette méthode évalue l’expression analysée et éventuellement convertit le résultat à un autre type de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 [in] Une combinaison de [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) constantes qui contrôlent la manière dont l’expression doit être évaluée.  
  
 `dwTimeout`  
 [in] Spécifie la durée maximale, en millisecondes, à attendre avant de retourner à partir de cette méthode. Utilisez `INFINITE` pour attendre indéfiniment.  
  
 `pSymbolProvider`  
 [in] Le fournisseur de symboles, exprimée sous la forme un [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) interface.  
  
 `pAddress`  
 [in] L’emplacement d’exécution actuel dans une méthode, exprimée sous la forme un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface.  
  
 `pBinder`  
 [in] Le binder, exprimée sous la forme un [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interface.  
  
 `bstrResultType`  
 [in] Le type de résultat doit être casté en. Cet argument peut être une valeur null.  
  
 `ppResult`  
 [out] Retourne le [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interface qui représente les résultats d’évaluation.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Le contexte d’évaluation d’expression est fourni par `pAddress`, ce qui rend possible de déterminer la méthode conteneur et utiliser la portée du langage des règles pour déterminer la valeur des symboles dans l’expression.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)

