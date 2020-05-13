---
title: IDebugDocumentContext2::GetStatementRange (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetStatementRange
helpviewer_keywords:
- IDebugDocumentContext2::GetStatementRange
ms.assetid: bc94851a-0ec4-47ea-99c7-0a585e54e726
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50e521d98f10477d56dfece30e20fd000b87b632
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731773"
---
# <a name="idebugdocumentcontext2getstatementrange"></a>IDebugDocumentContext2::GetStatementRange
Obtient la plage de relevé de fichiers du contexte du document.

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
[dans, dehors] Une structure [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) qui est remplie avec le poste de départ. Définissez cet argument à une valeur nulle si cette information n’est pas nécessaire.

`pEndPosition`\
[dans, dehors] Une structure [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) qui est remplie avec la position de fin. Définissez cet argument à une valeur nulle si cette information n’est pas nécessaire.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
Une plage de relevé est la plage des lignes qui ont contribué au code auquel le présent contexte de document se réfère.

Pour obtenir la plage de code source (y compris les commentaires) dans ce contexte de document, appelez la méthode [GetSourceRange.](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)

## <a name="example"></a>Exemple
L’exemple suivant montre comment implémenter cette méthode pour un objet simple `CDebugContext` qui expose [l’interface IDebugDocumentContext2.](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) Cet exemple ne remplit le poste de fin que si le poste de départ n’est pas une valeur nulle.

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
