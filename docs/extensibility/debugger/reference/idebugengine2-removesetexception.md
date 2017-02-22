---
title: "IDebugEngine2::RemoveSetException | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::RemoveSetException"
helpviewer_keywords: 
  - "IDebugEngine2::RemoveSetException"
ms.assetid: bdd25097-0e9d-4218-b417-0497ea48d2e8
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugEngine2::RemoveSetException
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Supprime l'exception spécifié elle n'est plus gérée par le moteur de débogage.  
  
## Syntaxe  
  
```cpp#  
HRESULT RemoveSetException(   
   EXCEPTION_INFO* pException  
);  
```  
  
```c#  
int RemoveSetException(   
   EXCEPTION_INFO[] pException  
);  
```  
  
#### Paramètres  
 `pException`  
 \[in\]  une structure d' [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md) qui décrit l'exception à supprimer.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 L'exception supprimée doit avoir été précédemment définie par un rappel à la méthode d' [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) .  
  
 Pour supprimer toutes les exceptions définies immédiatement, appelez la méthode d' [RemoveAllSetExceptions](../Topic/IDebugEngine2::RemoveAllSetExceptions.md) .  
  
## Voir aussi  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md)