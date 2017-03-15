---
title: "IEEVisualizerService::GetCustomViewerList | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEVisualizerService::GetCustomViewerList"
helpviewer_keywords: 
  - "IEEVisualizerService::GetCustomViewerList (méthode)"
ms.assetid: 249d26ca-914f-43af-a400-8162477223f4
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEEVisualizerService::GetCustomViewerList
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode retourne une liste des visualiseurs de type que ce service connaît.  
  
## Syntaxe  
  
```cpp  
HRESULT GetCustomViewerList(  
   ULONG                celtSkip,  
   ULONG                celtRequested,  
   DEBUG_CUSTOM_VIEWER* rgViewers,  
   ULONG*               pceltFetched  
);  
```  
  
```c#  
int GetCustomViewerList(  
   uint                  celtSkip,  
   uint                  celtRequested,  
   DEBUG_CUSTOM_VIEWER[] rgViewers,  
   out uint              pceltFetched  
);  
```  
  
#### Paramètres  
 `celtSkip`  
 \[in\]  Numéro de visualiseurs à ignorer sur.  
  
 `celRequested`  
 \[in\]  Numéro de visualiseurs à récupérer \(spécifie également la taille du tableau d' `rgViewers` \).  
  
 `rgViewers`  
 \[in, out\]  Tableau de structures de [DEBUG\_CUSTOM\_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) à accomplir.  
  
 `pceltFetched`  
 \[out\]  Numéro de visualiseurs réellement récupérés.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) passe la demande à cette méthode dans le cadre de son prise en charge des visualiseurs de type.  Si l'évaluateur d'expression fournit également des visionneuses personnalisées pour le même type, il peut ajouter les structures de manière appropriée remplies\- de [DEBUG\_CUSTOM\_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) pour ces visionneuses personnalisées à la liste.  Assurez \-vous qu' [GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md) reflète les visionneuses supplémentaires.  
  
 Consultez [Visualiseur de type et de la visionneuse personnalisée](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) pour plus d'informations sur les différences entre les visualiseurs et les visionneuses.  
  
## Voir aussi  
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [DEBUG\_CUSTOM\_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md)   
 [Visualiseur de type et de la visionneuse personnalisée](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)