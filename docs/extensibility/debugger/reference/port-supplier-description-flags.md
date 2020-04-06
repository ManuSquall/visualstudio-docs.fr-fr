---
title: PORT_SUPPLIER_DESCRIPTION_FLAGS Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- PORT_SUPPLIER_DESCRIPTION_FLAGS enumeration
ms.assetid: 5acee0ee-3a20-41c9-a7dc-0dadae6a5ba5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 26022098eb4233186a1442bde38fe4325accfdd1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713982"
---
# <a name="port_supplier_description_flags"></a>PORT_SUPPLIER_DESCRIPTION_FLAGS

Définit les métadonnées qui peuvent être récupérées sur un fournisseur de port.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_PORT_SUPPLIER_DESCRIPTION_FLAGS
{
    PSDFLAG_SHOW_WARNING_ICON = 0x1
};
typedef DWORD PORT_SUPPLIER_DESCRIPTION_FLAGS;
```

```csharp
public enum enum_PORT_SUPPLIER_DESCRIPTION_FLAGS
{
    PSDFLAG_SHOW_WARNING_ICON = 0x1
};
```

## <a name="fields"></a>Champs

`PSDFLAG_SHOW_WARNING_ICON`\
Si elle est sélectionnée, l’icône d’avertissement sera affichée dans l’interface utilisateur.

## <a name="remarks"></a>Notes

Cette énumération est retournée par la méthode [GetDescription.](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)

## <a name="requirements"></a>Spécifications

En-tête: Msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi

- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDescription (en)](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)
