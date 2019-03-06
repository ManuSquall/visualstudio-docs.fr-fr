---
title: MODULE_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO_FLAGS
helpviewer_keywords:
- MODULE_INFO_FLAGS enumeration
ms.assetid: e22d3723-b4d4-4524-8a2f-3adb55bbd273
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6db802fba0d6cd6b6f9b91dd40f6046491fb1f2b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56688873"
---
# <a name="moduleinfoflags"></a>MODULE_INFO_FLAGS
Spécifie l’état de symboles pour un module.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_MODULE_INFO_FLAGS {
   MIF_SYMBOLS_LOADED = 0x0001
};
typedef DWORD MODULE_INFO_FLAGS;
```

```csharp
public enum enum_MODULE_INFO_FLAGS {
   MIF_SYMBOLS_LOADED = 0x0001
};
```

## <a name="members"></a>Membres
 MIF_SYMBOLS_LOADED au moins un jeu de symboles a été chargé par le module (sinon aucun symbole n’a été chargé).

## <a name="remarks"></a>Notes
 Cette valeur est retournée par la [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) (méthode).

## <a name="requirements"></a>Spécifications
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)