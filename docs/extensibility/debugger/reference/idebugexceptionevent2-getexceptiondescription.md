---
title: "IDebugExceptionEvent2::GetExceptionDescription | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExceptionEvent2::GetExceptionDescription"
helpviewer_keywords: 
  - "IDebugExceptionEvent2::GetExceptionDescription"
ms.assetid: d07d458f-5729-47e4-9b77-1bd59c61a75a
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugExceptionEvent2::GetExceptionDescription
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient une description affichable de l'exception.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetExceptionDescription(   
   BSTR* pbstrDescription  
);  
```  
  
```c#  
int GetExceptionDescription(   
   out string pbstrDescription  
);  
```  
  
#### Paramètres  
 `pbstrDescription`  
 \[out\]  Retourne une description affichable de l'exception.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 La chaîne retournée par cette méthode est généralement le nom de l'exception et s'affiche dans la fenêtre de **Sortie** lorsque l'exception se produit.  
  
## Voir aussi  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)