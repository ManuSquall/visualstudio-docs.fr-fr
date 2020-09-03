---
title: DEBUG_ADDRESS_UNION | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS_UNION
helpviewer_keywords:
- DEBUG_ADDRESS_UNION union
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b500bcb49e9072c3d31ea5ac3f77bda606c23b78
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179180"
---
# <a name="debug_address_union"></a>DEBUG_ADDRESS_UNION
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Décrit différents genres d’adresses.  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
```csharp  
public struct DEBUG_ADDRESS_UNION {  
   public ADDRESS_KIND dwKind;  
   public IntPtr       unionmember;  
}  
```  
  
## <a name="terms"></a>Termes  
 dwKind  
 Valeur de l’énumération [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) , qui spécifie comment interpréter l’Union.  
  
 addr. addrNative  
 [C++ uniquement] Contient la structure [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) si `dwKind` = ADDRESS_KIND_NATIVE.  
  
 addr. addrThisRel  
 [C++ uniquement] Contient la structure[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) si `dwKind` = ADDRESS_KIND_UNMANAGED_THIS_RELATIVE.  
  
 addr. addUPhysical  
 [C++ uniquement] Contient la structure[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) si `dwKind` = ADDRESS_KIND_UNMANAGED_PHYSICAL.  
  
 addr. addrMethod  
 [C++ uniquement] Contient la structure[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) si `dwKind` = ADDRESS_KIND_METHOD.  
  
 addr. addrField  
 [C++ uniquement] Contient la structure[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) si `dwKind` = ADDRESS_KIND_FIELD.  
  
 addr. addrLocal  
 [C++ uniquement] Contient la structure[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) si `dwKind` = ADDRESS_KIND_LOCAL.  
  
 addr. addrParam  
 [C++ uniquement] Contient la structure[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) si `dwKind` = ADDRESS_KIND_PARAM.  
  
 addr. addrArrayElem  
 [C++ uniquement] Contient la structure[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) si `dwKind` = ADDRESS_KIND_ARRAYELEM.  
  
 addr. addrRetVal  
 [C++ uniquement] Contient la structure[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) si `dwKind` = ADDRESS_KIND_RETVAL.  
  
 addr. inutilisé  
 [C++ uniquement] remplissage.  
  
 addr  
 [C++ uniquement] Nom de l’Union.  
  
 unionmember  
 [C# uniquement] Cette valeur doit être marshalée vers le type de structure approprié en fonction de `dwKind` . Consultez la section Notes pour l’association entre `dwKind` et l’interprétation de l’Union.  
  
## <a name="remarks"></a>Notes  
 Cette structure fait partie de la structure [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) et représente l’un des différents types d’adresses (la `DEBUG_ADDRESS` structure est remplie par un appel à la méthode [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) ).  
  
 [C# uniquement] Le tableau suivant indique comment interpréter le `unionmember` membre pour chaque type d’adresse. L’exemple montre comment effectuer cette opération pour un type d’adresse.  
  
|`dwKind`|`unionmember` interprété comme|  
|--------------|----------------------------------|  
|`ADDRESS_KIND_NATIVE`|[NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)|  
|`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`|[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)|  
|`ADDRESS_KIND_UNMANAGED_PHYSICAL`|[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)|  
|`ADDRESS_KIND_METHOD`|[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)|  
|`ADDRESS_KIND_FIELD`|[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)|  
|`ADDRESS_KIND_LOCAL`|[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)|  
|`ADDRESS_KIND_PARAM`|[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)|  
|`ADDRESS_KIND_ARRAYELEM`|[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)|  
|`ADDRESS_KIND_RETVAL`|[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)|  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment interpréter un type d’adresse ( `METADATA_ADDRESS_ARRAYELEM` ) de la `DEBUG_ADDRESS_UNION` structure en C#. Les éléments restants peuvent être interprétés exactement de la même façon.  
  
```csharp  
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
  
## <a name="requirements"></a>Configuration requise  
 En-tête : SH. h  
  
 Espace de noms : Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
