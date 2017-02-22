---
title: "IEnumDebugFields::Reset | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugFields::Reset"
helpviewer_keywords: 
  - "IEnumDebugFields::Reset (méthode)"
ms.assetid: 38ff61e4-0120-42e8-971a-16be6050b425
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IEnumDebugFields::Reset
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette méthode réinitialise l'énumération au premier élément.  
  
## Syntaxe  
  
```cpp#  
HRESULT Reset(void);  
```  
  
```c#  
int Reset();  
```  
  
#### Paramètres  
 Aucun  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Une fois que cette méthode soit appelée, l'appel suivant à [Suivant](../../../extensibility/debugger/reference/ienumdebugfields-next.md) retourne le premier élément de l'énumération.  
  
## Voir aussi  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [Suivant](../../../extensibility/debugger/reference/ienumdebugfields-next.md)