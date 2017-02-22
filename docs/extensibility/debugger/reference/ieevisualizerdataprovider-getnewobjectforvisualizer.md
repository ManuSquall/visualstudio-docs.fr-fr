---
title: "IEEVisualizerDataProvider::GetNewObjectForVisualizer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEVisualizerDataProvider::GetNewObjectForVisualizer"
helpviewer_keywords: 
  - "IEEVisualizerDataProvider::GetNewObjectForVisualizer (méthode)"
ms.assetid: a898d549-4898-4fde-aad1-e8bb89129652
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEEVisualizerDataProvider::GetNewObjectForVisualizer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode extrait un objet pour le visualiseur.  Cette méthode crée toujours un nouvel objet de l'objet existant.  
  
## Syntaxe  
  
```cpp  
HRESULT GetNewObjectForVisualizer(  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int GetNewObjectForVisualizer(  
   out IDebugObject ppObject  
);  
```  
  
#### Paramètres  
 `ppObject`  
 \[out\]  le nouvel objet.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 `This method` réévalue l'objet qu'il représente actuellement et retourne le résultat sous forme de objet.  L'objet existant est mis à jour à la suite de l'évaluation.  
  
## Voir aussi  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)