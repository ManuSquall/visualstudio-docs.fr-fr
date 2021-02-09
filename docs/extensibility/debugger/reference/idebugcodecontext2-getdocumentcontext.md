---
title: 'IDebugCodeContext2 :: GetDocumentContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetDocumentContext
helpviewer_keywords:
- IDebugCodeContext2::GetDocumentContext
ms.assetid: d552cc92-963f-43c1-949f-ae6b63a427b8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: eaac527149d3224370f04d9dec46123b59568ac1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928742"
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
à Retourne l’objet [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) qui correspond au contexte de code. Si `S_OK` est retourné, ce ne doit pas être `null` .

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur. Un moteur de débogage doit retourner un code d’échec, par exemple `E_FAIL` lorsque le `out` paramètre est `null` tel que lorsque le contexte de code n’a pas de position source associée.

## <a name="remarks"></a>Notes
 En règle générale, le contexte du document peut être considéré comme une position dans un fichier source, tandis que le contexte de code est la position d’une instruction de code dans un flux d’exécution.

## <a name="see-also"></a>Voir aussi
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
