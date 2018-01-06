---
title: BP_RESOLUTION_LOCATION | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BP_RESOLUTION_LOCATION
helpviewer_keywords: BP_RESOLUTION_LOCATION structure
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a85c6c097867aea17be4b4aeca1431a05c74903a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="bpresolutionlocation"></a>BP_RESOLUTION_LOCATION
Spécifie la structure de l’emplacement de la résolution de point d’arrêt.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
 Une valeur à partir de la [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) énumération qui spécifie comment interpréter les `bpResLocation` union ou `unionmemberX` membres.  
  
 `bpResLocation.bpresCode`  
 (C++ uniquement) Contient le [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) si la structure `bpType`  =  `BPT_CODE`.  
  
 `bpResLocation.bpresData`  
 (C++ uniquement) Contient le [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) si la structure `bpType`  =  `BPT_DATA`.  
  
 `bpResLocation.unused`  
 (C++ uniquement) Un espace réservé.  
  
 `unionmember1`  
 (C# uniquement) Consultez la section Notes sur l’interprétation.  
  
 `unionmember2`  
 (C# uniquement) Consultez la section Notes sur l’interprétation.  
  
 `unionmember3`  
 (C# uniquement) Consultez la section Notes sur l’interprétation.  
  
 `unionmember4`  
 (C# uniquement) Consultez la section Notes sur l’interprétation.  
  
## <a name="remarks"></a>Notes  
 Cette structure est un membre de la [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) et [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) structures.  
  
 (C# uniquement) Le `unionmemberX` membres sont interprétés en fonction de la table suivante. Rechercher vers le bas de la colonne de gauche pour le `bpType` valeur puis à travers pour déterminer ce que chaque `unionmemberX` membre représente et marshaler le `unionmemberX` en conséquence. Consultez l’exemple d’une manière d’interpréter cette structure en c#.  
  
|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|  
|----------------------|--------------------|--------------------|--------------------|--------------------|  
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|  
|`BPT_DATA`|`string`(expression de données)|`string`(nom de la fonction)|`string`(nom de l’image)|`enum_BP_RES_DATA_FLAGS`|  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment interpréter le `BP_RESOLUTION_LOCATION` structure en c#.  
  
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
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)   
 [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)   
 [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)