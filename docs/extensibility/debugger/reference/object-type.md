---
title: OBJECT_TYPE Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- OBJECT_TYPE
helpviewer_keywords:
- OBJECT_TYPE enumeration
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4ffb85a14e42dd57c345481285eb1f776b3866d3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714129"
---
# <a name="object_type"></a>Object_Type
Spécifie le type d’objet de l’évaluateur d’expression.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_OBJECT_TYPE { 
   OBJECT_TYPE_BOOLEAN = 0x0,
   OBJECT_TYPE_CHAR    = 0x1,
   OBJECT_TYPE_I1      = 0x2,
   OBJECT_TYPE_U1      = 0x3,
   OBJECT_TYPE_I2      = 0x4,
   OBJECT_TYPE_U2      = 0x5,
   OBJECT_TYPE_I4      = 0x6,
   OBJECT_TYPE_U4      = 0x7,
   OBJECT_TYPE_I8      = 0x8,
   OBJECT_TYPE_U8      = 0x9,
   OBJECT_TYPE_R4      = 0xa,
   OBJECT_TYPE_R8      = 0xb,
   OBJECT_TYPE_OBJECT  = 0xc,
   OBJECT_TYPE_NULL    = 0xd,
   OBJECT_TYPE_CLASS   = 0xe
};
typedef DWORD OBJECT_TYPE;
```

```csharp
public enum enum_OBJECT_TYPE { 
   OBJECT_TYPE_BOOLEAN = 0x0,
   OBJECT_TYPE_CHAR    = 0x1,
   OBJECT_TYPE_I1      = 0x2,
   OBJECT_TYPE_U1      = 0x3,
   OBJECT_TYPE_I2      = 0x4,
   OBJECT_TYPE_U2      = 0x5,
   OBJECT_TYPE_I4      = 0x6,
   OBJECT_TYPE_U4      = 0x7,
   OBJECT_TYPE_I8      = 0x8,
   OBJECT_TYPE_U8      = 0x9,
   OBJECT_TYPE_R4      = 0xa,
   OBJECT_TYPE_R8      = 0xb,
   OBJECT_TYPE_OBJECT  = 0xc,
   OBJECT_TYPE_NULL    = 0xd,
   OBJECT_TYPE_CLASS   = 0xe
};
```

## <a name="fields"></a>Champs
 `OBJECT_TYPE_BOOLEAN`\
 Indique que l’objet est un Boolean.

 `OBJECT_TYPE_CHAR`\
 Indique que l’objet est un personnage.

 `OBJECT_TYPE_I1`\
 Indique que l’objet est un intégrer signé un par un.

 `OBJECT_TYPE_U1`\
 Indique que l’objet est un insigné one-byte.

 `OBJECT_TYPE_I2`\
 Indique que l’objet est un intégrer signé à deux parse.

 `OBJECT_TYPE_U2`\
 Indique que l’objet est un integer non signé à deux étages.

 `OBJECT_TYPE_I4`\
 Indique que l’objet est un intégrer signé à quatre byte.

 `OBJECT_TYPE_U4`\
 Indique que l’objet est un intégré non signé à quatre.

 `OBJECT_TYPE_I8`\
 Indique que l’objet est un intégrer signé à huit.

 `OBJECT_TYPE_U8`\
 Indique que l’objet est un intégré non signé à huit.

 `OBJECT_TYPE_R4`\
 Indique que l’objet est un numéro de quatre points flottants.

 `OBJECT_TYPE_R8`\
 Indique que l’objet est un numéro flottant de huit points.

 `OBJECT_TYPE_OBJECT`\
 Indique que l’objet est un objet.

 `OBJECT_TYPE_NULL`\
 Indique que l’objet est NULL.

 `OBJECT_TYPE_CLASS`\
 Indique que l’objet est une classe.

## <a name="remarks"></a>Notes
 Passé comme un argument aux méthodes [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md) et [CreateArrayObject.](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)

## <a name="requirements"></a>Spécifications
 En-tête: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)
- [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)
