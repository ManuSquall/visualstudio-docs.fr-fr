---
title: BP_REQUEST_INFO | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BP_REQUEST_INFO
helpviewer_keywords: BP_REQUEST_INFO structure
ms.assetid: 42a31412-5b6b-47fe-a762-0c2bc769e1cc
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 64f39aa59d566d85147b953ca8df4930d2a49eca
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="bprequestinfo"></a>BP_REQUEST_INFO
Contient les informations requises pour implémenter un point d’arrêt.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _BP_REQUEST_INFO {  
   BPREQI_FIELDS   dwFields;  
   GUID            guidLanguage;  
   BP_LOCATION     bpLocation;  
   IDebugProgram2* pProgram;  
   BSTR            bstrProgramName;  
   IDebugThread2*  pThread;  
   BSTR            bstrThreadName;  
   BP_CONDITION    bpCondition;  
   BP_PASSCOUNT    bpPassCount;  
   BP_FLAGS        dwFlags;  
} BP_REQUEST_INFO;  
```  
  
```csharp  
public struct BP_REQUEST_INFO {  
   public uint           dwFields;  
   public Guid           guidLanguage;  
   public BP_LOCATION    bpLocation;  
   public IDebugProgram2 pProgram;  
   public string         bstrProgramName;  
   public IDebugThread2  pThread;  
   public string         bstrThreadName;  
   public BP_CONDITION   bpCondition;  
   public BP_PASSCOUNT   bpPassCount;  
   public uint           dwFlags;  
};  
```  
  
## <a name="members"></a>Membres  
 `dwFields`  
 Une combinaison d’indicateurs à partir de la [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) énumération qui spécifie les champs sont remplis.  
  
 `guidLanguage`  
 GUID de la langue.  
  
 `bpLocation`  
 Le [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) structure qui spécifie le type de l’emplacement du point d’arrêt.  
  
 `pProgram`  
 Le [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objet qui représente l’application dans laquelle le point d’arrêt se produit.  
  
 `bstrProgramName`  
 Le nom de l’application dans laquelle le point d’arrêt se produit.  
  
 `pThread`  
 Le [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objet qui représente le thread dans lequel le point d’arrêt se produit.  
  
 `bstrThreadName`  
 Le nom du thread dans lequel le point d’arrêt se produit.  
  
 `bpCondition`  
 Le [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) structure qui décrit les conditions dans lesquelles le point d’arrêt se déclenche.  
  
 `bpPassCount`  
 Le [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) structure qui contient les informations de nombre passe du point d’arrêt.  
  
 `dwFlags`  
 Une combinaison d’indicateurs à partir de la [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) énumération qui spécifie les indicateurs pour le point d’arrêt demandé.  
  
## <a name="remarks"></a>Remarques  
 Cette structure est retournée par la [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) (méthode).  
  
 Si vous avez besoin d’obtenir le fournisseur de moteur de débogage GUID, la contrainte de point d’arrêt ou le point de trace, consultez le [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) structure.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)