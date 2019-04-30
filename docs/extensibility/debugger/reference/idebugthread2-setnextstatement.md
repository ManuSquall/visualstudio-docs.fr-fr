---
title: IDebugThread2::SetNextStatement | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::SetNextStatement
helpviewer_keywords:
- IDebugThread2::SetNextStatement
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 896167d3655c5234f56f3b70e4369706250973c5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62915530"
---
# <a name="idebugthread2setnextstatement"></a>IDebugThread2::SetNextStatement
Définit le pointeur d’instruction en cours pour le contexte de code donné.

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

#### <a name="parameters"></a>Paramètres
 `pStackFrame` Réservé pour une utilisation ultérieure ; la valeur est une valeur null.

 `pCodeContext`

 [in] Un [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objet qui décrit l’emplacement du code sur le point d’être exécutée et son contexte.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Le tableau suivant présente les autres valeurs possibles.

|Value|Description|
|-----------|-----------------|
|E_CANNOT_SET_NEXT_STATEMENT_ON_NONLEAF_FRAME|L’instruction suivante ne peut pas être dans un frame de pile plus approfondie sur le frame de pile.|
|E_CANNOT_SETIP_TO_DIFFERENT_FUNCTION|L’instruction suivante n’est pas associée à n’importe quelle image dans la pile.|
|E_CANNOT_SET_NEXT_STATEMENT_ON_EXCEPTION|Certains moteurs de débogage ne peut pas définir l’instruction suivante après une exception.|

## <a name="remarks"></a>Notes
 Le pointeur d’instruction indique l’instruction ou l’instruction suivante à exécuter. Cette méthode est utilisée pour retenter une ligne de code source ou pour forcer l’exécution de passer dans une autre fonction, par exemple.

## <a name="see-also"></a>Voir aussi
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)