---
title: BP_FLAGS90 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9f7192eb7b2fa6d8bc886c0e601788ecba8eebcd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153497"
---
# <a name="bp_flags90"></a>BP_FLAGS90
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Énumère les valeurs valides pour les indicateurs facultatifs. Les indicateurs facultatifs peuvent être utilisés pour spécifier des informations supplémentaires lorsque vous définissez un point d’arrêt. Cette énumération étend l’énumération [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
enum enum_BP_FLAGS90  
{  
   // VS 8.0 values  
   BP90_FLAG_NONE               = 0x0000,  
   BP90_FLAG_MAP_DOCPOSITION    = 0x0001,  
   BP90_FLAG_DONT_STOP          = 0x0002,  
  
   // Values added in VS 9.0  
   BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,  
};  
typedef DWORD BP_FLAGS90;  
```  
  
```csharp  
public enum enum_BP_FLAGS90  
{  
   // VS 8.0 values  
   BP90_FLAG_NONE                = 0x0000,  
   BP90_FLAG_MAP_DOCPOSITION     = 0x0001,  
   BP90_FLAG_DONT_STOP           = 0x0002,  
  
   // Values added in VS 9.0  
   BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,  
};  
```  
  
#### <a name="parameters"></a>Paramètres  
 BP90_FLAG_NONE  
 Ne spécifie aucun indicateur de point d’arrêt.  
  
 BP90_FLAG_MAP_DOCPOSITION  
 Spécifie que le moteur DE débogage (DE) doit mapper le point d’arrêt à l’aide de la position du document. Cela s’applique uniquement aux points d’arrêt définis dans les fichiers sources orientés script tels que les pages de Active Server (ASP).  
  
 BP90_FLAG_DONT_STOP  
 Spécifie que le point d’arrêt doit être traité par le moteur de débogage, mais que le moteur de débogage ne doit finalement pas s’arrêter là ; autrement dit, un objet événement [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) ne doit pas être envoyé. Cet indicateur est conçu pour être utilisé principalement avec les points de trace.  
  
 BP90_FLAG_TRACEPOINT_CONTINUE  
 Utilisé par le moteur de débogage natif pour déterminer si l’état d’exécution doit être effacé. Il diffère de BP90_FLAG_DONT_STOP, car BP90_FLAG_DONT_STOP n’est pas défini si le point de trace exécute une macro.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : Msdbg90. h  
  
 Espace de noms : Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
