---
title: "BP_LOCATION | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_LOCATION"
helpviewer_keywords: 
  - "Union BP_LOCATION"
ms.assetid: ed1e874c-f289-4c31-8b6c-04dde03ad0f5
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# BP_LOCATION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

spécifie le type de structure utilisé pour décrire l'emplacement du point d'arrêt.  
  
## Syntaxe  
  
```cpp#  
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
  
```c#  
public struct BP_LOCATION {  
   public uint   bpLocationType;  
   public IntPtr unionmember1;  
   public IntPtr unionmember2;  
   public IntPtr unionmember3;  
   public IntPtr unionmember4;  
};  
```  
  
## Membres  
 `bpLocationType`  
 une valeur de l'énumération de [BP\_LOCATION\_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) utilisée pour interpréter l'union d' `bpLocation` ou les membres d' `unionmemberX` .  
  
 `bpLocation`.`bplocCodeFileLine`  
 \[C\+\+\] uniquement contient la structure de [BP\_LOCATION\_CODE\_FILE\_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) si `bpLocationType` \= `BPLT_CODE_FILE_LINE`.  
  
 `bpLocation.bplocCodeFuncOffset`  
 \[C\+\+\] uniquement contient la structure de [BP\_LOCATION\_CODE\_FUNC\_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) si `bpLocationType` \= `BPLT_CODE_FUNC_OFFSET`.  
  
 `bpLocation.bplocCodeContext`  
 \[C\+\+\] uniquement contient la structure de [BP\_LOCATION\_CODE\_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) si `bpLocationType` \= `BPLT_CODE_CONTEXT`.  
  
 `bpLocation.bplocCodeString`  
 \[C\+\+\] uniquement contient la structure de [BP\_LOCATION\_CODE\_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) si `bpLocationType` \= `BPLT_CODE_STRING`.  
  
 `bpLocation.bplocCodeAddress`  
 \[C\+\+\] uniquement contient la structure de [BP\_LOCATION\_CODE\_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) si `bpLocationType` \= `BPLT_CODE_ADDRESS`.  
  
 `bpLocation.bplocDataString`  
 \[C\+\+\] uniquement contient la structure de [BP\_LOCATION\_DATA\_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) si `bpLocationType` \= `BPLT_DATA_STRING`.  
  
 `bpLocation.bplocResolution`  
 \[C\+\+\] uniquement contient la structure de [BP\_LOCATION\_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) si `bpLocationType` \= `BPLT_RESOLUTION`.  
  
 `unionmember1`  
 \[C\#\] uniquement voir notes sur comment interpréter.  
  
 `unionmember2`  
 \[C\#\] uniquement voir notes sur comment interpréter.  
  
 `unionmember3`  
 \[C\#\] uniquement voir notes sur comment interpréter.  
  
 `unionmember4`  
 \[C\#\] uniquement voir notes sur comment interpréter.  
  
## Notes  
 cette structure est un membre des structures de [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) et de [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .  
  
 \[C\#\] uniquement les membres d' `unionmemberX` sont interprètes en fonction de le tableau suivant.  Recherchez descendant dans la colonne de gauche pour la valeur puis l'apparence d' `bpLocationType` entre les autres colonnes déterminer ce que représente chaque membre d' `unionmemberX` et marshaler `unionmemberX` en conséquence.  Consultez l'exemple pour qu'un moyen interprète une partie de cette structure en c\#.  
  
|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|  
|----------------------|--------------------|--------------------|--------------------|--------------------|  
|`BPLT_CODE_FILE_LINE`|`string` \(un contexte\)|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|\-|\-|  
|`BPLT_CODE_FUNC_OFFSET`|`string` \(un contexte\)|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|\-|\-|  
|`BPLT_CODE_CONTEXT`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|\-|\-|\-|  
|`BPLT_CODE_STRING`|`string` \(un contexte\)|`string` \(expression conditionnelle\)|\-|\-|  
|`BPLT_CODE_ADDRESS`|`string` \(un contexte\)|`string` \(URL de module\)|`string` \(nom de fonction\)|`string` \(adresse\)|  
|`BPLT_DATA_STRING`|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|`string` \(un contexte\)|`string` \(expression de données\)|`uint` \(nombre d'éléments\)|  
|`BPLT_RESOLUTION`|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|\-|\-|\-|  
  
## Exemple  
 Cet exemple montre comment interpréter la structure d' `BP_LOCATION` en c\# pour le type d' `BPLT_DATA_STRING` .  Ce type particulier montre comment interpréter les quatre membres d' `unionmemberX` dans tous les formats possibles \(objet, chaîne, et numéro\).  
  
```c#  
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
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_LOCATION\_CODE\_FILE\_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)   
 [BP\_LOCATION\_CODE\_FUNC\_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)   
 [BP\_LOCATION\_CODE\_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)   
 [BP\_LOCATION\_CODE\_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)   
 [BP\_LOCATION\_CODE\_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)   
 [BP\_LOCATION\_DATA\_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)   
 [BP\_LOCATION\_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)