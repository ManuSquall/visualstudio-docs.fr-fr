---
description: Retourne le contexte de code représentant un emplacement si une opération de déroulement de la pile s’est produite.
title: 'IDebugStackFrame3 :: GetUnwindCodeContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3::GetUnwindCodeContext
helpviewer_keywords:
- IDebugStackFrame3::GetUnwindCodeContext method
ms.assetid: b25f7e7d-2b24-48e4-93b3-829e61d73ebf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1ef0a66729a2e9061a9e71ec0634a65999b55bf2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159729"
---
# <a name="idebugstackframe3getunwindcodecontext"></a>IDebugStackFrame3::GetUnwindCodeContext
Retourne le contexte de code représentant un emplacement si une opération de déroulement de la pile s’est produite.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetUnwindCodeContext(
   IDebugCodeContext2 **ppCodeContext
);
```

```csharp
int GetUnwindCodeContext(
   out IDebugCodeContext2 ppCodeContext
);
```

## <a name="parameters"></a>Paramètres
`ppCodeContext`\
à Retourne un objet [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) qui représente l’emplacement du contexte de code si un déroulement de la pile s’est produit.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Même si cette méthode peut retourner un contexte de code pour l’emplacement après un déroulement de pile, cela ne signifie pas nécessairement que le déroulement de la pile peut réellement se produire dans le frame de pile actuel.

## <a name="see-also"></a>Voir aussi
- [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
