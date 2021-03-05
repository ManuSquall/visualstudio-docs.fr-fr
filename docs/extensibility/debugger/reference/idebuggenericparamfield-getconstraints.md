---
description: Récupère les contraintes associées à ce paramètre générique.
title: 'IDebugGenericParamField :: GetConstraints | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericParamField::GetConstraints
- GetConstraints
ms.assetid: 86a78b5a-ee0f-4999-a0ba-919d3dc7d969
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 51c3dcbeda334953ef09f8bcfbf1789450201a0c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102172784"
---
# <a name="idebuggenericparamfieldgetconstraints"></a>IDebugGenericParamField::GetConstraints
Récupère les contraintes associées à ce paramètre générique.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetConstraints(
    ULONG32       cConstraints,
    IDebugField** ppConstraints,
    ULONG32*      pcConstraints
);
```

```csharp
int GetConstraints(
    uint              cConstraints,
    out IDebugField[] ppConstraints,
    ref uint          pcConstraints
);
```

## <a name="parameters"></a>Paramètres
`cConstraints`\
dans Nombre de contraintes.

`ppConstraints`\
à Retourne un tableau qui contient les contraintes associées à ce champ.

`pcConstraints`\
[in, out] Nombre de contraintes dans le `ppConstraints` tableau.

## <a name="return-value"></a>Valeur renvoyée
En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="example"></a>Exemple
L’exemple suivant montre comment implémenter cette méthode pour un objet **CDebugGenericParamFieldType** qui expose l’interface [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md) .

```cpp
HRESULT CDebugGenericParamFieldType::GetConstraints(
    ULONG32 cConstraints,
    IDebugField** ppConstraints,
    ULONG32* pcConstraints)
{
    HRESULT hr = S_OK;
    CComPtr<IMetaDataImport> pMetadata;
    CComPtr<IMetaDataImport2> pMetadata2;
    mdGenericParamConstraint* rgParamConsts = NULL;
    HCORENUM hEnum = 0;
    ULONG cConst = 0;
    ULONG iConst;
    ULONG iConstOut = 0;

    METHOD_ENTRY( CDebugGenericParamFieldType::GetConstraints );

    IfFalseGo(ppConstraints && pcConstraints, E_INVALIDARG );
    *pcConstraints = 0;

    IfNullGo( rgParamConsts = new mdGenericParamConstraint[cConstraints], E_OUTOFMEMORY);

    IfFailGo( m_spSH->GetMetadata( m_idModule, &pMetadata ) );
    IfFailGo( pMetadata->QueryInterface(IID_IMetaDataImport2, (void**)&pMetadata2) );
    IfFailGo( pMetadata2->EnumGenericParamConstraints( &hEnum,
              m_tokParam,
              rgParamConsts,
              cConstraints,
              &cConst) );
    pMetadata->CloseEnum(hEnum);
    hEnum = NULL;

    for (iConst = 0; iConst < cConst; iConst++)
    {
        mdToken tokConst;

        IfFailGo( pMetadata2->GetGenericParamConstraintProps( rgParamConsts[iConst],
                  NULL,
                  &tokConst ) );
        switch (TypeFromToken(tokConst))
        {
            case mdtTypeRef:
                {
                    Module_ID mid;
                    mdTypeDef tokClass;

                    IfFailGo( CDebugClassFieldType::GetClassToken(m_spSH, m_idModule, tokConst, &mid, &tokClass) );
                    IfFailGo( m_spSH->CreateClassType( mid, tokClass, ppConstraints + iConstOut ) );
                    iConstOut++;
                    break;
                }
            case mdtTypeDef:
                {
                    IfFailGo( m_spSH->CreateClassType( m_idModule, tokConst, ppConstraints + iConstOut ) );
                    iConstOut++;
                    break;
                }
            case mdtTypeSpec:
                {
                    PCCOR_SIGNATURE pvSig;
                    ULONG cbSig;
                    DWORD cb = 0;
                    DWORD dwElementType;

                    IfFailGo( pMetadata2->GetTypeSpecFromToken( tokConst, &pvSig, &cbSig) );

                    cb += CorSigUncompressData(&(pvSig[cb]), &dwElementType);

                    IfFailGo( m_spSH->CreateType( pvSig, cbSig, m_idModule, mdMethodDefNil, m_pGenScope, ppConstraints + iConstOut ) );

                    iConstOut++;

                    break;
                }
            default:
                {
                    ASSERT(!"Bad constraint token");
                }
        }
    }

    *pcConstraints = iConstOut;

Error:

    METHOD_EXIT( CDebugGenericParamFieldType::GetConstraints, hr );

    DELETERG(rgParamConsts);

    return hr;
}
```

## <a name="see-also"></a>Voir aussi
- [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)
