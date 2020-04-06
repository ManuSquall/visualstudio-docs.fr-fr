---
title: IDebugDocumentContext2::GetSourceRange ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetSourceRange
helpviewer_keywords:
- IDebugDocumentContext2::GetSourceRange
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 782cf230c38af77da09b49f69c093e2e95bf7199
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731798"
---
# <a name="idebugdocumentcontext2getsourcerange"></a>IDebugDocumentContext2::GetSourceRange
Obtient la plage de code source de ce contexte de document.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetSourceRange( 
   TEXT_POSITION* pBegPosition,
   TEXT_POSITION* pEndPosition
);
```

```csharp
int GetSourceRange( 
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
 Une plage source est toute la gamme de code source, de l’énoncé actuel à juste après la déclaration précédente qui a contribué au code. La plage source est généralement utilisée pour mélanger les relevés de source, y compris les commentaires, avec du code dans la fenêtre de démontage.

 Pour obtenir la plage pour seulement les instructions de code contenues dans ce contexte de document, appelez la méthode [GetStatementRange.](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)

## <a name="see-also"></a>Voir aussi
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
