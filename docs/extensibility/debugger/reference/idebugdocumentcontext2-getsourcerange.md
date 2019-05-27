---
title: IDebugDocumentContext2::GetSourceRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetSourceRange
helpviewer_keywords:
- IDebugDocumentContext2::GetSourceRange
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a535da1feb24dd0de69f76af451056f3d8335d8a
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66204631"
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
[in, out] Un [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) structure est remplie avec la position de départ. Définissez cet argument à une valeur null si cette information n’est pas nécessaire.

`pEndPosition`\
[in, out] Un [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) structure est remplie avec la position de fin. Définissez cet argument à une valeur null si cette information n’est pas nécessaire.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Une plage source est l’ensemble du code source, à l’arrière d’instruction en cours se termine juste après l’instruction précédente qui a contribué de code. La plage source est généralement utilisée pour le mélange d’instructions de la source, y compris les commentaires, avec du code dans la fenêtre code machine.

 Pour obtenir la plage pour simplement les instructions de code contenues dans ce contexte de document, appelez le [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) (méthode).

## <a name="see-also"></a>Voir aussi
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)