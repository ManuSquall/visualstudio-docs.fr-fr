---
title: "IEEVisualizerService::GetCustomViewerCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEVisualizerService::GetCustomViewerCount"
helpviewer_keywords: 
  - "IEEVisualizerService::GetCustomViewerCount (méthode)"
ms.assetid: f7b095c2-e538-4352-8cad-d4c6d4f6bdbc
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEEVisualizerService::GetCustomViewerCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode extrait le nombre de visualiseurs de type disponibles de ce service.  
  
## Syntaxe  
  
```cpp  
HRESULT GetCustomViewerCount(  
   ULONG* pcelt  
);  
```  
  
```c#  
int GetCustomViewerCount(  
   out uint pcelt  
);  
```  
  
#### Paramètres  
 `pcelt`  
 \[out\]  Retourne le nombre de visualiseurs de type disponibles.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 [GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md) passe la demande à cette méthode dans son prise en charge des visualiseurs de type.  
  
## Voir aussi  
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md)