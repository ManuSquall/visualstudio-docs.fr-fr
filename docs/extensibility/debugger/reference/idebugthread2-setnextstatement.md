---
description: Définit le pointeur d’instruction actuel sur le contexte de code donné.
title: 'IDebugThread2 :: SetNextStatement | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::SetNextStatement
helpviewer_keywords:
- IDebugThread2::SetNextStatement
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5dd6bd027a9938b7dce855742cc351180498bb8b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081163"
---
# <a name="idebugthread2setnextstatement"></a>IDebugThread2::SetNextStatement
Définit le pointeur d’instruction actuel sur le contexte de code donné.

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
Réservé à une utilisation ultérieure ; défini sur une valeur null.

`pCodeContext`\
dans Objet [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) qui décrit l’emplacement du code sur le point d’être exécuté et son contexte.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur. Le tableau suivant présente d’autres valeurs possibles.

|Valeur|Description|
|-----------|-----------------|
|E_CANNOT_SET_NEXT_STATEMENT_ON_NONLEAF_FRAME|L’instruction suivante ne peut pas être dans un frame de pile plus profondément sur la pile de frames.|
|E_CANNOT_SETIP_TO_DIFFERENT_FUNCTION|L’instruction suivante n’est associée à aucune image dans la pile.|
|E_CANNOT_SET_NEXT_STATEMENT_ON_EXCEPTION|Certains moteurs de débogage ne peuvent pas définir l’instruction suivante après une exception.|

## <a name="remarks"></a>Notes
 Le pointeur d’instruction indique l’instruction ou l’instruction suivante à exécuter. Cette méthode est utilisée pour effectuer une nouvelle tentative sur une ligne de code source ou pour forcer l’exécution à continuer dans une autre fonction, par exemple.

## <a name="see-also"></a>Voir aussi
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
