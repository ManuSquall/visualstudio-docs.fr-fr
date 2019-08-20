---
title: IDebugCodeContext2::GetDocumentContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetDocumentContext
helpviewer_keywords:
- IDebugCodeContext2::GetDocumentContext
ms.assetid: d552cc92-963f-43c1-949f-ae6b63a427b8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a12838db0687fd7ebe20a5c576db0e06ece49107
ms.sourcegitcommit: 34807a6b6105ae7839adde8ff994c85182ad3aff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2019
ms.locfileid: "67342406"
---
# <a name="idebugcodecontext2getdocumentcontext"></a>IDebugCodeContext2::GetDocumentContext
Obtient le contexte de document qui correspond à ce contexte de code. Le contexte de document représente une position dans le fichier source qui correspond au code source qui a généré cette instruction.

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
[out] Retourne le [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) objet correspondant au contexte de code. Si `S_OK` est retourné, ths doit être non -`null`.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Un moteur de débogage doit retourner un code d’erreur tel que `E_FAIL` lorsque le `out` paramètre est `null` telles que lorsque le contexte de code n’a aucune position de la source associée.

## <a name="remarks"></a>Notes
 En règle générale, le contexte de document peut être considéré comme une position dans un fichier source pendant que le contexte de code est une position d’une instruction de code dans un flux d’exécution.

## <a name="see-also"></a>Voir aussi
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
