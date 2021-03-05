---
description: Spécifie le type de nom d’hôte.
title: GETHOSTNAME_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- GETHOSTNAME_TYPE
helpviewer_keywords:
- GETHOSTNAME_TYPE enumeration
ms.assetid: 2be92bea-8133-412b-9015-1833baf16e1b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3354bdbceeac796e2761bb83a5d860ca8a716315
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150781"
---
# <a name="gethostname_type"></a>GETHOSTNAME_TYPE
Spécifie le type de nom d’hôte.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_GETHOSTNAME_TYPE {
    GHN_FRIENDLY_NAME = 0,
    GHN_FILE_NAME     = 1
};
typedef DWORD GETHOSTNAME_TYPE;
```

```csharp
public enum enum_GETHOSTNAME_TYPE {
    GHN_FRIENDLY_NAME = 0,
    GHN_FILE_NAME     = 1
};
```

## <a name="fields"></a>Champs
`GHN_FRIENDLY_NAME`\
Spécifie un nom convivial de l’hôte.

`GHN_FILE_NAME`\
Spécifie un nom de fichier de l’hôte.

## <a name="remarks"></a>Notes
Ces valeurs sont passées en tant qu’arguments à la méthode [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) pour récupérer un nom d’hôte dans différents formats.

## <a name="requirements"></a>Configuration requise
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)
