---
title: IDebugDocumentContext2::GetName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetName
helpviewer_keywords:
- IDebugDocumentContext2::GetName
ms.assetid: 546c5b2e-f166-4edb-9e61-57d797ca98a1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2c770c339399aaf01fee9598318c94266a391c55
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56705727"
---
# <a name="idebugdocumentcontext2getname"></a>IDebugDocumentContext2::GetName
Obtient le nom affichable du document qui contient le contexte de ce document.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetName(
    GETNAME_TYPE gnType,
    BSTR*        pbstrFileName
);
```

```csharp
int GetName(
    enum_GETNAME_TYPE  gnType,
    out string         pbstrFileName
);
```

#### <a name="parameters"></a>Paramètres
`gnType`

 [in] Une valeur comprise entre le [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) énumération qui spécifie le type de nom à retourner.

`pbstrFileName`

 [out] Retourne le nom du fichier.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
Cette méthode transfère généralement l’appel à la [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md) (méthode), sauf si le contexte de document est écrites pour stocker le nom du document (comme le montrent les exemple).

## <a name="example"></a>Exemple
L’exemple suivant montre comment implémenter cette méthode pour une simple `CDebugContext` objet qui expose le [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) interface.

```cpp
HRESULT CDebugContext::GetName(GETNAME_TYPE gnType, BSTR* pbstrFileName)
{
    HRESULT hr;

    // Check for a valid file name argument.
    if (pbstrFileName)
    {
        *pbstrFileName = NULL;

        switch (gnType)
        {
            case GN_NAME:
            case GN_FILENAME:
            {
                // Copy the member file name into the local file name.
                *pbstrFileName = SysAllocString(m_sbstrFileName);
                // Check for successful copy.
                hr = (*pbstrFileName) ? S_OK : E_OUTOFMEMORY;
                break;
            }
            default:
            {
                hr = E_FAIL;
                break;
            }
        }
    }
    else
    {
        hr = E_INVALIDARG;
    }

    return hr;
}
```

## <a name="see-also"></a>Voir aussi
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)
