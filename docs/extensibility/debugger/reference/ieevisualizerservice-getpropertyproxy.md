---
title: "IEEVisualizerService::GetPropertyProxy | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEVisualizerService::GetPropertyProxy"
helpviewer_keywords: 
  - "IEEVisualizerService::GetPropertyProxy (méthode)"
ms.assetid: 748750f4-76e7-4580-9da2-afba07681b37
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEEVisualizerService::GetPropertyProxy
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode retourne un proxy pour un objet de propriété.  
  
## Syntaxe  
  
```cpp  
HRESULT GetPropertyProxy(  
   DWORD                  dwID,  
   IPropertyProxyEESide** proxy  
);  
```  
  
```c#  
int GetPropertyProxy(  
   uint                     dwID,  
   out IPropertyProxyEESide proxy  
);  
```  
  
#### Paramètres  
 `dwID`  
 \[in\]  ID du proxy de propriété à récupérer.  
  
 `proxy`  
 \[out\]  Proxy souhaité implémenté dans une interface d' [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) .  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) passe la demande à cette méthode dans le cadre de son prise en charge des visualiseurs de type.  
  
## Voir aussi  
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)