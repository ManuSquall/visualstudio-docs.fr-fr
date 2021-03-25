---
description: Spécifie la position à partir de laquelle commencer la recherche dans un flux de code machine.
title: SEEK_START | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SEEK_START
helpviewer_keywords:
- SEEK_START enumeration
ms.assetid: 55bd8901-626e-428b-a263-23b14417f4c6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a15635f2cf56f3be1e9955af4ee79782ed3c85fa
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061522"
---
# <a name="seek_start"></a>SEEK_START
Spécifie la position à partir de laquelle commencer la recherche dans un flux de code machine.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_SEEK_START { 
   SEEK_START_BEGIN       = 0x0001,
   SEEK_START_END         = 0x0002,
   SEEK_START_CURRENT     = 0x0003,
   SEEK_START_CODECONTEXT = 0x0004,
   SEEK_START_CODELOCID   = 0x0005
};
typedef DWORD SEEK_START;
```

```csharp
public enum enum_SEEK_START { 
   SEEK_START_BEGIN       = 0x0001,
   SEEK_START_END         = 0x0002,
   SEEK_START_CURRENT     = 0x0003,
   SEEK_START_CODECONTEXT = 0x0004,
   SEEK_START_CODELOCID   = 0x0005
};
```

## <a name="fields"></a>Champs
 `SEEK_START_BEGIN`\
 Commence la recherche au début du document actif.

 `SEEK_START_END`\
 Commence la recherche à la fin du document actif.

 `SEEK_START_CURRENT`\
 Commence la recherche à la position actuelle du document actif.

 `SEEK_START_CODECONTEXT`\
 Commence la recherche au niveau du contexte de code donné du document actif.

 `SEEK_START_CODELOCID`\
 Commence la recherche à l’identificateur de l’emplacement du code donné. Les identificateurs d’emplacement de code sont obtenus en appelant [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md).

## <a name="remarks"></a>Notes
 Passé comme argument à la méthode [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) .

## <a name="requirements"></a>Spécifications
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
- [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)
