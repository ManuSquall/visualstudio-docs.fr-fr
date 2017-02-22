---
title: "IPropertyProxyEESide::CreateReplacementObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IPropertyProxyEESide::CreateReplacementObject"
helpviewer_keywords: 
  - "IPropertyProxyEESide::CreateReplacementObject"
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IPropertyProxyEESide::CreateReplacementObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

crée une copie d'un détail d'objet de données à l'évaluateur d'expression \(EE\).  
  
## Syntaxe  
  
```cpp  
HRESULT CreateReplacementObject(  
   IEEDataStorage*  dataIn,  
   IEEDataStorage** dataOut  
);  
```  
  
```c#  
int CreateReplacementObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### Paramètres  
 `dataIn`  
 \[in\]  un objet d' [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) maintenant les données à copier.  
  
 `dataOut`  
 \[out\]  Retourne un nouvel objet d' `IEEDataStorage` .  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Cette méthode reçoit un objet d' [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) représentant un tableau d'octets.  Cet objet de données entrant n'est pas généralement implémenté par l'évaluateur d'expression.  Toutefois, l'objet retourné par cette méthode est toujours implémenté par l'évaluateur d'expression, dans laquelle permet l'évaluateur d'expression implémenter l'interface de `IEEDataStorage` la logique de classe est souhaitée.  
  
 notez que les données fournies par l'objet entrant d' `IEEDataStorage` doivent être les mêmes données dans l'objet sortant d' `IEEDataStorage` .  
  
## Voir aussi  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)