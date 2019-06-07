---
title: METADATA_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3d608e4e9bf9987eb1dd430a9e22660c1da6a90a
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66746701"
---
# <a name="metadatatype"></a>METADATA_TYPE
Cette structure spécifie des informations sur un type de champ extraites à partir des métadonnées.

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
 ID de l’application d'où provenance le symbole. Cela est utilisé pour identifier de manière unique une instance de l’application.

 `guidModule`\
 Le GUID du module qui contient ce champ.

 `tokClass`\
 ID de jeton de métadonnées de ce type.

 [C++] `_mdToken` est un `typedef` pour 32 bits `int`.

## <a name="remarks"></a>Notes
 Cette structure apparaît dans le cadre de l’union dans le [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) structure lorsque le `dwKind` champ la `TYPE_INFO` structure est définie sur `TYPE_KIND_METADATA` (une valeur comprise entre le [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) énumération).

 Le `tokClass` valeur est un jeton de métadonnées qui identifie un type. Pour plus d’informations sur la façon d’interpréter les bits de poids fort de l’ID de jeton de métadonnées, consultez la `CorTokenType` énumération dans le fichier corhdr.h dans le SDK .NET Framework.

## <a name="requirements"></a>Configuration requise
 En-tête : sh.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)