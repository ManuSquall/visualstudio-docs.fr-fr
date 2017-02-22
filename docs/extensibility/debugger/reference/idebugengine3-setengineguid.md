---
title: "IDebugEngine3::SetEngineGuid | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine3::SetEngineGuid"
helpviewer_keywords: 
  - "IDebugEngine3::SetEngineGuid"
ms.assetid: 8bdfa05d-feb7-4d98-abac-77825a04c50f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEngine3::SetEngineGuid
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette méthode définit `GUID`\(DE\) du moteur de débogage.  
  
## Syntaxe  
  
```cpp  
HRESULT SetEngineGuid(  
   GUID* guidEngine  
);  
```  
  
```  
[C#]  
int SetEngineGuid(  
   ref Guid guidEngine  
);  
```  
  
#### Paramètres  
 `guidEngine`  
 \[in\]  `GUID` du moteur.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, le code d'erreur de retour.  
  
## Voir aussi  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)