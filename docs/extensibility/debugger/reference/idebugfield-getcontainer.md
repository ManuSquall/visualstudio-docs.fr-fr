---
title: "IDebugField::GetContainer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugField::GetContainer"
helpviewer_keywords: 
  - "IDebugField::GetContainer (méthode)"
ms.assetid: 6d6c8213-6181-4adf-9584-3e4cac163dd8
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugField::GetContainer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode extrait le conteneur d'un champ.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetContainer(   
   IDebugContainerField** ppContainerField  
);  
```  
  
```c#  
int GetContainer(  
   out IDebugContainerField ppContainerField  
);  
```  
  
#### Paramètres  
 `ppContainerField`  
 \[out\]  Retourne le conteneur comme représenté par l'interface d' [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) .  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Si ce champ n'a pas un conteneur, `ppContainerField` sera retourné une valeur NULL.  
  
## Voir aussi  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)