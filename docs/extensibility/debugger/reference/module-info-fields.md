---
description: Spécifie les indicateurs pour les informations du module de débogage.
title: MODULE_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4c530caa530a230dc0fc0344a31e0ab7793f336f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079772"
---
# <a name="module_info_fields"></a>MODULE_INFO_FIELDS
Spécifie les indicateurs pour les informations du module de débogage.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_MODULE_INFO_FIELDS { 
   MIF_NONE              = 0x0000,
   MIF_NAME              = 0x0001,
   MIF_URL               = 0x0002,
   MIF_VERSION           = 0x0004,
   MIF_DEBUGMESSAGE      = 0x0008,
   MIF_LOADADDRESS       = 0x0010,
   MIF_PREFFEREDADDRESS  = 0x0020,
   MIF_SIZE              = 0x0040,
   MIF_LOADORDER         = 0x0080,
   MIF_TIMESTAMP         = 0x0100,
   MIF_URLSYMBOLLOCATION = 0x0200,
   MIF_FLAGS             = 0x0400,
   MIF_ALLFIELDS         = 0x07ff
};
typedef DWORD MODULE_INFO_FIELDS;
```

```csharp
public enum enum_MODULE_INFO_FIELDS { 
   MIF_NONE              = 0x0000,
   MIF_NAME              = 0x0001,
   MIF_URL               = 0x0002,
   MIF_VERSION           = 0x0004,
   MIF_DEBUGMESSAGE      = 0x0008,
   MIF_LOADADDRESS       = 0x0010,
   MIF_PREFFEREDADDRESS  = 0x0020,
   MIF_SIZE              = 0x0040,
   MIF_LOADORDER         = 0x0080,
   MIF_TIMESTAMP         = 0x0100,
   MIF_URLSYMBOLLOCATION = 0x0200,
   MIF_FLAGS             = 0x0400,
   MIF_ALLFIELDS         = 0x07ff
};
```

## <a name="fields"></a>Champs
 `MIF_NONE`\
 Initialisez/n’utilisez aucun des champs de la structure.

 `MIF_NAME`\
 Initialisez/utilisez le `m_bstrName` champ de la structure [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) .

 `MIF_URL`\
 Initialisez/utilisez le `m_bstrUrl` champ de la `MODULE_INFO` structure.

 `MIF_VERSION`\
 Initialisez/utilisez le `m_bstrVersion` champ de la `MODULE_INFO` structure.

 `MIF_DEBUGMESSAGE`\
 Initialisez/utilisez le `m_bstrDebugMessage` champ de la `MODULE_INFO` structure.

 `MIF_LOADADDRESS`\
 Initialisez/utilisez le `m_addrLoadAddress` champ de la `MODULE_INFO` structure.

 `MIF_PREFFEREDADDRESS`\
 Initialisez/utilisez le `m_addrPreferredLoadAddress` champ de la `MODULE_INFO` structure.

 `MIF_SIZE`\
 Initialisez/utilisez le `m_dwSize` champ de la `MODULE_INFO` structure.

 `MIF_LOADORDER`\
 Initialisez/utilisez le `m_dwLoadOrder` champ de la `MODULE_INFO` structure.

 `MIF_TIMESTAMP`\
 Initialisez/utilisez le `m_TimeStamp` champ de la `MODULE_INFO` structure.

 `MIF_URLSYMBOLLOCATION`\
 Initialisez/utilisez le `m_bstrUrlSymbolLocation` champ de la `MODULE_INFO` structure.

 `MIF_FLAGS`\
 Initialisez/utilisez le `m_dwModuleFlags` champ de la `MODULE_INFO` structure.

 `MIF_ALLFIELDS`\
 Initialisez/Utilisez tous les champs de la `MODULE_INFO` structure.

## <a name="remarks"></a>Notes
 Ces valeurs sont passées en tant qu’arguments à la méthode [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) pour indiquer les champs de la structure [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) qui doivent être initialisés.

 Ces valeurs sont également utilisées dans la `MODULE_INFO` structure pour indiquer les champs qui sont utilisés et valides.

 Ces indicateurs peuvent être combinés avec une opération au niveau du bit `OR` .

## <a name="requirements"></a>Spécifications
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
