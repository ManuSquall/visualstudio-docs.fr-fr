---
title: "IPropertyProxyEESide::GetInitialData | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IPropertyProxyEESide::GetInitialData"
helpviewer_keywords: 
  - "IPropertyProxyEESide::GetInitialData"
ms.assetid: 36cceb19-2604-4ef9-b42b-5dd30cbe24b1
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IPropertyProxyEESide::GetInitialData
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Retourne les données initiales pour cet objet.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetInitialData(  
   IEEDataStorage** dataOut  
);  
```  
  
```c#  
int GetInitialData(  
   out IEEDataStorage dataOut  
);  
```  
  
#### Paramètres  
 `dataOut`  
 \[out\]  Retourne un objet d' [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) contenant les données initiales de cet objet.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)