---
description: Récupère une liste des chemins de code pour une position donnée dans un fichier source.
title: 'IDebugProgram2 :: EnumCodePaths | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodePaths
helpviewer_keywords:
- IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 057089c8c7b68fd1109c31bbfc0014f49a71368c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076041"
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
Récupère une liste des chemins de code pour une position donnée dans un fichier source.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumCodePaths( 
   LPCOLESTR            pszHint,
   IDebugCodeContext2*  pStart,
   IDebugStackFrame2*   pFrame,
   BOOL                 fSource,
   IEnumCodePaths2**    ppEnum,
   IDebugCodeContext2** ppSafety
);
```

```csharp
int EnumCodePaths( 
   string                 pszHint,
   IDebugCodeContext2     pStart,
   IDebugStackFrame2      pFrame,
   Int                    fSource,
   out IEnumCodePaths2    ppEnum,
   out IDebugCodeContext2 ppSafety
);
```

## <a name="parameters"></a>Paramètres
`pszHint`\
dans Mot situé sous le curseur dans la vue **source ou code** **machine** de l’IDE.

`pStart`\
dans Objet [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) qui représente le contexte de code actuel.

`pFrame`\
dans Objet [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) qui représente le frame de pile associé au point d’arrêt actuel.

`fSource`\
dans Valeur différente de zéro ( `TRUE` ) si dans la vue **source** , ou zéro ( `FALSE` ) dans la vue code **machine** .

`ppEnum`\
à Retourne un objet [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) contenant une liste des chemins de code.

`ppSafety`\
à Retourne un objet [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) qui représente un contexte de code supplémentaire à définir comme point d’arrêt si le chemin d’accès au code choisi est ignoré. Cela peut se produire dans le cas d’une expression booléenne de court-circuit, par exemple.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Un chemin d’accès de code décrit le nom d’une méthode ou d’une fonction qui a été appelée pour atteindre le point actuel dans l’exécution du programme. Une liste de chemins de code représente la pile des appels.

## <a name="see-also"></a>Voir aussi
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
