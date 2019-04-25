---
title: BP_RESOLUTION_LOCATION | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_LOCATION
helpviewer_keywords:
- BP_RESOLUTION_LOCATION structure
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2ea6539f2ed790dda5cc4c9de126aa226f4b2686
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953307"
---
# <a name="bpresolutionlocation"></a>BP_RESOLUTION_LOCATION
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Spécifie la structure de l’emplacement de la résolution de point d’arrêt.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
struct _BP_RESOLUTION_LOCATION {  
   BP_TYPE bpType;  
   union {  
      BP_RESOLUTION_CODE bpresCode;  
      BP_RESOLUTION_DATA bpresData;  
      int                unused;  
   } bpResLocation;  
} BP_RESOLUTION_LOCATION;  
```  
  
```csharp  
public struct BP_RESOLUTION_LOCATION {  
   public uint bpType;  
   public IntPtr unionmember1;  
   public IntPtr unionmember2;  
   public IntPtr unionmember3;  
   public uint   unionmember4;  
};  
```  
  
## <a name="members"></a>Membres  
 `bpType`  
 Une valeur comprise entre le [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) énumération qui spécifie comment interpréter les `bpResLocation` union ou `unionmemberX` membres.  
  
 `bpResLocation.bpresCode`  
 (C++ uniquement) Contient le [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) structure si `bpType`  =  `BPT_CODE`.  
  
 `bpResLocation.bpresData`  
 (C++ uniquement) Contient le [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) structure si `bpType`  =  `BPT_DATA`.  
  
 `bpResLocation.unused`  
 (C++ uniquement) Un espace réservé.  
  
 `unionmember1`  
 [C# uniquement] Consultez la section Notes sur l’interprétation.  
  
 `unionmember2`  
 [C# uniquement] Consultez la section Notes sur l’interprétation.  
  
 `unionmember3`  
 [C# uniquement] Consultez la section Notes sur l’interprétation.  
  
 `unionmember4`  
 [C# uniquement] Consultez la section Notes sur l’interprétation.  
  
## <a name="remarks"></a>Notes  
 Cette structure est un membre de la [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) et [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) structures.  
  
 [C# uniquement] Le `unionmemberX` membres sont interprétées selon le tableau suivant. Rechercher vers le bas de la colonne de gauche pour le `bpType` valeur ensuite à travers à déterminer ce que chaque `unionmemberX` membre représente et marshaler le `unionmemberX` en conséquence. Consultez l’exemple d’une façon d’interpréter cette structure en C#.  
  
|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|  
|----------------------|--------------------|--------------------|--------------------|--------------------|  
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|  
|`BPT_DATA`|`string` (expression de données)|`string` (nom de fonction)|`string` (nom de l’image)|`enum_BP_RES_DATA_FLAGS`|  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment interpréter le `BP_RESOLUTION_LOCATION` structure en C#.  
  
```csharp  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(BP_RESOLUTION_LOCATION bprl)  
        {  
            if (bprl.bpType == (uint)enum_BP_TYPE.BPT_CODE)  
            {  
                 IDebugCodeContext2 pContext = (IDebugCodeContext2)Marshal.GetObjectForIUnknown(bp.unionmember1);  
            }  
            else if (bprl.bpType == (uint)enum_BP_TYPE.BPT_DATA)  
            {  
                 string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);  
                 string functionName = Marshal.PtrToStringBSTR(bp.unionmember2);  
                 string imageName = Marshal.PtrToStringBSTR(bp.unionmember3);  
                 enum_BP_RES_DATA_FLAGS numElements = (enum_BP_RES_DATA_FLAGS)bp.unionmember4;  
            }  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)   
 [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)   
 [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)
