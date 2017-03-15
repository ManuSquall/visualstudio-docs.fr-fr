---
title: "IDebugEngine2::SetLocale | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::SetLocale"
helpviewer_keywords: 
  - "IDebugEngine2::SetLocale"
ms.assetid: cd0d2cf1-2aac-43da-a830-4bb3d696c219
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEngine2::SetLocale
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

définit les paramètres régionaux du moteur de débogage \(DE\).  
  
## Syntaxe  
  
```cpp#  
HRESULT SetLocale(   
   WORD wLangID  
);  
```  
  
```c#  
int SetLocale(   
   ushort wLangID  
);  
```  
  
#### Paramètres  
 `wLangID`  
 \[in\]  Spécifie les paramètres régionaux.  par exemple, 1033 pour l'anglais.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Cette méthode est appelée par le gestionnaire de débogage de session \(SDM\) pour propager les paramètres régionaux de l'IDE afin que les chaînes retournées par le De soient correctement localisées.  
  
## Voir aussi  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)