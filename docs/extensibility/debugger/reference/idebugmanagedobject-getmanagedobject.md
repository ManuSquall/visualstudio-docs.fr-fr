---
title: "IDebugManagedObject::GetManagedObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugManagedObject::GetManagedObject"
helpviewer_keywords: 
  - "IDebugManagedObject::GetManagedObject (méthode)"
ms.assetid: 6abe1402-6aad-41e6-8ec1-ae12d5945992
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugManagedObject::GetManagedObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Retourne une interface qui représente l'objet managé.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetManagedObject(   
   IUnknown** ppManagedObject  
);  
```  
  
```cpp#  
int GetManagedObject(  
   out object ppManagedObject  
);  
```  
  
#### Paramètres  
 `ppManagedObject`  
 \[out\]  Retourne une interface qui représente l'objet managé.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
## Notes  
 L'interface retournée par cette méthode peut être interrogé pour toute interface implémentée par la classe managée, qui autorise ses méthodes à appeler.  
  
## Voir aussi  
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)