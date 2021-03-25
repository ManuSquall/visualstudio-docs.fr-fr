---
description: Obtient le contexte de document qui décrit l’emplacement de cet événement.
title: 'IDebugCanStopEvent2 :: GetDocumentContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetDocumentContext
helpviewer_keywords:
- IDebugCanStopEvent2::GetDocumentContext
ms.assetid: 936a6c4e-30c5-4c7e-9ad5-910cc605a4b5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 44e1f2aa918547d8b3b0b1bea1940072fe2d8f84
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085076"
---
# <a name="idebugcanstopevent2getdocumentcontext"></a>IDebugCanStopEvent2::GetDocumentContext
Obtient le contexte de document qui décrit l’emplacement de cet événement.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetDocumentContext ( 
   IDebugDocumentContext2** ppDocCxt
);
```

```csharp
int GetDocumentContext ( 
   out IDebugDocumentContext2 ppDocCxt
);
```

## <a name="parameters"></a>Paramètres
`ppDocCxt`\
à Retourne l’interface [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) qui représente une position dans un document de fichier source correspondant à l’emplacement de code actuel.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 En règle générale, le contexte du document peut être considéré comme une position dans un fichier source.

 Pour obtenir le contexte de code, qui est orienté vers des instructions de code, appelez la méthode [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md) .

## <a name="see-also"></a>Voir aussi
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)
