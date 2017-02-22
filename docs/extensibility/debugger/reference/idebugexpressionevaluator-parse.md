---
title: "IDebugExpressionEvaluator::Parse | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionEvaluator::Parse"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator::Parse (méthode)"
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugExpressionEvaluator::Parse
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode convertit une chaîne d'expression d'une expression analysée.  
  
## Syntaxe  
  
```cpp#  
HRESULT Parse(   
   LPCOLESTR                upstrExpression,  
   PARSEFLAGS               dwFlags,  
   UINT                     nRadix,  
   BSTR*                    pbstrError,  
   UINT*                    pichError,  
   IDebugParsedExpression** ppParsedExpression  
);  
```  
  
```c#  
int Parse(  
   string                     upstrExpression,   
   enum_PARSEFLAGS            dwFlags,   
   uint                       nRadix,   
   out string                 pbstrError,   
   out uint                   pichError,   
   out IDebugParsedExpression ppParsedExpression  
);  
```  
  
#### Paramètres  
 `upstrExpression`  
 \[in\]  la chaîne d'expression à analyser.  
  
 `dwFlags`  
 \[in\]  une collection de constantes de [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) qui déterminent comment l'expression doit être analysée.  
  
 `nRadix`  
 \[in\]  Base à utiliser pour interpréter des informations numériques.  
  
 `pbstrError`  
 \[out\]  Retourne l'erreur en forme de texte explicite.  
  
 `pichError`  
 \[out\]  Retourne la position de début de l'erreur dans la chaîne d'expression.  
  
 `ppParsedExpression`  
 \[out\]  Retourne l'expression analysée dans un objet d' [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) .  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 cette méthode produit une expression analysée, pas une valeur réelle.  Une expression analysée est prête à être évaluée, c. autrement dit., a converti en une valeur.  
  
## Voir aussi  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)   
 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)