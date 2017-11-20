---
title: IDebugExpressionEvaluator::Parse | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugExpressionEvaluator::Parse
helpviewer_keywords: IDebugExpressionEvaluator::Parse method
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b0491cd6d80db449fbeaa8fee2a6040a66082558
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugexpressionevaluatorparse"></a>IDebugExpressionEvaluator::Parse
Cette méthode convertit une chaîne d’expression à une expression analysée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Parse(   
   LPCOLESTR                upstrExpression,  
   PARSEFLAGS               dwFlags,  
   UINT                     nRadix,  
   BSTR*                    pbstrError,  
   UINT*                    pichError,  
   IDebugParsedExpression** ppParsedExpression  
);  
```  
  
```csharp  
int Parse(  
   string                     upstrExpression,   
   enum_PARSEFLAGS            dwFlags,   
   uint                       nRadix,   
   out string                 pbstrError,   
   out uint                   pichError,   
   out IDebugParsedExpression ppParsedExpression  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `upstrExpression`  
 [in] La chaîne d’expression à analyser.  
  
 `dwFlags`  
 [in] Une collection de [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) constantes qui déterminent comment l’expression doit être analysée.  
  
 `nRadix`  
 [in] Base à utiliser pour interpréter les informations numériques.  
  
 `pbstrError`  
 [out] Retourne l’erreur en tant que texte explicite.  
  
 `pichError`  
 [out] Retourne la position de caractère de début de l’erreur dans la chaîne d’expression.  
  
 `ppParsedExpression`  
 [out] Retourne l’expression analysée dans un [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) objet.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Cette méthode génère une expression analysée, pas une valeur réelle. Une expression analysée est prête à être évaluée, autrement dit, convertie en une valeur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)   
 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)