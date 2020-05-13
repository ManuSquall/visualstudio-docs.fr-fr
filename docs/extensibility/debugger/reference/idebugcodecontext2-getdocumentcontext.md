---
title: IDebugCodeContext2::GetDocumentContext Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetDocumentContext
helpviewer_keywords:
- IDebugCodeContext2::GetDocumentContext
ms.assetid: d552cc92-963f-43c1-949f-ae6b63a427b8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 46510ce794ea30fdd365a77007b962a1eafd5d31
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734345"
---
# <a name="idebugcodecontext2getdocumentcontext"></a>IDebugCodeContext2::GetDocumentContext
Obtient le contexte de document qui correspond à ce contexte de code. Le contexte du document représente une position dans le fichier source qui correspond au code source qui a généré cette instruction.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetDocumentContext( 
   IDebugDocumentContext2** ppSrcCxt
);
```

```csharp
int GetDocumentContext( 
   out IDebugDocumentContext2 ppSrcCxt
);
```

## <a name="parameters"></a>Paramètres
`ppSrcCxt`\
[out] Retourne l’objet [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) qui correspond au contexte du code. Si `S_OK` elle est retournée, les`null`ths doivent être non- .

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur. Un moteur de débogé doit `E_FAIL` retourner `out` un `null` code de défaillance tel que lorsque le paramètre est tel que lorsque le contexte du code n’a pas de position source associée.

## <a name="remarks"></a>Notes
 En général, le contexte du document peut être considéré comme une position dans un fichier source alors que le contexte du code est une position d’instruction de code dans un flux d’exécution.

## <a name="see-also"></a>Voir aussi
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
