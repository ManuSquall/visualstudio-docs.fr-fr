---
title: OBJECT_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- OBJECT_TYPE
helpviewer_keywords:
- OBJECT_TYPE enumeration
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 08d50e3d3ddda55a7ff0f3fea333c5408b02878a
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65461030"
---
# <a name="objecttype"></a>OBJECT_TYPE
Spécifie le type d’un objet à partir de l’évaluateur d’expression.

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
 Indique que l’objet est une valeur booléenne.

 `OBJECT_TYPE_CHAR`\
 Indique que l’objet est un caractère.

 `OBJECT_TYPE_I1`\
 Indique que l’objet est un entier signé de 1 octet.

 `OBJECT_TYPE_U1`\
 Indique que l’objet est un entier non signé sur un octet.

 `OBJECT_TYPE_I2`\
 Indique que l’objet est un entier signé de 2 octets.

 `OBJECT_TYPE_U2`\
 Indique que l’objet est un entier non signé de 2 octets.

 `OBJECT_TYPE_I4`\
 Indique que l’objet est un entier signé de 4 octets.

 `OBJECT_TYPE_U4`\
 Indique que l’objet est un entier non signé de 4 octets.

 `OBJECT_TYPE_I8`\
 Indique que l’objet est un entier signé de 8 octets.

 `OBJECT_TYPE_U8`\
 Indique que l’objet est un entier non signé de 8 octets.

 `OBJECT_TYPE_R4`\
 Indique que l’objet est un nombre à virgule flottante de 4 octets.

 `OBJECT_TYPE_R8`\
 Indique que l’objet est un nombre à virgule flottante de 8 octets.

 `OBJECT_TYPE_OBJECT`\
 Indique que l’objet est un objet.

 `OBJECT_TYPE_NULL`\
 Indique que l’objet est NULL.

 `OBJECT_TYPE_CLASS`\
 Indique que l’objet est une classe.

## <a name="remarks"></a>Notes
 Passé en tant qu’argument à la [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md) et [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md) méthodes.

## <a name="requirements"></a>Configuration requise
 En-tête : ee.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)
- [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)