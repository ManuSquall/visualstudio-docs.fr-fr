---
title: "IPropertyProxyProvider::GetPropertyProxy | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IPropertyProxyProvider::GetPropertyProxy"
helpviewer_keywords: 
  - "IPropertyProxyProvider::GetPropertyProxy"
ms.assetid: 3ebb7515-5bfe-48f4-9b8d-721b8f664eb6
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IPropertyProxyProvider::GetPropertyProxy
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Extrait l'interface de proxy de propriété pour l'ID spécifié de proxy  
  
## Syntaxe  
  
```cpp#  
HRESULT GetPropertyProxy(  
   DWORD                  dwID,  
   IPropertyProxyEESide** proxy  
);  
```  
  
```c#  
int GetPropertyProxy(  
   uint                     dwID,  
   out IPropertyProxyEESide proxy  
);  
```  
  
#### Paramètres  
 `dwID`  
 \[in\]  ID du proxy souhaité de propriété.  
  
 `proxy`  
 \[out\]  Retourne un objet d' [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) .  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Pour prendre en charge les visualiseurs externes de type, cette méthode effectue le suivi en général à l'appel de la méthode d' [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md) .  Consultez [Visualisation et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md) pour savoir comment l'IEEVisualizerService est obtenu.  
  
## Voir aussi  
 [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)   
 [Visualisation et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md)