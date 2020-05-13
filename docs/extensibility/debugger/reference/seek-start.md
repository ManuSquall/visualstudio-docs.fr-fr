---
title: SEEK_START Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SEEK_START
helpviewer_keywords:
- SEEK_START enumeration
ms.assetid: 55bd8901-626e-428b-a263-23b14417f4c6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca1c38027123ca5147a6a7ab1fa6a3f92966409a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713601"
---
# <a name="seek_start"></a>SEEK_START
Spécifie la position à partir de laquelle commencer à chercher dans un flux de démontage.

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
 Commence à chercher au début du document actuel.

 `SEEK_START_END`\
 Commence à chercher à la fin du document actuel.

 `SEEK_START_CURRENT`\
 Commence à chercher à la position actuelle du document actuel.

 `SEEK_START_CODECONTEXT`\
 Commence à chercher dans le contexte de code donné du document actuel.

 `SEEK_START_CODELOCID`\
 Commence à chercher à l’identifiant de localisation de code donné. Les identifiants de localisation du code sont obtenus en appelant [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md).

## <a name="remarks"></a>Notes
 Passé comme un argument à la méthode [Seek.](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
- [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)
