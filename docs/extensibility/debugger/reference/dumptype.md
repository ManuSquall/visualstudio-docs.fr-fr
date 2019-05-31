---
title: DUMPTYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DUMPTYPE
helpviewer_keywords:
- DUMPTYPE enumeration
ms.assetid: ea8160db-8732-4056-a1d7-892ef72da71e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7edb3129733aec29bb5eda64d388024bec4d5ece
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318189"
---
# <a name="dumptype"></a>DUMPTYPE
Spécifie la quantité d’état d’un programme (par exemple, les threads en cours d’exécution, les frames de pile et adresse d’instruction en cours) pour vider.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_DUMPTYPE {
    DUMP_MINIDUMP = 0,
    DUMP_FULLDUMP = 1
};
typedef DWORD DUMPTYPE;
```

```csharp
public enum enum_DUMPTYPE {
    DUMP_MINIDUMP = 0,
    DUMP_FULLDUMP = 1
};
```

## <a name="fields"></a>Champs
`DUMP_MINIDUMP`\
Spécifie un fichier de vidage petit, plus compact.

`DUMP_FULLDUMP`\
Spécifie un vidage volumineux et complet.

## <a name="remarks"></a>Notes
Passé en tant qu’argument à la [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md) (méthode).

## <a name="requirements"></a>Configuration requise
En-tête : msdbg.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)
