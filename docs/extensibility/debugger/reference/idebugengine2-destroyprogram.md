---
title: "IDebugEngine2::DestroyProgram | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::DestroyProgram"
helpviewer_keywords: 
  - "IDebugEngine2::DestroyProgram"
ms.assetid: 0c9e2698-c70f-4770-a7bb-39650e9c3a1f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEngine2::DestroyProgram
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Signale à un moteur de \(DE\) débogage que le programme spécifié a été atypiquement terminé et que le De doit nettoyer toutes les références au programme et envoyer un programme destroy l'événement.  
  
## Syntaxe  
  
```cpp#  
HRESULT DestroyProgram(   
   IDebugProgram2* pProgram  
);  
```  
  
```cpp#  
int DestroyProgram(   
   IDebugProgram2 pProgram  
);  
```  
  
#### Paramètres  
 `pProgram`  
 \[in\]  Un objet d' [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) qui représente le programme qui a été atypiquement complet.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Une fois que cette méthode soit appelée, le De envoie ensuite un événement d' [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) vers le gestionnaire \(SDM\) de débogage de session.  
  
 Cette méthode n'est pas implémentée \(retourne `E_NOTIMPL`\) si le De s'exécute dans le même processus que le programme débogué.  Cette méthode est implémentée uniquement si le De s'exécute dans le même processus que le SDM.  
  
## Voir aussi  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)