---
description: Spécifie l’unité d’étape pour l’exécution pas à pas.
title: STEPUNIT | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- STEPUNIT
helpviewer_keywords:
- STEPUNIT enumeration
ms.assetid: cb8441f2-f744-4e73-acfe-ae8542df9649
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f628039cdd9715d9463b0def9912da8f78ef6b84
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221884"
---
# <a name="stepunit"></a>STEPUNIT
Spécifie l’unité d’étape pour l’exécution pas à pas.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_STEPUNIT { 
   STEP_STATEMENT   = 0,
   STEP_LINE        = 1,
   STEP_INSTRUCTION = 2
};
typedef DWORD STEPUNIT;
```

```csharp
enum enum_STEPUNIT { 
   STEP_STATEMENT   = 0,
   STEP_LINE        = 1,
   STEP_INSTRUCTION = 2
};
```

## <a name="fields"></a>Champs
 `STEP_STATEMENT`\
 Étapes par instruction.

 `STEP_LINE`\
 Étapes par ligne.

 `STEP_INSTRUCTION`\
 Étapes par instruction.

## <a name="remarks"></a>Notes
 Passé comme argument à la méthode [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md) .

## <a name="requirements"></a>Spécifications
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Étape](../../../extensibility/debugger/reference/idebugprocess3-step.md)
