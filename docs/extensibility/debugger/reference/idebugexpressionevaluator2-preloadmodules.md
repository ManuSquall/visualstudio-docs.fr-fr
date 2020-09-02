---
title: IDebugExpressionEvaluator2 ::P reloadModules | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::PreloadModules
- PreloadModules
ms.assetid: bcf9b968-ee14-4a92-88ad-926268a44e03
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: db345fb2936ef7278675407549798ae669487f06
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729331"
---
# <a name="idebugexpressionevaluator2preloadmodules"></a>IDebugExpressionEvaluator2::PreloadModules
Précharge les modules désignés par le fournisseur de symboles spécifié.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT PreloadModules (
    IDebugSymbolProvider* pSym
);
```

```csharp
int PreloadModules (
    IDebugSymbolProvider pSym
);
```

## <a name="parameters"></a>Paramètres
`pSym`\
dans Fournisseur de symboles pour lequel les modules seront préchargés.

## <a name="return-value"></a>Valeur renvoyée
En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
Cette méthode facultative est utilisée quand vous effectuez un attachement de processus d’hébergement. Il donne à EE une chance de « chauffer » dans le cadre de l’attachement.

## <a name="example"></a>Exemple
L’exemple suivant montre comment implémenter cette méthode pour un objet **ExpressionEvaluatorPackage** qui expose l’interface [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md) .

```cpp
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

## <a name="see-also"></a>Voir aussi
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
