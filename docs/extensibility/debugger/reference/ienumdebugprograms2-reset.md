---
title: "IEnumDebugPrograms2::Reset | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugPrograms2::Reset"
helpviewer_keywords: 
  - "IEnumDebugPrograms2::Reset"
ms.assetid: b289242b-24ea-4df3-a811-20b0c8a903d6
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumDebugPrograms2::Reset
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

réinitialise l'énumération au premier élément.  
  
## Syntaxe  
  
```cpp#  
HRESULT Reset(  
   void  
);  
```  
  
```c#  
int Reset();  
```  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Une fois que cette méthode soit appelée, l'appel suivant à la méthode d' [Suivant](../Topic/IEnumDebugPrograms2::Next.md) retourne le premier élément de l'énumération.  
  
## Voir aussi  
 [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)