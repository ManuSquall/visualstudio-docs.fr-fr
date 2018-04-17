---
title: BPREQI_FIELDS | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BPREQI_FIELDS
helpviewer_keywords:
- BPREQI_FIELDS enumeration
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ff66a2c23f96ad083d84a937a45c1b2b8cf3ddec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
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
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)