---
title: BP_LOCATION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_LOCATION
helpviewer_keywords:
- BP_LOCATION union
ms.assetid: ed1e874c-f289-4c31-8b6c-04dde03ad0f5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 237d89abeb4d41a2c01a7e7d0eb1ccc1ca7a6ddc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54974043"
---
# <a name="bplocation"></a>BP_LOCATION
Spécifie le type de structure utilisée pour décrire l’emplacement du point d’arrêt.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _BP_LOCATION {  
   BP_LOCATION_TYPE bpLocationType;  
   union {  
      BP_LOCATION_CODE_FILE_LINE   bplocCodeFileLine;  
      BP_LOCATION_CODE_FUNC_OFFSET bplocCodeFuncOffset;  
      BP_LOCATION_CODE_CONTEXT     bplocCodeContext;  
      BP_LOCATION_CODE_STRING      bplocCodeString;  
      BP_LOCATION_CODE_ADDRESS     bplocCodeAddress;  
      BP_LOCATION_DATA_STRING      bplocDataString;  
      BP_LOCATION_RESOLUTION       bplocResolution;  
      DWORD                        unused;  
   } bpLocation;  
} BP_LOCATION;  
```  
  
```csharp  
public struct BP_LOCATION {  
   public uint   bpLocationType;  
   public IntPtr unionmember1;  
   public IntPtr unionmember2;  
   public IntPtr unionmember3;  
   public IntPtr unionmember4;  
};  
```  
  
## <a name="members"></a>Membres  
 `bpLocationType`  
 Une valeur comprise entre le [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) énumération utilisée pour interpréter la `bpLocation` union ou `unionmemberX` membres.  
  
 `bpLocation`.`bplocCodeFileLine`  
 (C++ uniquement) Contient le [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) structure si `bpLocationType`  =  `BPLT_CODE_FILE_LINE`.  
  
 `bpLocation.bplocCodeFuncOffset`  
 (C++ uniquement) Contient le [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) structure si `bpLocationType`  =  `BPLT_CODE_FUNC_OFFSET`.  
  
 `bpLocation.bplocCodeContext`  
 (C++ uniquement) Contient le [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) structure si `bpLocationType`  =  `BPLT_CODE_CONTEXT`.  
  
 `bpLocation.bplocCodeString`  
 (C++ uniquement) Contient le [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) structure si `bpLocationType`  =  `BPLT_CODE_STRING`.  
  
 `bpLocation.bplocCodeAddress`  
 (C++ uniquement) Contient le [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) structure si `bpLocationType`  =  `BPLT_CODE_ADDRESS`.  
  
 `bpLocation.bplocDataString`  
 (C++ uniquement) Contient le [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) structure si `bpLocationType`  =  `BPLT_DATA_STRING`.  
  
 `bpLocation.bplocResolution`  
 (C++ uniquement) Contient le [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) structure si `bpLocationType`  =  `BPLT_RESOLUTION`.  
  
 `unionmember1`  
 [C# uniquement] Consultez la section Notes sur l’interprétation.  
  
 `unionmember2`  
 [C# uniquement] Consultez la section Notes sur l’interprétation.  
  
 `unionmember3`  
 [C# uniquement] Consultez la section Notes sur l’interprétation.  
  
 `unionmember4`  
 [C# uniquement] Consultez la section Notes sur l’interprétation.  
  
## <a name="remarks"></a>Notes  
 Cette structure est un membre de la [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) et [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) structures.  
  
 [C# uniquement] Le `unionmemberX` membres sont interprétées selon le tableau suivant. Rechercher vers le bas de la colonne de gauche pour le `bpLocationType` valeur puis rechercher dans les autres colonnes pour déterminer ce que chaque `unionmemberX` membre représente et marshaler le `unionmemberX` en conséquence. Consultez l’exemple pour savoir comment interpréter une partie de cette structure en c#.  
  
|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|  
|----------------------|--------------------|--------------------|--------------------|--------------------|  
|`BPLT_CODE_FILE_LINE`|`string` (un contexte)|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|-|-|  
|`BPLT_CODE_FUNC_OFFSET`|`string` (un contexte)|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|-|-|  
|`BPLT_CODE_CONTEXT`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|  
|`BPLT_CODE_STRING`|`string` (un contexte)|`string` (expression conditionnelle)|-|-|  
|`BPLT_CODE_ADDRESS`|`string` (un contexte)|`string` module URL)|`string` (nom de fonction)|`string` (address)|  
|`BPLT_DATA_STRING`|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|`string` (un contexte)|`string` (expression de données)|`uint` (nombre d’éléments)|  
|`BPLT_RESOLUTION`|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|-|-|-|  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment interpréter le `BP_LOCATION` structure en c# pour le `BPLT_DATA_STRING` type. Ce type particulier montre comment interpréter ces quatre `unionmemberX` membres dans tous les formats possibles (object, string et nombre).  
  
```csharp  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(BP_LOCATION bp)  
        {  
            if (bp.bpLocationType == (uint)enum_BP_LOCATION_TYPE.BPLT_DATA_STRING)  
            {  
                 IDebugThread2 pThread = (IDebugThread2)Marshal.GetObjectForIUnknown(bp.unionmember1);  
                 string context = Marshal.PtrToStringBSTR(bp.unionmember2);  
                 string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);  
                 uint numElements = (uint)Marshal.ReadInt32(bp.unionmember4);  
            }  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)   
 [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)   
 [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)   
 [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)   
 [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)   
 [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)   
 [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)