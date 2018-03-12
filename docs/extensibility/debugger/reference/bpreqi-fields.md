---
title: BPREQI_FIELDS | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BPREQI_FIELDS
helpviewer_keywords:
- BPREQI_FIELDS enumeration
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 1e7c0206ca5834b281447e9a00c4ce3cad0c247c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="bpreqifields"></a>BPREQI_FIELDS
Spécifie les informations à récupérer sur une demande de point d’arrêt.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
typedef DWORD BPREQI_FIELDS;  
```  
  
```csharp  
public enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
```  
  
## <a name="members"></a>Membres  
 BPREQI_BPLOCATION  
 Initialisation/utiliser le `bpLocation` champ (emplacement de point d’arrêt) de la [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) ou [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) structure.  
  
 BPREQI_LANGUAGE  
 Initialisation/utiliser le `guidLanguage` champ le `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.  
  
 BPREQI_PROGRAM  
 Initialisation/utiliser le `pProgram` champ le `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.  
  
 BPREQI_PROGRAMNAME  
 Initialisation/utiliser le `bstrProgramName` champ le `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.  
  
 BPREQI_THREAD  
 Initialisation/utiliser le `pThread` champ le `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.  
  
 BPREQI_THREADNAME  
 Initialisation/utiliser le `bstrThreadName` champ le `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.  
  
 BPREQI_PASSCOUNT  
 Initialisation/utiliser le `bpPassCount` champ le `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.  
  
 BPREQI_CONDITION  
 Initialisation/utiliser le `bpCondition` champ (condition de point d’arrêt) de la `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.  
  
 BPREQI_FLAGS  
 Initialisation/utiliser le `dwFlags` champ le `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.  
  
 BPREQI_ALLOLDFIELDS  
 Initialisation/utiliser tous les champs de la de la `BP_REQUEST_INFO` structure.  
  
 BPREQI_VENDOR  
 Initialisation/utiliser le `guidVendor` champ `BP_REQUEST_INFO2` structure.  
  
 BPREQI_CONSTRAINT  
 Initialisation/utiliser le `bstrConstraint` champ `BP_REQUEST_INFO2` structure.  
  
 BPREQI_TRACEPOINT  
 Initialisation/utiliser le `bstrTracepoint` champ `BP_REQUEST_INFO2` structure.  
  
 BPREQI_ALLFIELDS  
 Spécifie tous les champs pour la `BP_REQUEST_INFO2` structure.  
  
## <a name="remarks"></a>Notes  
 Est passé comme argument à la [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) et [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) méthodes pour spécifier les champs de la [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) et [BP_REQUEST_INFO2 ](../../../extensibility/debugger/reference/bp-request-info2.md) structures doivent être initialisées.  
  
 Ces indicateurs sont également utilisés pour indiquer les champs de la `BP_REQUEST_INFO` et `BP_REQUEST_INFO2` les structures sont utilisés et valide lors de chaque structure est retournée.  
  
 Ces valeurs peuvent être combinées avec une opération de bits `OR`.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)