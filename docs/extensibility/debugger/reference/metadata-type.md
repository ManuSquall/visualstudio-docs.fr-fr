---
description: La structure METADATA_TYPE spécifie des informations sur un type de champ extrait de métadonnées.
title: METADATA_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5a76e051e146985338564d497323b6232b35a4a1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079850"
---
# <a name="metadata_type"></a>METADATA_TYPE
Cette structure spécifie des informations sur un type de champ issu de métadonnées.

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
 ID de l’application à partir de laquelle le symbole a été obtenu. Cela permet d’identifier de manière unique une instance de l’application.

 `guidModule`\
 GUID du module qui contient ce champ.

 `tokClass`\
 ID de jeton de métadonnées de ce type.

 (C++) `_mdToken` est un `typedef` pour un 32 bits `int` .

## <a name="remarks"></a>Notes
 Cette structure apparaît dans le cadre de l’Union dans la structure [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) lorsque le `dwKind` champ de la `TYPE_INFO` structure a la valeur `TYPE_KIND_METADATA` (une valeur de l’énumération [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) ).

 La `tokClass` valeur est un jeton de métadonnées qui identifie de façon unique un type. Pour plus d’informations sur la façon d’interpréter les bits supérieurs de l’ID de jeton de métadonnées, consultez l' `CorTokenType` énumération dans le fichier corhdr. h dans le kit de développement logiciel (SDK) .NET Framework.

## <a name="requirements"></a>Spécifications
 En-tête : SH. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
