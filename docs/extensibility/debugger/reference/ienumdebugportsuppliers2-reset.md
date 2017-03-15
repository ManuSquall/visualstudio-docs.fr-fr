---
title: "IEnumDebugPortSuppliers2::Reset | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugPortSuppliers2::Next"
helpviewer_keywords: 
  - "IEnumDebugPortSuppliers2::Next"
ms.assetid: f69cbacf-da9d-4b22-b8a2-abd9b8c131f2
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumDebugPortSuppliers2::Reset
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
 Une fois que cette méthode soit appelée, l'appel suivant à la méthode d' [Suivant](../Topic/IEnumDebugPortSuppliers2::Next.md) retourne le premier élément de l'énumération.  
  
## Voir aussi  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)