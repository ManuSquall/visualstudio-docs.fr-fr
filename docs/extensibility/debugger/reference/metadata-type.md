---
title: METADATA_TYPE Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: afe5ea128775c7be0e48035ab4c7e7d370c9d233
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714285"
---
# <a name="metadata_type"></a>METADATA_TYPE
Cette structure spécifie des informations sur un type de terrain tiré des métadonnées.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _tagTYPE_METADATA {
   ULONG32  ulAppDomainID;
   GUID     guidModule;
   _mdToken tokClass;
} METADATA_TYPE;
```

```csharp
public struct METADATA_TYPE {
   public uint ulAppDomainID;
   public Guid guidModule;
   public int  tokClass;
};
```

## <a name="parameters"></a>Paramètres
 `ulAppDomainID`\
 ID de l’application à partir de laquelle le symbole est venu. Ceci est utilisé pour identifier de façon unique un exemple de l’application.

 `guidModule`\
 Le GUID du module qui contient ce champ.

 `tokClass`\
 Les métadonnées jeton ID de ce type.

 [C] `_mdToken` est `typedef` un pour un 32 bits `int`.

## <a name="remarks"></a>Notes
 Cette structure fait partie du [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) syndicat dans la structure `dwKind` TYPE_INFO `TYPE_INFO` lorsque le `TYPE_KIND_METADATA` champ de la structure est fixé à (une valeur de [l’dwTYPE_KIND’énumération).](../../../extensibility/debugger/reference/dwtype-kind.md)

 La `tokClass` valeur est un jeton de métadonnées qui identifie uniquement un type. Pour plus de détails sur la façon d’interpréter les bits supérieurs de l’ID symbolique des métadonnées, voir l’énumération `CorTokenType` dans le fichier corhdr.h dans le cadre .NET SDK.

## <a name="requirements"></a>Spécifications
 En-tête: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
