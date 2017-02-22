---
title: "BP_RESOLUTION_LOCATION | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_RESOLUTION_LOCATION"
helpviewer_keywords: 
  - "Structure BP_RESOLUTION_LOCATION"
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_RESOLUTION_LOCATION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

spécifie la structure de l'emplacement de résolution de point d'arrêt.  
  
## Syntaxe  
  
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
  
```c#  
public struct BP_RESOLUTION_LOCATION {  
   public uint bpType;  
   public IntPtr unionmember1;  
   public IntPtr unionmember2;  
   public IntPtr unionmember3;  
   public uint   unionmember4;  
};  
```  
  
## Membres  
 `bpType`  
 une valeur de l'énumération de [BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md) qui spécifie comment interpréter l'union d' `bpResLocation` ou les membres d' `unionmemberX` .  
  
 `bpResLocation.bpresCode`  
 \[C\+\+\] uniquement contient la structure de [BP\_RESOLUTION\_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) si `bpType` \= `BPT_CODE`.  
  
 `bpResLocation.bpresData`  
 \[C\+\+\] uniquement contient la structure de [BP\_RESOLUTION\_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) si `bpType` \= `BPT_DATA`.  
  
 `bpResLocation.unused`  
 \[C\+\+\] uniquement l'espace réservé d'Un.  
  
 `unionmember1`  
 \[C\#\] uniquement voir notes sur comment interpréter.  
  
 `unionmember2`  
 \[C\#\] uniquement voir notes sur comment interpréter.  
  
 `unionmember3`  
 \[C\#\] uniquement voir notes sur comment interpréter.  
  
 `unionmember4`  
 \[C\#\] uniquement voir notes sur comment interpréter.  
  
## Notes  
 cette structure est un membre des structures de [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) et de [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) .  
  
 \[C\#\] uniquement les membres d' `unionmemberX` sont interprètes en fonction de le tableau suivant.  Recherchez descendant dans la colonne de gauche pour la valeur d' `bpType` puis à travers déterminer ce que représente chaque membre d' `unionmemberX` et marshaler `unionmemberX` en conséquence.  Consultez l'exemple pour qu'un moyen interprète cette structure en c\#.  
  
|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|  
|----------------------|--------------------|--------------------|--------------------|--------------------|  
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|\-|\-|\-|  
|`BPT_DATA`|`string` \(expression de données\)|`string` \(nom de fonction\)|`string` \(nom de l'image\)|`enum_BP_RES_DATA_FLAGS`|  
  
## Exemple  
 Cet exemple montre comment interpréter la structure d' `BP_RESOLUTION_LOCATION` en c\#.  
  
```c#  
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
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md)   
 [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [BP\_RESOLUTION\_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)   
 [BP\_RESOLUTION\_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)   
 [BP\_RES\_DATA\_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)