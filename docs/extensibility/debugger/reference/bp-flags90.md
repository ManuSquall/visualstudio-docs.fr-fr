---
title: BP_FLAGS90 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 5e958be77ca266af30556fa8c03c580eea94b903
ms.contentlocale: fr-fr
ms.lasthandoff: 09/06/2017

---
# <a name="bpflags90"></a>BP_FLAGS90
Énumère les valeurs valides pour les indicateurs facultatifs. Les indicateurs facultatifs peuvent être utilisés pour spécifier des informations supplémentaires lorsque vous définissez un point d’arrêt. Cette énumération étend la [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
 Spécifie que le moteur de débogage (DE) doit mapper le point d’arrêt à l’aide de la position du document. Cela s’applique uniquement aux points d’arrêt définis dans les fichiers de code source orienté sur le script Active Server Pages (ASP).  
  
 BP90_FLAG_DONT_STOP  
 Spécifie que le point d’arrêt doit être traité par le moteur de débogage, mais que le moteur de débogage en fin de compte ne doit pas arrêter Autrement dit, un [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) objet d’événement ne doit pas être envoyé. Cet indicateur est conçu pour être utilisé avec des points de trace.  
  
 BP90_FLAG_TRACEPOINT_CONTINUE  
 Utilisé par le moteur de débogage natif pour déterminer si l’état d’exécution pas à pas doit être effacé. Il diffère BP90_FLAG_DONT_STOP car BP90_FLAG_DONT_STOP n’est pas défini si le point de trace s’exécute une macro.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : Msdbg90.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
