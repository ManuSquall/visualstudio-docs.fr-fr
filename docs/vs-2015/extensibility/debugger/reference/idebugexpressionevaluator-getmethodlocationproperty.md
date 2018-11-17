---
title: IDebugExpressionEvaluator::GetMethodLocationProperty | Microsoft Docs
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
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f8391adf8fab0deda937cb49f5594aa5275a9ff7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51738498"
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette méthode convertit un emplacement de la méthode et le décalage en une adresse mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetMethodLocationProperty(   
   LPCOLESTR             upstrFullyQualifiedMethodPlusOffset,  
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   IDebugProperty2**     ppProperty  
);  
```  
  
```csharp  
int GetMethodLocationProperty(  
   string               upstrFullyQualifiedMethodPlusOffset,   
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   out IDebugProperty2  ppProperty  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `upstrFullyQualifiedMethodPlusOffset`  
 [in] L’emplacement de la méthode et le décalage, exprimé sous forme de chaîne.  
  
 `pSymbolProvider`  
 [in] Le fournisseur de symboles exprimée sous la forme un [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) objet.  
  
 `pAddress`  
 [in] Une adresse dans la méthode, exprimée sous la forme un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objet.  
  
 `pBinder`  
 [in] Le binder exprimée sous la forme un [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) objet.  
  
 `ppProperty`  
 [out] Retourne un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interface qui représente l’adresse mémoire.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 L’adresse retournée peut être utilisé pour définir un point d’arrêt, par exemple.  
  
 Malgré son nom `upstrFullyQualifiedMethodPlusOffset`, ce paramètre peut être passé à un nom de méthode partiellement qualifié. Dans ce cas, la méthode sélectionnée est celui qui englobe `pAddress`. Interprétation de ce paramètre est l’implémentation de l’évaluateur d’expression et le langage qu'il prend en charge.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)

