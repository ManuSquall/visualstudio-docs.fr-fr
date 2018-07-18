---
title: BP_REQUEST_INFO2 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_REQUEST_INFO2
helpviewer_keywords:
- BP_REQUEST_INFO2 structure
ms.assetid: 008c87f7-a76e-43d3-8904-11b225d6a9a5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 11402c5ad188b72600debb5cb64b7f2811e75ee9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31104681"
---
# <a name="bprequestinfo2"></a>BP_REQUEST_INFO2
Contient les informations requises pour implémenter un point d’arrêt, y compris le GUID de fournisseur, de contrainte et de point de trace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _BP_REQUEST_INFO2 {  
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
   GUID            guidVendor;  
   BSTR            bstrConstraint;  
   BSTR            bstrTracepoint;  
} BP_REQUEST_INFO2;  
```  
  
```csharp  
public struct BP_REQUEST_INFO2 {  
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
   public Guid           guidVendor;  
   public string         bstrConstraint;  
   public string         bstrTracepoint;  
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
  
 `guidVendor`  
 GUID du fournisseur. Peut être une valeur null.  
  
 `bstrConstraint`  
 Nom de contrainte de point d’arrêt. Peut être une valeur null.  
  
 `bstrTracepoint`  
 Nom du point de trace. Peut être une valeur null.  
  
## <a name="remarks"></a>Notes  
 Cette structure est retournée par la [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md) (méthode).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)   
 [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)