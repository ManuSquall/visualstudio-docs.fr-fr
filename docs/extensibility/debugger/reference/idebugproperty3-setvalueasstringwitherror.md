---
description: Définit la valeur de cette propriété et retourne un message d’erreur, si nécessaire.
title: 'IDebugProperty3 :: SetValueAsStringWithError | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::SetValueAsStringWithError
helpviewer_keywords:
- IDebugProperty3::SetValueAsStringWithError
ms.assetid: b378368f-4a45-4b2f-8e3d-3bff7a18ab17
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bd789561a85f23cff2ec794d4877662441f9149e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168099"
---
# <a name="idebugproperty3setvalueasstringwitherror"></a>IDebugProperty3::SetValueAsStringWithError
Définit la valeur de cette propriété et retourne un message d’erreur, si nécessaire.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetValueAsStringWithError(
    LPCOLESTR pszValue,
    DWORD     dwRadix,
    DWORD     dwTimeout,
    BSTR*     errorString
);
```

```csharp
int SetValueAsStringWithError(
    string     pszValue,
    uint       dwRadix,
    uint       dwTimeout,
    out string errorString
);
```

## <a name="parameters"></a>Paramètres
`pszValue`\
dans Valeur à définir.

`dwRadix`\
dans Base de la valeur qui est définie.

`dwTimeout`\
dans Durée d’attente de la définition de la valeur ( `INFINITE` signifie attendre indéfiniment).

`errorString`\
à Si une erreur s’est produite lors de la définition de la valeur, cela contient la raison de l’échec.

## <a name="return-value"></a>Valeur renvoyée
En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
La valeur entrante peut être une expression à évaluer.

## <a name="example"></a>Exemple
L’exemple suivant montre comment implémenter cette méthode pour un objet **CProperty** qui expose l’interface [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) .

```cpp
HRESULT CProperty::SetValueAsStringWithError(
    LPCOLESTR in_szValue,
    DWORD in_RADIX,
    DWORD in_TIMEOUT,
    BSTR * out_ERRORTEXT
)
{
    // precondition
    REQUIRE( NULL != in_szValue );

    if (NULL == in_szValue)
        return E_INVALIDARG;

    INVARIANT( this );
    if (!this->ClassInvariant())
        return E_UNEXPECTED;

    if (NULL == m_pPropertyContext->m_pCEE->m_LanguageSpecificUseCases.pfSetValue)
        return S_OK;

    // function body
    DEBUG_PROPERTY_INFO dpInfo,dpInfo2;
    HRESULT HR = this->GetPropertyInfo(DEBUGPROP_INFO_FULLNAME | DEBUGPROP_INFO_ATTRIB | DEBUGPROP_INFO_TYPE | DEBUGPROP_INFO_VALUE_AUTOEXPAND,
                                       in_RADIX,
                                       in_TIMEOUT,
                                       NULL,
                                       0,
                                       &dpInfo);

    if (ENSURE( S_OK == HR ))
    {
        REQUIRE( NULL != dpInfo.bstrFullName );
        REQUIRE( NULL != dpInfo.bstrType );

        REQUIRE( NULL == dpInfo.bstrName );
        REQUIRE( NULL == dpInfo.bstrValue );
        REQUIRE( NULL == dpInfo.pProperty );

        BSTR bstrError = NULL;

        UINT ichError = 0;
        IDebugProperty2* pProperty = NULL;
        IDebugParsedExpression* pParsedExpression = NULL;

        CComBSTR bstrValue = dpInfo.bstrFullName;
        bstrValue += L" = ";
        bstrValue += in_szValue;
        HR = this->m_pPropertyContext->m_pCEE->
                Parse(bstrValue, 0, in_RADIX, &bstrError, &ichError, &pParsedExpression);
        if (S_OK == HR)
        {
            REQUIRE( NULL == bstrError );
            HR = pParsedExpression->EvaluateSync(EVAL_NOEVENTS | EVAL_RETURNVALUE,
                                                 in_TIMEOUT,
                                                 m_pPropertyContext->m_pSymbolProvider,
                                                 m_pPropertyContext->m_pAddress,
                                                 m_pPropertyContext->m_pBinder,
                                                 NULL,
                                                 &pProperty);

            dpInfo2.dwAttrib = DBG_ATTRIB_VALUE_ERROR;
            if (pProperty)
            {
                pProperty->GetPropertyInfo(DEBUGPROP_INFO_ATTRIB | DEBUGPROP_INFO_VALUE,10,in_TIMEOUT,NULL,0,&dpInfo2);
            }
            if (DBG_ATTRIB_VALUE_ERROR & dpInfo2.dwAttrib)
            {
                HR = E_FAIL;
                bstrError = dpInfo2.bstrValue;
            }
            else
            {
                ::SysFreeString(dpInfo.bstrValue);
            }
            EXTERNAL_RELEASE(pProperty);
            EXTERNAL_RELEASE(pParsedExpression);
        }

        if (bstrError)
        {
            if(out_ERRORTEXT)
            {
                *out_ERRORTEXT = bstrError;
                bstrError = NULL;
            }
            else
            {
                ::SysFreeString(bstrError);
            }
        }
        ::SysFreeString(dpInfo.bstrFullName);
        ::SysFreeString(dpInfo.bstrType);
    }

    // postcondition
    INVARIANT( this );

    return HR;
}
```

## <a name="see-also"></a>Voir aussi
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
