---
title: "DEBUG_ADDRESS_UNION | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEBUG_ADDRESS_UNION"
helpviewer_keywords: 
  - "Union DEBUG_ADDRESS_UNION"
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# DEBUG_ADDRESS_UNION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

décrit différents genres d'adresses.  
  
## Syntaxe  
  
```cpp  
typedef struct _tagDEBUG_ADDRESS_UNION {  
   ADDRESS_KIND dwKind;  
   union {  
      NATIVE_ADDRESS                  addrNative;  
      UNMANAGED_ADDRESS_THIS_RELATIVE addrThisRel;  
      UNMANAGED_ADDRESS_PHYSICAL      addrUPhysical;  
      METADATA_ADDRESS_METHOD         addrMethod;  
      METADATA_ADDRESS_FIELD          addrField;  
      METADATA_ADDRESS_LOCAL          addrLocal;  
      METADATA_ADDRESS_PARAM          addrParam;  
      METADATA_ADDRESS_ARRAYELEM      addrArrayElem;  
      METADATA_ADDRESS_RETVAL         addrRetVal;  
      DWORD                           unused;  
   } addr;  
} DEBUG_ADDRESS_UNION;  
```  
  
```c#  
public struct DEBUG_ADDRESS_UNION {  
   public ADDRESS_KIND dwKind;  
   public IntPtr       unionmember;  
}  
```  
  
## termes  
 dwKind  
 Une valeur de l'énumération d' [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) , en spécifiant comment interpréter l'union.  
  
 addr.addrNative  
 \[C\+\+\] uniquement contient la structure de [NATIVE\_ADDRESS](../../../extensibility/debugger/reference/native-address.md) si `dwKind` \= ADDRESS\_KIND\_NATIVE.  
  
 addr.addrThisRel  
 \[C\+\+\] uniquement contient la structure de[UNMANAGED\_ADDRESS\_THIS\_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) si `dwKind` \= ADDRESS\_KIND\_UNMANAGED\_THIS\_RELATIVE.  
  
 addr.addUPhysical  
 \[C\+\+\] uniquement contient la structure de[UNMANAGED\_ADDRESS\_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) si `dwKind` \= ADDRESS\_KIND\_UNMANAGED\_PHYSICAL.  
  
 addr.addrMethod  
 \[C\+\+\] uniquement contient la structure de[METADATA\_ADDRESS\_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) si `dwKind` \= ADDRESS\_KIND\_METHOD.  
  
 addr.addrField  
 \[C\+\+\] uniquement contient la structure de[METADATA\_ADDRESS\_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) si `dwKind` \= ADDRESS\_KIND\_FIELD.  
  
 addr.addrLocal  
 \[C\+\+\] uniquement contient la structure de[METADATA\_ADDRESS\_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) si `dwKind` \= ADDRESS\_KIND\_LOCAL.  
  
 addr.addrParam  
 \[C\+\+\] uniquement contient la structure de[METADATA\_ADDRESS\_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) si `dwKind` \= ADDRESS\_KIND\_PARAM.  
  
 addr.addrArrayElem  
 \[C\+\+\] uniquement contient la structure de[METADATA\_ADDRESS\_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) si `dwKind` \= ADDRESS\_KIND\_ARRAYELEM.  
  
 addr.addrRetVal  
 \[C\+\+\] uniquement contient la structure de[METADATA\_ADDRESS\_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) si `dwKind` \= ADDRESS\_KIND\_RETVAL.  
  
 addr.unused  
 \[C\+\+\] uniquement effectuer.  
  
 addr  
 \[C\+\+\] uniquement le nom de l'union.  
  
 unionmember  
 \[C\#\] uniquement cette valeur doit être marshalé vers le type approprié de structure en fonction `dwKind`.  Consultez la section notes de l'association entre `dwKind` et l'interprétation de l'union.  
  
## Notes  
 Cette structure fait partie de la structure de [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) et représente un d'un certain nombre de types d'adresses \(la structure d' `DEBUG_ADDRESS` est effectuée par un appel à la méthode d' [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) \).  
  
 \[C\#\] uniquement le tableau suivant montre comment interpréter le membre d' `unionmember` pour chaque type d'adresse.  L'exemple montre comment cela est fait pour un type d'adresse.  
  
|`dwKind`|`unionmember` a interprète comme|  
|--------------|--------------------------------------|  
|`ADDRESS_KIND_NATIVE`|[NATIVE\_ADDRESS](../../../extensibility/debugger/reference/native-address.md)|  
|`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`|[UNMANAGED\_ADDRESS\_THIS\_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)|  
|`ADDRESS_KIND_UNMANAGED_PHYSICAL`|[UNMANAGED\_ADDRESS\_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)|  
|`ADDRESS_KIND_METHOD`|[METADATA\_ADDRESS\_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)|  
|`ADDRESS_KIND_FIELD`|[METADATA\_ADDRESS\_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)|  
|`ADDRESS_KIND_LOCAL`|[METADATA\_ADDRESS\_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)|  
|`ADDRESS_KIND_PARAM`|[METADATA\_ADDRESS\_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)|  
|`ADDRESS_KIND_ARRAYELEM`|[METADATA\_ADDRESS\_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)|  
|`ADDRESS_KIND_RETVAL`|[METADATA\_ADDRESS\_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)|  
  
## Exemple  
 Cet exemple montre comment interpréter un type d'adresse \(`METADATA_ADDRESS_ARRAYELEM`\) de la structure d' `DEBUG_ADDRESS_UNION` en c\#.  Les éléments restants peuvent être interprètes de la même façon.  
  
```c#  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(DEBUG_ADDRESS_UNION dau)  
        {  
            if (dau.dwKind == (uint)enum_ADDRESS_KIND.ADDRESS_KIND_METADATA_ARRAYELEM)  
            {  
                 METADATA_ADDRESS_ARRAYELEM arrayElem =  
                     (METADATA_ADDRESS_ARRAYELEM)Marshal.PtrToStructure(dau.unionmember,  
                                 typeof(METADATA_ADDRESS_ARRAYELEM));  
            }  
        }  
    }  
}  
```  
  
## Configuration requise  
 en\-tête : sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)