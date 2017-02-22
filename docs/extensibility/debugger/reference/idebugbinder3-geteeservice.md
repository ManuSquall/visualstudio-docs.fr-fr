---
title: "IDebugBinder3::GetEEService | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder3::GetEEService"
helpviewer_keywords: 
  - "IDebugBinder3::GetEEService (méthode)"
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugBinder3::GetEEService
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette méthode retourne un service demandé.  
  
## Syntaxe  
  
```cpp  
HRESULT GetEEService(  
   [in] GUID        vendor,  
   [in] GUID        language,  
   [in] GUID        iid,  
   [out] IUnknown** ppService  
);  
```  
  
```c#  
Int GetEEService(  
   Guid       vendor,  
   Guid       language,  
   Guid       iid,  
   out object ppService  
);  
```  
  
#### Paramètres  
 `vendor`  
 \[in\]  `GUID` d'un fournisseur \(une valeur NULL est acceptable\).  
  
 `language`  
 \[in\]  `GUID` d'un langage \(une valeur NULL est acceptable\).  
  
 `iid`  
 \[in\]  `IID` du service à obtenir.  
  
 `ppService`  
 \[out\]  une interface au service demandé.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Passez `IID` pour l'interface d' [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md) \(`IID_IEEVisualizerServiceProvider`\) pour voir si le service du visualiseur de type est disponible.  Dans ce cas, l'évaluateur d'expression peut obtenir l'interface d' [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) pour prendre en charge les visualiseurs de type.  Pour plus d'informations, consultez [Visualisation et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md).  
  
## Voir aussi  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [Visualisation et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md)