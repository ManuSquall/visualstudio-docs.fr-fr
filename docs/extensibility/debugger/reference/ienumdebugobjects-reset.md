---
title: "IEnumDebugObjects::Reset | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugObjects::Reset"
helpviewer_keywords: 
  - "IEnumDebugObjects::Reset (méthode)"
ms.assetid: 4a245e47-cc39-4177-b83d-083ea0e3190f
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IEnumDebugObjects::Reset
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
 Une fois que cette méthode soit appelée, l'appel suivant à [Suivant](../../../extensibility/debugger/reference/ienumdebugobjects-next.md) retourne le premier élément de l'énumération.  
  
## Voir aussi  
 [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)   
 [Suivant](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)