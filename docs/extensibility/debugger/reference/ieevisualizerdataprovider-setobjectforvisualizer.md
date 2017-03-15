---
title: "IEEVisualizerDataProvider::SetObjectForVisualizer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEVisualizerDataProvider::SetObjectForVisualizer"
helpviewer_keywords: 
  - "IEEVisualizerDataProvider::SetObjectForVisualizer (méthode)"
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEEVisualizerDataProvider::SetObjectForVisualizer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode convertit l'objet que le visualiseur représente.  
  
## Syntaxe  
  
```cpp  
HRESULT SetObjectForVisualizer(  
   IDebugObject*  pNewObject,  
   BSTR*          error,  
   IDebugObject** pException  
);  
```  
  
```c#  
int SetObjectForVisualizer(  
   IDebugObject     pNewObject,  
   out string       error,  
   out IDebugObject pException  
);  
```  
  
#### Paramètres  
 `pNewObject`  
 \[in\]  L'objet à définir.  
  
 `error`  
 \[out\]  Si une erreur s'est produite définissant l'objet, conserve de cette chaîne le message d'erreur.  
  
 `pException`  
 \[out\]  Si une erreur s'est produite, conserve de cet objet des informations sur les exceptions.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 elle appartient à l'implémenteur pour déterminer comment les informations sur l'erreur sont retournées.  Toutefois, il est possible que certaines appelants puissent uniquement se voir si un objet exception a été retourné pour savoir cas de erreur, cette méthode retourne toujours un objet exception en cas de erreur.  La chaîne d'erreur doit également être fournie au cas où l'appelant devriez utiliser de celle\-ci.  
  
## Voir aussi  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)