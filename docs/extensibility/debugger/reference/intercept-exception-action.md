---
title: "INTERCEPT_EXCEPTION_ACTION | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "INTERCEPT_EXCEPTION_ACTION"
helpviewer_keywords: 
  - "Énumération de INTERCEPT_EXCEPTION_ACTION"
ms.assetid: e647f1eb-2932-4447-8c78-3b0d706fb972
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# INTERCEPT_EXCEPTION_ACTION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Spécifie les actions à exécuter en désactivant des exceptions.  
  
## Syntaxe  
  
```cpp#  
enum enum_INTERCEPT_EXCEPTION_ACTION  
{  
   IEA_INTERCEPT = 0x0001  
}  
typedef DWORD INTERCEPT_EXCEPTION_ACTION;  
```  
  
```c#  
public enum enum_INTERCEPT_EXCEPTION_ACTION  
{  
   IEA_INTERCEPT = 0x0001  
}  
```  
  
#### Paramètres  
 IEA\_INTERCEPT  
 Permet d'arrêter l'exception actuelle.  C'est la seule valeur prise en charge actuellement et doit être spécifié.  
  
## Notes  
 ces valeurs sont passées dans la méthode d' [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) .  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)