---
title: "EXCEPTION_STATE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EXCEPTION_STATE"
helpviewer_keywords: 
  - "Énumération de EXCEPTION_STATE"
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# EXCEPTION_STATE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

spécifie l'état d'exception.  
  
## Syntaxe  
  
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
  
```c#  
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
  
## Membres  
 EXCEPTION\_NONE  
 Ne arrêtez pas à l'exception.  
  
 EXCEPTION\_STOP\_FIRST\_CHANCE  
 Niveau de la première mise à déclencher de l'exception.  En décrivant un événement exception, cet indicateur indique que l'événement exception est un événement exception de première\-chance.  
  
 EXCEPTION\_STOP\_SECOND\_CHANCE  
 Arrêt à la deuxième mise à déclencher de l'exception.  En décrivant un événement exception, indique que l'événement exception est un événement de seconde chance d'exception.  
  
 EXCEPTION\_STOP\_USER\_FIRST\_CHANCE  
 Niveau de la première mise à déclencher d'une exception utilisateur.  En décrivant un événement exception, indique que l'événement exception est un événement exception utilisateur de première\-chance.  
  
 EXCEPTION\_STOP\_USER\_UNCAUGHT  
 Arrêtez lorsqu'une exception utilisateur n'est pas interceptée.  En décrivant un événement exception, indique que l'événement exception est un événement non interceptée d'exception utilisateur.  
  
 EXCEPTION\_STOP\_ALL  
 arrêt sur toute exception.  Non utilisé en décrivant un événement exception.  
  
 \_BE\_CONTINUED D'EXCEPTION\_CAN NOT  
 En décrivant un événement exception, indique que l'exception ne peut se poursuivre de.  
  
 EXCEPTION\_CODE\_SUPPORTED  
 Indique que l'exception a code la prise en charge.  utilisé en affichant une exception  
  
 EXCEPTION\_CODE\_DISPLAY\_IN\_HEX  
 Indique que le code d'exception doit être affiché au format hexadécimal.  utilisé en affichant une exception.  
  
 EXCEPTION\_JUST\_MY\_CODE\_SUPPORTED  
 Indique que le code d'exception prend en charge JustMyCode.  utilisé en affichant une exception.  
  
 EXCEPTION\_MANAGED\_DEBUG\_ASSISTANT  
 Indique que le débogueur de code managé doit gérer des exceptions.  sinon défini, le débogueur par défaut gère les exceptions.  Cela est passé à la méthode d' [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) et pas utilisé dans la structure d' [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md) .  
  
 EXCEPTION\_STOP\_FIRST\_CHANCE\_USE\_PARENT  
 OBSOLÈTE, NE SUR UTILISEZ NOT.  
  
 EXCEPTION\_STOP\_SECOND\_CHANCE\_USE\_PARENT  
 OBSOLÈTE, NE SUR UTILISEZ NOT.  
  
 EXCEPTION\_STOP\_USER\_FIRST\_CHANCE\_USE\_PARENT  
 OBSOLÈTE, NE SUR UTILISEZ NOT.  
  
 EXCEPTION\_STOP\_USER\_SECOND\_CHANCE\_USE\_PARENT  
 OBSOLÈTE, NE SUR UTILISEZ NOT.  
  
## Notes  
 Utilisé comme membre d' `dwState` de la structure d' [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md) pour indiquer l'état de l'exception et ce qui peut être fait le concernant.  
  
 ces valeurs sont également passées à la méthode d' [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) pour définir l'état de toutes les exceptions.  
  
 Ces indicateurs peuvent être combinées avec une opération de bits OR.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)