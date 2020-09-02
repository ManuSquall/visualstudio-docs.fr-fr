---
title: ADDRESS_KIND | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- ADDRESS_KIND
helpviewer_keywords:
- ADDRESS_KIND enumeration
ms.assetid: 3a12fbec-7088-4cf9-8f6f-ad8ddec6009a
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6152ff5f493134812916f28e0b908bf98ecdbb35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62561871"
---
# <a name="address_kind"></a>ADDRESS_KIND
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Spécifie les types d’adresses.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_ADDRESS_KIND {  
   ADDRESS_KIND_NATIVE                  = 0x0001,  
   ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,  
   ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,  
   ADDRESS_KIND_METADATA_METHOD         = 0x0010,  
   ADDRESS_KIND_METADATA_FIELD          = 0x0011,  
   ADDRESS_KIND_METADATA_LOCAL          = 0x0012,  
   ADDRESS_KIND_METADATA_PARAM          = 0x0013,  
   ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,  
   ADDRESS_KIND_METADATA_RETVAL         = 0x0015,  
};  
typedef DWORD ADDRESS_KIND;  
```  
  
```csharp  
public enum enum_ADDRESS_KIND {  
   ADDRESS_KIND_NATIVE                  = 0x0001,  
   ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,  
   ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,  
   ADDRESS_KIND_METADATA_METHOD         = 0x0010,  
   ADDRESS_KIND_METADATA_FIELD          = 0x0011,  
   ADDRESS_KIND_METADATA_LOCAL          = 0x0012,  
   ADDRESS_KIND_METADATA_PARAM          = 0x0013,  
   ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,  
   ADDRESS_KIND_METADATA_RETVAL         = 0x0015,  
};  
```  
  
## <a name="terms"></a>Termes  
 ADDRESS_KIND_NATIVE  
 Adresse native, représentée par la structure [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) .  
  
 ADDRESS_KIND_UNMANAGED_THIS_RELATIVE  
 Adresse non managée relative à un `this` pointeur ( `Me` en Visual Basic) et représentée par la structure [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) .  
  
 ADDRESS_KIND_UNMANAGED_PHYSICAL  
 Adresse physique non managée, représentée par la structure [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) .  
  
 ADDRESS_KIND_METHOD  
 Méthode d’une classe, représentée par la structure [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) .  
  
 ADDRESS_KIND_FIELD  
 Champ d’une classe, représenté par la structure [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) .  
  
 ADDRESS_KIND_LOCAL  
 L’adresse est destinée à une variable locale et est représentée par la structure [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) .  
  
 ADDRESS_KIND_PARAM  
 Une méthode ou un paramètre de fonction, représenté par la structure [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) .  
  
 ADDRESS_KIND_ARRAYELEM  
 Élément de tableau, représenté par la structure [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) .  
  
 ADDRESS_KIND_RETVAL  
 Valeur de retour, représentée par la structure [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) .  
  
## <a name="remarks"></a>Notes  
 La méthode [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) retourne la structure [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) qui contient une Union de structures possibles, la structure [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) . Le `dwKind` champ de la `DEBUG_ADDRESS_UNION` structure contient la `ADDRESS_KIND` valeur et décrit comment interpréter le champ d’Union.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : SH. h  
  
 Espace de noms : Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
