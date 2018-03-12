---
title: EXCEPTION_STATE | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 69c0f1f4f9396d57af1381962e12b0d3201aa3ef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="exceptionstate"></a>EXCEPTION_STATE
Spécifie l’état d’exception.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_EXCEPTION_STATE {   
   EXCEPTION_NONE                          = 0x0000,  
   EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,  
   EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,  
   EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,  
   EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,  
   EXCEPTION_STOP_ALL                      = 0x00FF,  
   EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,  
  
   // These are for exception types only  
   EXCEPTION_CODE_SUPPORTED                = 0x1000,  
   EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,  
   EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,  
   EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,  
  
   // These are no longer used  
   EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,  
   EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,  
   EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,  
   EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,  
};  
typedef DWORD EXCEPTION_STATE;  
```  
  
```csharp  
public enum enum_EXCEPTION_STATE {   
   EXCEPTION_NONE                          = 0x0000,  
   EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,  
   EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,  
   EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,  
   EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,  
   EXCEPTION_STOP_ALL                      = 0x00FF,  
   EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,  
  
   // These are for exception types only  
   EXCEPTION_CODE_SUPPORTED                = 0x1000,  
   EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,  
   EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,  
   EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,  
  
   // These are no longer used  
   EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,  
   EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,  
   EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,  
   EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,  
};  
```  
  
## <a name="members"></a>Membres  
 EXCEPTION_NONE  
 N’arrêtez pas à l’exception.  
  
 EXCEPTION_STOP_FIRST_CHANCE  
 Arrêter le premier déclenchement de l’événement d’exception. Lors de la description d’un événement d’exception, cet indicateur indique que l’événement d’exception est un événement d’exception de première chance.  
  
 EXCEPTION_STOP_SECOND_CHANCE  
 Arrêter à la deuxième déclenchement de l’événement d’exception. Lors de la description d’un événement d’exception, indique que l’événement d’exception est un événement d’exception de deuxième chance.  
  
 EXCEPTION_STOP_USER_FIRST_CHANCE  
 Arrêter le premier déclenchement d’une exception du mode utilisateur. Lors de la description d’un événement d’exception, indique que l’événement d’exception est un événement d’exception de première chance.  
  
 EXCEPTION_STOP_USER_UNCAUGHT  
 Arrêter lorsqu’une exception du mode utilisateur n’est pas interceptée. Lors de la description d’un événement d’exception, indique que l’événement d’exception est un événement d’exception en mode utilisateur non interceptée.  
  
 EXCEPTION_STOP_ALL  
 Arrêtez sur n’importe quelle exception. Pas utilisé lors de la description d’un événement d’exception.  
  
 EXCEPTION_CANNOT_BE_CONTINUED  
 Lors de la description d’un événement d’exception, indique que l’exception ne peut pas être poursuivie à partir de.  
  
 EXCEPTION_CODE_SUPPORTED  
 Indique que l’exception comporte du code prenant en charge. Utilisé lors de l’affichage d’une exception  
  
 EXCEPTION_CODE_DISPLAY_IN_HEX  
 Indique que le code d’exception doit être affiché en notation hexadécimale. Utilisé lors de l’affichage d’une exception.  
  
 EXCEPTION_JUST_MY_CODE_SUPPORTED  
 Indique que le code d’exception prend en charge JustMyCode. Utilisé lors de l’affichage d’une exception.  
  
 EXCEPTION_MANAGED_DEBUG_ASSISTANT  
 Indique que le débogueur de code managé doit gérer les exceptions. Si ce n’est pas le cas, ensemble, le débogueur par défaut gère les exceptions. Il est passé à la [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) méthode mais pas dans le [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) structure.  
  
 EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT  
 OBSOLÈTE, N’UTILISEZ PAS.  
  
 EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT  
 OBSOLÈTE, N’UTILISEZ PAS.  
  
 EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT  
 OBSOLÈTE, N’UTILISEZ PAS.  
  
 EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT  
 OBSOLÈTE, N’UTILISEZ PAS.  
  
## <a name="remarks"></a>Notes  
 Utilisé en tant que le `dwState` membre de la [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) structure pour indiquer l’état de l’exception et ce qui peut être fait à son sujet.  
  
 Ces valeurs sont également transmis à la [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) méthode pour définir l’état de toutes les exceptions.  
  
 Ces indicateurs peuvent être combinées avec une opération OR au niveau du bit.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)