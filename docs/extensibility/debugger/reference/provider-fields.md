---
title: PROVIDER_FIELDS Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROVIDER_FIELDS
helpviewer_keywords:
- PROVIDER_FIELDS enumeration
ms.assetid: 39631545-2b0e-45b4-978b-d63656484b02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 37f64b455ab0331f9b8f08da1f29a3e2c1b82fdf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713786"
---
# <a name="provider_fields"></a>PROVIDER_FIELDS
Spécifie les propriétés associées à un fournisseur de programme.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_PROVIDER_FIELDS {
   PFIELD_PROGRAM_NODES       = 0x01,
   PFIELD_IS_DEBUGGER_PRESENT = 0x02
};
typedef DWORD PROVIDER_FIELDS;
```

```csharp
public enum enum_PROVIDER_FIELDS {
   PFIELD_PROGRAM_NODES       = 0x01,
   PFIELD_IS_DEBUGGER_PRESENT = 0x02
};
```

## <a name="fields"></a>Champs
 `PFIELD_PROGRAM_NODES`\
 Le `ProgramNodes` champ est valide.

 `PFIELD_IS_DEBUGGER_PRESENT`\
 Le `fIsDebuggerPresent` champ est valide.

## <a name="remarks"></a>Notes
 Ces valeurs sont `Fields` retournées dans le membre de la structure [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) pour indiquer quels champs de la structure ont été explicitement remplis.

 Ces valeurs peuvent être combinées avec un peu plus. `OR`

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
