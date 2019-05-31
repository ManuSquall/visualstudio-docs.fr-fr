---
title: SEEK_START | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SEEK_START
helpviewer_keywords:
- SEEK_START enumeration
ms.assetid: 55bd8901-626e-428b-a263-23b14417f4c6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: de4aa0214ab97c330ddfb689076a2c378c4d227a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66329306"
---
# <a name="seekstart"></a>SEEK_START
Spécifie la position à partir duquel commencer la recherche dans un flux de code machine.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_SEEK_START { 
   SEEK_START_BEGIN       = 0x0001,
   SEEK_START_END         = 0x0002,
   SEEK_START_CURRENT     = 0x0003,
   SEEK_START_CODECONTEXT = 0x0004,
   SEEK_START_CODELOCID   = 0x0005
};
typedef DWORD SEEK_START;
```

```csharp
public enum enum_SEEK_START { 
   SEEK_START_BEGIN       = 0x0001,
   SEEK_START_END         = 0x0002,
   SEEK_START_CURRENT     = 0x0003,
   SEEK_START_CODECONTEXT = 0x0004,
   SEEK_START_CODELOCID   = 0x0005
};
```

## <a name="fields"></a>Champs
 `SEEK_START_BEGIN`\
 Démarre la recherche au début du document actif.

 `SEEK_START_END`\
 Démarre la recherche à la fin du document actif.

 `SEEK_START_CURRENT`\
 Démarre la recherche à la position actuelle du document actif.

 `SEEK_START_CODECONTEXT`\
 Démarre la recherche dans le contexte de code donné du document actif.

 `SEEK_START_CODELOCID`\
 Démarre la recherche à l’identificateur d’emplacement de code donné. Identificateurs d’emplacement de code sont obtenus en appelant [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md).

## <a name="remarks"></a>Notes
 Passé en tant qu’argument à la [recherche](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) (méthode).

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
- [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)