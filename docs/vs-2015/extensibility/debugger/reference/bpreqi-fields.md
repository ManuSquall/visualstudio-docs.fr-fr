---
title: BPREQI_FIELDS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BPREQI_FIELDS
helpviewer_keywords:
- BPREQI_FIELDS enumeration
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a8ad9e4b6d83ebc05c78a8b84c0c06e00d7563bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153226"
---
# <a name="bpreqi_fields"></a>BPREQI_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Spécifie les informations à récupérer sur une demande de point d’arrêt.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
typedef DWORD BPREQI_FIELDS;  
```  
  
```csharp  
public enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
```  
  
## <a name="members"></a>Membres  
 BPREQI_BPLOCATION  
 Initialisez/utilisez le `bpLocation` champ (emplacement du point d’arrêt) de la structure [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) ou [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .  
  
 BPREQI_LANGUAGE  
 Initialisez/utilisez le `guidLanguage` champ de la `BP_REQUEST_INFO` `BP_REQUEST_INFO2` structure ou.  
  
 BPREQI_PROGRAM  
 Initialisez/utilisez le `pProgram` champ de la `BP_REQUEST_INFO` `BP_REQUEST_INFO2` structure ou.  
  
 BPREQI_PROGRAMNAME  
 Initialisez/utilisez le `bstrProgramName` champ de la `BP_REQUEST_INFO` `BP_REQUEST_INFO2` structure ou.  
  
 BPREQI_THREAD  
 Initialisez/utilisez le `pThread` champ de la `BP_REQUEST_INFO` `BP_REQUEST_INFO2` structure ou.  
  
 BPREQI_THREADNAME  
 Initialisez/utilisez le `bstrThreadName` champ de la `BP_REQUEST_INFO` `BP_REQUEST_INFO2` structure ou.  
  
 BPREQI_PASSCOUNT  
 Initialisez/utilisez le `bpPassCount` champ de la `BP_REQUEST_INFO` `BP_REQUEST_INFO2` structure ou.  
  
 BPREQI_CONDITION  
 Initialisez/utilisez le `bpCondition` champ (condition de point d’arrêt) de la `BP_REQUEST_INFO` `BP_REQUEST_INFO2` structure ou.  
  
 BPREQI_FLAGS  
 Initialisez/utilisez le `dwFlags` champ de la `BP_REQUEST_INFO` `BP_REQUEST_INFO2` structure ou.  
  
 BPREQI_ALLOLDFIELDS  
 Initialisez/Utilisez tous les champs pour le de la `BP_REQUEST_INFO` structure.  
  
 BPREQI_VENDOR  
 Initialisez/utilisez le `guidVendor` champ de la `BP_REQUEST_INFO2` structure.  
  
 BPREQI_CONSTRAINT  
 Initialisez/utilisez le `bstrConstraint` champ de la `BP_REQUEST_INFO2` structure.  
  
 BPREQI_TRACEPOINT  
 Initialisez/utilisez le `bstrTracepoint` champ de la `BP_REQUEST_INFO2` structure.  
  
 BPREQI_ALLFIELDS  
 Spécifie tous les champs de la `BP_REQUEST_INFO2` structure.  
  
## <a name="remarks"></a>Notes  
 Passé comme argument aux méthodes [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) et [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) pour spécifier les champs des structures [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) et [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) à initialiser.  
  
 Ces indicateurs sont également utilisés pour indiquer les champs des `BP_REQUEST_INFO` structures et qui `BP_REQUEST_INFO2` sont utilisés et valides lorsque chaque structure est retournée.  
  
 Ces valeurs peuvent être combinées avec une opération de bits `OR` .  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg. h  
  
 Espace de noms : Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
