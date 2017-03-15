---
title: "IEEVisualizerServiceProvider::CreateVisualizerService | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEVisualizerServiceProvider::CreateVisualizerService"
helpviewer_keywords: 
  - "IEEVisualizerServiceProvider::CreateVisualizerService (méthode)"
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEEVisualizerServiceProvider::CreateVisualizerService
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode crée un service du visualiseur.  
  
## Syntaxe  
  
```cpp  
HRESULT CreateVisualizerService(  
   IDebugBinder*              binder,  
   IDebugSymbolProvider*      pSymProv,  
   IDebugAddress*             pAddress,  
   IEEVisualizerDataProvider* dataProvider,  
   IEEVisualizerService**     ppService  
);  
```  
  
```c#  
int CreateVisualizerService(  
   IDebugBinder binder,  
   IDebugSymbolProvider      pSymProv,  
   IDebugAddress             pAddress,  
   IEEVisualizerDataProvider dataProvider,  
   out IEEVisualizerService  ppService  
);  
```  
  
#### Paramètres  
 `binder`  
 \[in\]  l'objet d' [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) passé à [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md).  
  
 `pSymProv`  
 \[in\]  l'objet d' [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) passé à `IDebugParsedExpression::EvaluateSync`.  
  
 `pAddress`  
 \[in\]  l'objet d' [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) passé à `IDebugParsedExression::EvaluateSync`.  
  
 `dataProvider`  
 \[in\]  Un objet qui implémente l'interface d' [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) \(fournie par l'évaluateur d'expression\).  
  
 `ppService`  
 \[out\]  le service créé.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 `binder`, `pSymProv`, les paramètres et tous d' `pAddress` ont été passés à la méthode d' `IDebugParsedExpression::EvaluateSync` .  `CreateVisualizerService` doit être appelé uniquement à partir de `IDebugParsedExpression::EvaluateSync` dans le cadre de la prise en charge du évaluateur d'expression les visualiseurs de type.  
  
## Voir aussi  
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)