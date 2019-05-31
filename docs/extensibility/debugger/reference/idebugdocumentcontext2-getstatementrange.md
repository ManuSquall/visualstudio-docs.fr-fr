---
title: IDebugDocumentContext2::GetStatementRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetStatementRange
helpviewer_keywords:
- IDebugDocumentContext2::GetStatementRange
ms.assetid: bc94851a-0ec4-47ea-99c7-0a585e54e726
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6ef4dae20a69fefcb67240e82999bdf2798d56e5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335299"
---
# <a name="idebugdocumentcontext2getstatementrange"></a>IDebugDocumentContext2::GetStatementRange
Obtient la plage d’instruction de fichier du contexte de document.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetStatementRange(
    TEXT_POSITION* pBegPosition,
    TEXT_POSITION* pEndPosition
);
```

```csharp
int GetStatementRange(
    TEXT_POSITION[] pBegPosition,
    TEXT_POSITION[] pEndPosition
);
```

## <a name="parameters"></a>Paramètres
`pBegPosition`\
[in, out] Un [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) structure est remplie avec la position de départ. Définissez cet argument à une valeur null si cette information n’est pas nécessaire.

`pEndPosition`\
[in, out] Un [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) structure est remplie avec la position de fin. Définissez cet argument à une valeur null si cette information n’est pas nécessaire.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
Une plage de l’instruction est la plage des lignes qui ont contribué le code auquel ce contexte de document fait référence.

Pour obtenir la plage de code source (y compris les commentaires) dans ce contexte de document, appelez le [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md) (méthode).

## <a name="example"></a>Exemple
L’exemple suivant montre comment implémenter cette méthode pour une simple `CDebugContext` objet qui expose le [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) interface. Cet exemple remplit la position de fin uniquement si la position de début n’est pas une valeur null.

```cpp
HRESULT CDebugContext::GetStatementRange(TEXT_POSITION* pBegPosition,
                                         TEXT_POSITION* pEndPosition)
{
    HRESULT hr;

    // Check for a valid beginning position argument pointer.
    if (pBegPosition)
    {
        // Copy the member TEXT_POSITION into the local pBegPosition.
        memcpy(pBegPosition, &m_pos, sizeof (TEXT_POSITION));

        // Check for a valid ending position argument pointer.
        if (pEndPosition)
        {
            // Copy the member TEXT_POSITION into the local pEndPosition.
            memcpy(pEndPosition, &m_pos, sizeof (TEXT_POSITION));
        }
        hr = S_OK;
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
- [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
