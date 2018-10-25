---
title: OBJECT_TYPE | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- OBJECT_TYPE
helpviewer_keywords:
- OBJECT_TYPE enumeration
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c49036d66310be7774f3f8d36215aca4bedd7582
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49922833"
---
# <a name="objecttype"></a>OBJECT_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Spécifie le type d’un objet à partir de l’évaluateur d’expression.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
enum enum_OBJECT_TYPE {   
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
public enum enum_OBJECT_TYPE {   
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
  
## <a name="members"></a>Membres  
 OBJECT_TYPE_BOOLEAN  
 Indique que l’objet est une valeur booléenne.  
  
 OBJECT_TYPE_CHAR  
 Indique que l’objet est un caractère.  
  
 OBJECT_TYPE_I1  
 Indique que l’objet est un entier signé de 1 octet.  
  
 OBJECT_TYPE_U1  
 Indique que l’objet est un entier non signé sur un octet.  
  
 OBJECT_TYPE_I2  
 Indique que l’objet est un entier signé de 2 octets.  
  
 OBJECT_TYPE_U2  
 Indique que l’objet est un entier non signé de 2 octets.  
  
 OBJECT_TYPE_I4  
 Indique que l’objet est un entier signé de 4 octets.  
  
 OBJECT_TYPE_U4  
 Indique que l’objet est un entier non signé de 4 octets.  
  
 OBJECT_TYPE_I8  
 Indique que l’objet est un entier signé de 8 octets.  
  
 OBJECT_TYPE_U8  
 Indique que l’objet est un entier non signé de 8 octets.  
  
 OBJECT_TYPE_R4  
 Indique que l’objet est un nombre à virgule flottante de 4 octets.  
  
 OBJECT_TYPE_R8  
 Indique que l’objet est un nombre à virgule flottante de 8 octets.  
  
 OBJECT_TYPE_OBJECT  
 Indique que l’objet est un objet.  
  
 OBJECT_TYPE_NULL  
 Indique que l’objet est NULL.  
  
 OBJECT_TYPE_CLASS  
 Indique que l’objet est une classe.  
  
## <a name="remarks"></a>Notes  
 Passé en tant qu’argument à la [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md) et [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md) méthodes.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : ee.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)   
 [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)

