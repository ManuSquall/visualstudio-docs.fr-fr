---
title: "IPropertyProxyEESide::InitSourceDataProvider | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IPropertyProxyEESide::InitSourceDataProvider"
helpviewer_keywords: 
  - "IPropertyProxyEESide::InitSourceDataProvider"
ms.assetid: 5156f593-5052-4e3a-9d02-081916fb342d
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IPropertyProxyEESide::InitSourceDataProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Initialise les données sources pour cet objet et retourne un objet contenant les données initiales.  
  
## Syntaxe  
  
```cpp#  
HRESULT InitSourceDataProvider(  
   IEEDataStorage** dataOut  
);  
```  
  
```c#  
int InitSourceDataProvider(  
   out IEEDataStorage dataOut  
);  
```  
  
#### Paramètres  
 `dataOut`  
 \[out\]  Retourne un objet d' [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Cette méthode provoque quelle que soit nécessaire pour initialiser un objet qui peut retourner une interface d' [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) sur les données de l'objet.  Cela permet aux données de l'objet à restituer et, si autorisé, modifiées par un visualiseur de type.  
  
## Voir aussi  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)