---
title: BPREQI_FIELDS90 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: BPREQI_FIELDS90 enumeration
ms.assetid: bf6f7efc-39f2-46a2-906d-c3647bf89995
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 496f529118f44ec573983362d792b0c68213b05b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="bpreqifields90"></a>BPREQI_FIELDS90
Énumère les valeurs valides qui spécifient les informations à récupérer une demande de point d’arrêt. Cette énumération étend la [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_BPREQI_FIELDS90  
{  
   // VS 8.0 values  
   BPREQI90_BPLOCATION                = 0x0001,  
   BPREQI90_LANGUAGE                  = 0x0002,  
   BPREQI90_PROGRAM                   = 0x0004,  
   BPREQI90_PROGRAMNAME               = 0x0008,  
   BPREQI90_THREAD                    = 0x0010,  
   BPREQI90_THREADNAME                = 0x0020,  
   BPREQI90_PASSCOUNT                 = 0x0040,  
   BPREQI90_CONDITION                 = 0x0080,  
   BPREQI90_FLAGS                     = 0x0100,  
   BPREQI90_ALLOLDFIELDS              = 0x01ff,  
   BPREQI90_VENDOR                    = 0x0200,  
   BPREQI90_CONSTRAINT                = 0x0400,  
   BPREQI90_TRACEPOINT                = 0x0800,  
  
   // Values added in VS 9.0  
   BPREQI90_MACROTRACEPOINT           = 0x1000,  
  
   BPREQI90_ALLFIELDS                 = 0xffff  
};  
typedef DWORD BPREQI_FIELDS90;  
```  
  
```csharp  
public enum enum_BPREQI_FIELDS90  
{  
    // VS 8.0 values  
    BPREQI90_BPLOCATION                = 0x0001,  
    BPREQI90_LANGUAGE                  = 0x0002,  
    BPREQI90_PROGRAM                   = 0x0004,  
    BPREQI90_PROGRAMNAME               = 0x0008,  
    BPREQI90_THREAD                    = 0x0010,  
    BPREQI90_THREADNAME                = 0x0020,  
    BPREQI90_PASSCOUNT                 = 0x0040,  
    BPREQI90_CONDITION                 = 0x0080,  
    BPREQI90_FLAGS                     = 0x0100,  
    BPREQI90_ALLOLDFIELDS              = 0x01ff,  
    BPREQI90_VENDOR                    = 0x0200,  
    BPREQI90_CONSTRAINT                = 0x0400,  
    BPREQI90_TRACEPOINT                = 0x0800,  
  
    // Values added in VS 9.0  
    BPREQI90_MACROTRACEPOINT           = 0x1000,  
  
    BPREQI90_ALLFIELDS                 = 0xffff  
};  
```  
  
#### <a name="parameters"></a>Paramètres  
 BPREQI90_BPLOCATION  
 Initialiser ou utilisez le `bpLocation` champ (emplacement de point d’arrêt) de la [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) ou [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) structure.  
  
 BPREQI90_LANGUAGE  
 Initialiser ou utilisez le `guidLanguage` champ le `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.  
  
 BPREQI90_PROGRAM  
 Initialiser ou utilisez le `pProgram` champ le `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.  
  
 BPREQI90_PROGRAMNAME  
 Initialiser ou utilisez le `bstrProgramName` champ le `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.  
  
 BPREQI90_THREAD  
 Initialiser ou utilisez le `pThread` champ le `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.  
  
 BPREQI90_THREADNAME  
 Initialiser ou utilisez le `bstrThreadName` champ le `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.  
  
 BPREQI90_PASSCOUNT  
 Initialiser ou utilisez le `bpPassCount` champ le `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.  
  
 BPREQI90_CONDITION  
 Initialiser ou utilisez le `bpCondition` champ (condition de point d’arrêt) de la `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.  
  
 BPREQI90_FLAGS  
 Initialiser ou utilisez le `dwFlags` champ le `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.  
  
 BPREQI90_ALLOLDFIELDS  
 Initialiser ou d’utiliser tous les champs de la de la `BP_REQUEST_INFO` structure.  
  
 BPREQI90_VENDOR  
 Initialiser ou utilisez le `guidVendor` champ `BP_REQUEST_INFO2` structure.  
  
 BPREQI90_CONSTRAINT  
 Initialiser ou utilisez le `bstrConstraint` champ `BP_REQUEST_INFO2` structure.  
  
 BPREQI90_TRACEPOINT  
 Initialiser ou utilisez le `bstrTracepoint` champ `BP_REQUEST_INFO2` structure.  
  
 BPREQI90_MACROTRACEPOINT  
 Initialiser ou utilisez le `bstrMacroTracepoint` champ `BP_REQUEST_INFO2` structure. BPREQI_ALLFIELDS n’inclut pas ce champ.  
  
 BPREQI90_ALLFIELDS  
 Spécifie tous les champs pour la `BP_REQUEST_INFO2` structure.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : Msdbg90.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)