---
description: Obtient la plage de codes source de ce contexte de document.
title: 'IDebugDocumentContext2 :: GetSourceRange, | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetSourceRange
helpviewer_keywords:
- IDebugDocumentContext2::GetSourceRange
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a66f1b99793b1c8fa8036771d7815f95a395462a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066592"
---
# <a name="idebugdocumentcontext2getsourcerange"></a>IDebugDocumentContext2::GetSourceRange
Obtient la plage de codes source de ce contexte de document.

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
[in, out] Structure [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) qui est remplie avec la position de départ. Définissez cet argument sur une valeur null si cette information n’est pas nécessaire.

`pEndPosition`\
[in, out] Structure [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) qui est remplie avec la position de fin. Définissez cet argument sur une valeur null si cette information n’est pas nécessaire.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Une plage source est la plage entière du code source, de l’instruction actuelle jusqu’à juste après l’instruction précédente qui a contribué au code. La plage source est généralement utilisée pour mélanger des instructions sources, y compris des commentaires, avec du code dans la fenêtre Code machine.

 Pour obtenir la plage uniquement pour les instructions de code contenues dans ce contexte de document, appelez la méthode [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) .

## <a name="see-also"></a>Voir aussi
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
