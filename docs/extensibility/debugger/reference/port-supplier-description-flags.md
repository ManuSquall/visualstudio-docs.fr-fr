---
title: PORT_SUPPLIER_DESCRIPTION_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- PORT_SUPPLIER_DESCRIPTION_FLAGS enumeration
ms.assetid: 5acee0ee-3a20-41c9-a7dc-0dadae6a5ba5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5a0241265f05f616b8810f84c1a82689a8604237
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212735"
---
# <a name="portsupplierdescriptionflags"></a>PORT_SUPPLIER_DESCRIPTION_FLAGS

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
Si sélectionné, l’icône d’avertissement s’affichera dans l’interface utilisateur.

## <a name="remarks"></a>Notes

Cette énumération est retournée par la [GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md) (méthode).

## <a name="requirements"></a>Configuration requise

En-tête : Msdbg.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi

- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)
