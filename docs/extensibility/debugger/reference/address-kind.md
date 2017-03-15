---
title: "ADDRESS_KIND | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ADDRESS_KIND"
helpviewer_keywords: 
  - "Énumération de ADDRESS_KIND"
ms.assetid: 3a12fbec-7088-4cf9-8f6f-ad8ddec6009a
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# ADDRESS_KIND
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Spécifie les types d'adresses.  
  
## Syntaxe  
  
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
  
```c#  
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
  
## termes  
 ADDRESS\_KIND\_NATIVE  
 une adresse native, représentée par la structure de [NATIVE\_ADDRESS](../../../extensibility/debugger/reference/native-address.md) .  
  
 ADDRESS\_KIND\_UNMANAGED\_THIS\_RELATIVE  
 Une adresse non managée par rapport à un pointeur d' `this` \(`Me` en Visual Basic\) et représentée par la structure d' [UNMANAGED\_ADDRESS\_THIS\_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) .  
  
 ADDRESS\_KIND\_UNMANAGED\_PHYSICAL  
 une adresse physique non managée, représentée par la structure d' [UNMANAGED\_ADDRESS\_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) .  
  
 ADDRESS\_KIND\_METHOD  
 une méthode de classe, représentée par la structure de [METADATA\_ADDRESS\_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) .  
  
 ADDRESS\_KIND\_FIELD  
 un champ d'une classe, représenté par la structure de [METADATA\_ADDRESS\_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) .  
  
 ADDRESS\_KIND\_LOCAL  
 l'adresse est pour une variable locale et est représentée par la structure de [METADATA\_ADDRESS\_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) .  
  
 ADDRESS\_KIND\_PARAM  
 une méthode ou un paramètre de fonction, représenté par la structure de [METADATA\_ADDRESS\_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) .  
  
 ADDRESS\_KIND\_ARRAYELEM  
 un élément de tableau, représenté par la structure de [METADATA\_ADDRESS\_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) .  
  
 ADDRESS\_KIND\_RETVAL  
 une valeur de retour, représentée par la structure de [METADATA\_ADDRESS\_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) .  
  
## Notes  
 La méthode d' [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) retourne la structure de [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) qui contient une union des structures possibles, la structure de [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) .  Le champ d' `dwKind` de la structure d' `DEBUG_ADDRESS_UNION` contient la valeur d' `ADDRESS_KIND` et décrit comment interpréter le champ de l'union.  
  
## Configuration requise  
 en\-tête : sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)