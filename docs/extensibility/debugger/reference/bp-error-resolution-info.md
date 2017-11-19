---
title: BP_ERROR_RESOLUTION_INFO | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BP_ERROR_RESOLUTION_INFO
helpviewer_keywords: BP_ERROR_RESOLUTION_INFO structure
ms.assetid: a6b83242-5728-4716-80f3-840c96d59c6c
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ae45c2a273d394c218d5140d8cec48aa9bd92997
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="bperrorresolutioninfo"></a>BP_ERROR_RESOLUTION_INFO
Décrit la résolution d’un point d’arrêt erreur, y compris l’emplacement, le programme et thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _BP_ERROR_RESOLUTION_INFO {   
   BPERESI_FIELDS         dwFields;  
   BP_RESOLUTION_LOCATION bpResLocation;  
   IDebugProgram2*        pProgram;  
   IDebugThread2*         pThread;  
   BSTR                   bstrMessage;  
   BP_ERROR_TYPE          dwType;  
} BP_ERROR_RESOLUTION_INFO;  
```  
  
```csharp  
public struct BP_ERROR_RESOLUTION_INFO {   
   public uint                   dwFields;  
   public BP_RESOLUTION_LOCATION bpResLocation;  
   public IDebugProgram2         pProgram;  
   public IDebugThread2          pThread;  
   public string                 bstrMessage;  
   public uint                   dwType;  
};  
```  
  
## <a name="members"></a>Membres  
 `dwFields`  
 Une combinaison de valeurs à partir de la [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) énumération spécifiant les champs de cette structure sont remplis.  
  
 `bpResLocation`  
 Le [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) union, ce qui spécifie l’emplacement de la résolution de point d’arrêt.  
  
 `pProgram`  
 Le [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objet qui représente l’application dans laquelle l’erreur de point d’arrêt s’est produite.  
  
 `pThread`  
 Le [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objet qui représente le thread sur lequel l’application qui a généré l’erreur de point d’arrêt est en cours d’exécution.  
  
 `bstrMessage`  
 Chaîne contenant un message d’avertissement ou d’erreur résultant de la résolution de cette erreur.  
  
 `dwType`  
 Une valeur à partir de la [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) énumération qui spécifie le type d’erreur de point d’arrêt.  
  
## <a name="remarks"></a>Remarques  
 Cette structure est retournée à partir de la [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) (méthode).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)   
 [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)   
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)