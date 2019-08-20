---
title: EXCEPTION_STATE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4e30d9cc9df592cc6feb97c14449dbc6a122ec63
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68149357"
---
# <a name="exceptionstate"></a>EXCEPTION_STATE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Spécifie l’état d’exception.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 Arrêter au premier déclenchement de l’événement d’exception. Lorsque vous décrivez un événement d’exception, cet indicateur indique que l’événement d’exception est un événement d’exception de première chance.  
  
 EXCEPTION_STOP_SECOND_CHANCE  
 Arrêter au deuxième déclenchement de l’événement d’exception. Lorsque vous décrivez un événement d’exception, indique que l’événement d’exception est un événement d’exception de la seconde chance.  
  
 EXCEPTION_STOP_USER_FIRST_CHANCE  
 Arrêter au premier déclenchement d’une exception du mode utilisateur. Lorsque vous décrivez un événement d’exception, indique que l’événement d’exception est un événement d’exception de première chance utilisateur.  
  
 EXCEPTION_STOP_USER_UNCAUGHT  
 Arrêter lorsqu’une exception de mode utilisateur n’est pas interceptée. Lorsque vous décrivez un événement d’exception, indique que l’événement d’exception est un événement d’exception en mode utilisateur non interceptées.  
  
 EXCEPTION_STOP_ALL  
 Arrêtez sur n’importe quelle exception. Pas utilisé lors de la description d’un événement d’exception.  
  
 EXCEPTION_CANNOT_BE_CONTINUED  
 Lorsque vous décrivez un événement d’exception, indique que l’exception ne peut pas être poursuivie à partir de.  
  
 EXCEPTION_CODE_SUPPORTED  
 Indique que l’exception comporte du code qui l’accompagnent. Utilisés pour afficher une exception  
  
 EXCEPTION_CODE_DISPLAY_IN_HEX  
 Indique que le code d’exception doit être affiché au format hexadécimal. Utilisé dans l’affichage d’une exception.  
  
 EXCEPTION_JUST_MY_CODE_SUPPORTED  
 Indique que le code d’exception prend en charge JustMyCode. Utilisé dans l’affichage d’une exception.  
  
 EXCEPTION_MANAGED_DEBUG_ASSISTANT  
 Indique que le débogueur de code managé doit gérer les exceptions. Si ce n’est pas le cas, ensemble, le débogueur par défaut gère les exceptions. Ces données sont transmises à la [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) (méthode) et pas dans le [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) structure.  
  
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
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)
