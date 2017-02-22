---
title: "IEnumDebugBoundBreakpoints2::Reset | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugBoundBreakpoints2::Reset"
helpviewer_keywords: 
  - "IEnumDebugBoundBreakpoints2::Reset"
ms.assetid: 0f0522a5-6a97-4c4e-859b-cc4476e6c527
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumDebugBoundBreakpoints2::Reset
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
 Une fois que cette méthode soit appelée, l'appel suivant à la méthode d' [Suivant](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md) retourne le premier élément de l'énumération.  
  
## Voir aussi  
 [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)