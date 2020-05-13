---
title: IDebugThread2::SetNextStatement (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::SetNextStatement
helpviewer_keywords:
- IDebugThread2::SetNextStatement
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b390e5c021fa069ae3fb09eef1978caaf9cc8ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718654"
---
# <a name="idebugthread2setnextstatement"></a>IDebugThread2::SetNextStatement
Définit le pointeur d’instruction actuel dans le contexte du code donné.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetNextStatement ( 
   IDebugStackFrame2*  pStackFrame,
   IDebugCodeContext2* pCodeContext
);
```

```csharp
int SetNextStatement ( 
   IDebugStackFrame2  pStackFrame,
   IDebugCodeContext2 pCodeContext
);
```

## <a name="parameters"></a>Paramètres
`pStackFrame`\
Réservé à une utilisation future; d’une valeur nulle.

`pCodeContext`\
[dans] Un objet [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) qui décrit l’emplacement du code sur le point d’être exécuté et son contexte.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur. Le tableau suivant montre d’autres valeurs possibles.

|Valeur|Description|
|-----------|-----------------|
|E_CANNOT_SET_NEXT_STATEMENT_ON_NONLEAF_FRAME|La prochaine déclaration ne peut pas être dans un cadre de pile plus profond sur la pile de cadre.|
|E_CANNOT_SETIP_TO_DIFFERENT_FUNCTION|La déclaration suivante n’est associée à aucun cadre dans la pile.|
|E_CANNOT_SET_NEXT_STATEMENT_ON_EXCEPTION|Certains moteurs débogés ne peuvent pas définir la déclaration suivante après une exception.|

## <a name="remarks"></a>Notes
 Le pointeur d’instruction indique la prochaine instruction ou déclaration à exécuter. Cette méthode est utilisée pour retenter une ligne de code source ou pour forcer l’exécution à continuer dans une autre fonction, par exemple.

## <a name="see-also"></a>Voir aussi
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
