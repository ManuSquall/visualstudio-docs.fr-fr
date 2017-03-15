---
title: "BPREQI_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BPREQI_FIELDS"
helpviewer_keywords: 
  - "Énumération de BPREQI_FIELDS"
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# BPREQI_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Spécifie les informations à récupérer à propos d'une requête de point d'arrêt.  
  
## Syntaxe  
  
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
  
```c#  
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
  
## Membres  
 BPREQI\_BPLOCATION  
 Initialisez\/utilisez le champ d' `bpLocation` \(emplacement du point d'arrêt\) de la structure de [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) ou de [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .  
  
 BPREQI\_LANGUAGE  
 Initialisez\/utilisez le champ d' `guidLanguage` de la structure d' `BP_REQUEST_INFO` ou d' `BP_REQUEST_INFO2` .  
  
 BPREQI\_PROGRAM  
 Initialisez\/utilisez le champ d' `pProgram` de la structure d' `BP_REQUEST_INFO` ou d' `BP_REQUEST_INFO2` .  
  
 BPREQI\_PROGRAMNAME  
 Initialisez\/utilisez le champ d' `bstrProgramName` de la structure d' `BP_REQUEST_INFO` ou d' `BP_REQUEST_INFO2` .  
  
 BPREQI\_THREAD  
 Initialisez\/utilisez le champ d' `pThread` de la structure d' `BP_REQUEST_INFO` ou d' `BP_REQUEST_INFO2` .  
  
 BPREQI\_THREADNAME  
 Initialisez\/utilisez le champ d' `bstrThreadName` de la structure d' `BP_REQUEST_INFO` ou d' `BP_REQUEST_INFO2` .  
  
 BPREQI\_PASSCOUNT  
 Initialisez\/utilisez le champ d' `bpPassCount` de la structure d' `BP_REQUEST_INFO` ou d' `BP_REQUEST_INFO2` .  
  
 BPREQI\_CONDITION  
 Initialisez\/utilisez le champ d' `bpCondition` \(condition de point d'arrêt\) de la structure d' `BP_REQUEST_INFO` ou d' `BP_REQUEST_INFO2` .  
  
 BPREQI\_FLAGS  
 Initialisez\/utilisez le champ d' `dwFlags` de la structure d' `BP_REQUEST_INFO` ou d' `BP_REQUEST_INFO2` .  
  
 BPREQI\_ALLOLDFIELDS  
 Initialisez\/utiliser tous les champs de la structure d' `BP_REQUEST_INFO` .  
  
 BPREQI\_VENDOR  
 Initialisez\/utilisez le champ d' `guidVendor` de la structure d' `BP_REQUEST_INFO2` .  
  
 BPREQI\_CONSTRAINT  
 Initialisez\/utilisez le champ d' `bstrConstraint` de la structure d' `BP_REQUEST_INFO2` .  
  
 BPREQI\_TRACEPOINT  
 Initialisez\/utilisez le champ d' `bstrTracepoint` de la structure d' `BP_REQUEST_INFO2` .  
  
 BPREQI\_ALLFIELDS  
 Spécifie tous les champs de la structure d' `BP_REQUEST_INFO2` .  
  
## Notes  
 Passés comme argument aux méthodes d' [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) et d' [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) pour spécifier les champs de [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) et de [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) structure sont être initialisé.  
  
 Ces indicateurs sont également utilisées pour indiquer que les champs des structures d' `BP_REQUEST_INFO` et d' `BP_REQUEST_INFO2` sont utilisés et valides lorsque chaque structure est retournée.  
  
 Ces valeurs peuvent être combinées avec `OR`de bits.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)