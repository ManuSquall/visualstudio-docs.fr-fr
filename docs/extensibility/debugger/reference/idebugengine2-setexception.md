---
title: "IDebugEngine2::SetException | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::SetException"
helpviewer_keywords: 
  - "IDebugEngine2::SetException"
ms.assetid: e6f5ec48-09e8-4b9b-9dc9-55f8d883f1b7
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEngine2::SetException
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Spécifie comment le moteur de \(DE\) débogage doit gérer une exception donnée.  
  
## Syntaxe  
  
```cpp#  
HRESULT SetException(   
   EXCEPTION_INFO* pException  
);  
```  
  
```c#  
int SetException(   
   EXCEPTION_INFO[] pException  
);  
```  
  
#### Paramètres  
 `pException`  
 \[in\]  une structure d' [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md) qui décrit l'exception et comment la déboguer.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Un De a pu être chargé pour arrêter le programme générer une exception à la première chance, seconde chance, ou pas du tout.  
  
## Voir aussi  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md)