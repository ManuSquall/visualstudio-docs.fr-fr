---
title: MODULE_INFO_FIELDS Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa64147738a916d44b6924f193860f74bd10a855
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714327"
---
# <a name="module_info_fields"></a>MODULE_INFO_FIELDS
Spécifie les drapeaux pour les informations du module de débogé.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_MODULE_INFO_FIELDS { 
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
public enum enum_MODULE_INFO_FIELDS { 
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
 Initialiser/utiliser aucun des champs de la structure.

 `MIF_NAME`\
 Initialiser/utiliser `m_bstrName` le champ dans la structure [MODULE_INFO.](../../../extensibility/debugger/reference/module-info.md)

 `MIF_URL`\
 Initialiser/utiliser `m_bstrUrl` le champ `MODULE_INFO` dans la structure.

 `MIF_VERSION`\
 Initialiser/utiliser `m_bstrVersion` le champ `MODULE_INFO` dans la structure.

 `MIF_DEBUGMESSAGE`\
 Initialiser/utiliser `m_bstrDebugMessage` le champ `MODULE_INFO` dans la structure.

 `MIF_LOADADDRESS`\
 Initialiser/utiliser `m_addrLoadAddress` le champ `MODULE_INFO` dans la structure.

 `MIF_PREFFEREDADDRESS`\
 Initialiser/utiliser `m_addrPreferredLoadAddress` le champ `MODULE_INFO` dans la structure.

 `MIF_SIZE`\
 Initialiser/utiliser `m_dwSize` le champ `MODULE_INFO` dans la structure.

 `MIF_LOADORDER`\
 Initialiser/utiliser `m_dwLoadOrder` le champ `MODULE_INFO` dans la structure.

 `MIF_TIMESTAMP`\
 Initialiser/utiliser `m_TimeStamp` le champ `MODULE_INFO` dans la structure.

 `MIF_URLSYMBOLLOCATION`\
 Initialiser/utiliser `m_bstrUrlSymbolLocation` le champ `MODULE_INFO` dans la structure.

 `MIF_FLAGS`\
 Initialiser/utiliser `m_dwModuleFlags` le champ `MODULE_INFO` dans la structure.

 `MIF_ALLFIELDS`\
 Initialiser/utiliser tous les champs `MODULE_INFO` de la structure.

## <a name="remarks"></a>Notes
 Ces valeurs sont transmises comme un argument à la méthode [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) pour indiquer quels domaines de la structure [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) doivent être parasécés.

 Ces valeurs sont également `MODULE_INFO` utilisées dans la structure pour indiquer quels champs sont utilisés et valides.

 Ces drapeaux peuvent être combinés avec un peu plus. `OR`

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
