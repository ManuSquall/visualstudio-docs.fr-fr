---
title: "IDebugExpressionEvaluator2::PreloadModules | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator2::PreloadModules"
  - "PreloadModules"
ms.assetid: bcf9b968-ee14-4a92-88ad-926268a44e03
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugExpressionEvaluator2::PreloadModules
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Précharge les modules désignés par le fournisseur spécifié de symbole.  
  
## Syntaxe  
  
```cpp#  
HRESULT PreloadModules (  
   IDebugSymbolProvider* pSym  
);  
```  
  
```c#  
int PreloadModules (  
   IDebugSymbolProvider pSym  
);  
```  
  
#### Paramètres  
 `pSym`  
 \[in\]  Fournisseur de symbole dont les modules sont préchargés.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Cette méthode facultative est utilisée lorsque vous effectuez une opération d'attachement d'hébergement\-processus.  Cela permet à l'évaluateur d'expression la possibilité « de réchauffer » dans le cadre de l'attachement.  
  
## Exemple  
 L'exemple suivant indique comment appliquer cette méthode d'un objet **d'ExpressionEvaluatorPackage** qui expose l'interface d' [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md) .  
  
```cpp#  
STDMETHODIMP ExpressionEvaluatorPackage::PreloadModules  
(  
    IDebugSymbolProvider *pSym  
)  
{  
    HRESULT hr = NOERROR;  
    RuntimeMemberDescriptor  * prtMemberDesc;  
    RuntimeClassDescriptor *prtClassDesc;  
    CComPtr<IDebugClassField> pClassField;  
    IfFalseGo(pSym,E_INVALIDARG);  
  
    prtMemberDesc = &(g_rgRTLangMembers[StandardModuleAttributeCtor]);  
    prtClassDesc = &(g_rgRTLangClasses[prtMemberDesc->rtParent]);  
    pSym->GetClassTypeByName(prtClassDesc->wszClassName, nmCaseSensitive, &pClassField);  
  
    pClassField = NULL;  
    prtMemberDesc = &(g_rgRTLangMembers[LoadAssembly]);  
    prtClassDesc = &(g_rgRTLangClasses[prtMemberDesc->rtParent]);  
    pSym->GetClassTypeByName(prtClassDesc->wszClassName, nmCaseSensitive, &pClassField);  
  
Error:  
    return hr;  
}  
```  
  
## Voir aussi  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)