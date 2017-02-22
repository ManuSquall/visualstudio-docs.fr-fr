---
title: "IDebugAlias::Dispose | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugAlias::Dispose"
helpviewer_keywords: 
  - "IDebugAlias::Dispose (méthode)"
ms.assetid: e84909a4-d378-4f48-bf25-2c014c77c8e3
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugAlias::Dispose
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Marque cet alias pour suppression.  
  
## Syntaxe  
  
```cpp  
HRESULT Dispose();  
```  
  
```c#  
int Dispose();  
```  
  
#### Paramètres  
 Aucun  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
## Notes  
 une fois que cette méthode est appelée, l'alias n'est plus disponible.  
  
## Voir aussi  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)