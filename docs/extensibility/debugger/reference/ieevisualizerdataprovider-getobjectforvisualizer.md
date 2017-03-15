---
title: "IEEVisualizerDataProvider::GetObjectForVisualizer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEVisualizerDataProvider::GetObjectForVisualizer"
helpviewer_keywords: 
  - "IEEVisualizerDataProvider::GetObjectForVisualizer (méthode)"
ms.assetid: bd5376fc-13b4-40b7-9a5d-7ba8289f1b24
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IEEVisualizerDataProvider::GetObjectForVisualizer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette méthode obtient l'objet que ce visualiseur représente.  
  
## Syntaxe  
  
```cpp  
HRESULT GetObjectForVisualizer(  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int GetObjectForVisualizer(  
   out IDebugObject ppObject  
);  
```  
  
#### Paramètres  
 `ppObject`  
 \[out\]  l'objet représenté par ce visualiseur  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 il permet à`GetObjectForVisualizer` pour retourner une version mise en cache de l'objet.  Si l'appelant veut vous assurer que l'objet est à jour, il appellera [GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md).  
  
## Voir aussi  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)