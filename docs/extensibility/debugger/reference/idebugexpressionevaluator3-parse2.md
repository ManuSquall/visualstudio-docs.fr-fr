---
title: "IDebugExpressionEvaluator3::Parse2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator3::Parse2"
ms.assetid: 78099628-d600-4f76-b7c8-ee07c864af1e
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugExpressionEvaluator3::Parse2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Convertit une chaîne d'expression d'une expression analysée données le fournisseur de symbole et l'adresse du frame évaluation.  
  
## Syntaxe  
  
```cpp#  
HRESULT Parse2 (  
   LPCOLESTR                upstrExpression,  
   PARSEFLAGS               dwFlags,  
   UINT                     nRadix,  
   IDebugSymbolProvider*    pSymbolProvider,  
   IDebugAddress*           pAddress,  
   BSTR*                    pbstrError,  
   UINT*                    pichError,  
   IDebugParsedExpression** ppParsedExpression  
);  
```  
  
```c#  
HRESULT Parse2 (  
   string                     upstrExpression,  
   enum_PARSEFLAGS            dwFlags,  
   uint                       nRadix,  
   IDebugSymbolProvider       pSymbolProvider,  
   IDebugAddress              pAddress,  
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
  
 `pSymbolProvider`  
 \[in\]  interface du fournisseur de symbole.  
  
 `pAddress`  
 \[in\]  Adresse du frame évaluation.  
  
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
  
## Exemple  
 L'exemple suivant indique comment appliquer cette méthode d'un objet **de l'CEE** qui expose l'interface d' [IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md) .  
  
```cpp#  
HRESULT CEE::Parse2 ( LPCOLESTR in_szExprText,  
  PARSEFLAGS in_FLAGS,  
  UINT in_RADIX,  
  IDebugSymbolProvider *pSymbolProvider,  
  IDebugAddress *pAddress,  
  BSTR* out_pbstrError,  
  UINT* inout_pichError,  
  IDebugParsedExpression** out_ppParsedExpression )  
{  
    // precondition  
    REQUIRE( NULL != in_szExprText );  
    //REQUIRE( NULL != out_pbstrError );  
    REQUIRE( NULL != inout_pichError );  
    REQUIRE( NULL != out_ppParsedExpression );  
  
    if (NULL == in_szExprText)  
        return E_INVALIDARG;  
  
    if (NULL == inout_pichError)  
        return E_POINTER;  
  
    if (NULL == out_ppParsedExpression)  
        return E_POINTER;  
  
    if (out_pbstrError)  
        *out_pbstrError = NULL;  
  
    *out_ppParsedExpression = NULL;  
  
    INVARIANT( this );  
  
    if (!this->ClassInvariant())  
        return E_UNEXPECTED;  
  
    // function body  
    EEDomain::fParseExpression DomainVal =  
    {  
        this,                   // CEE*  
        in_szExprText,          // LPCOLESTR  
        in_FLAGS,               // EVALFLAGS  
        in_RADIX,               // RADIX  
        out_pbstrError      ,   // BSTR*  
        inout_pichError,        // UINT*  
        pSymbolProvider,  
        out_ppParsedExpression  // Output  
    };  
  
    return (*m_LanguageSpecificUseCases.pfParseExpression)(DomainVal);  
}  
```  
  
## Voir aussi  
 [IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)