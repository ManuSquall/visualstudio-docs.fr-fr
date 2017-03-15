---
title: "IDebugManagedObject::SetFromManagedObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugManagedObject::SetFromManagedObject"
helpviewer_keywords: 
  - "IDebugManagedObject::SetFromManagedObject (méthode)"
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugManagedObject::SetFromManagedObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

définit la valeur de l'instance de l'objet de classe de valeur de l'instance de la classe de valeur fournie comme paramètre.  
  
## Syntaxe  
  
```cpp#  
HRESULT SetFromManagedObject(   
   IUnknown* pManagedObject  
);  
```  
  
```c#  
int SetFromManagedObject(  
   object pManagedObject  
);  
```  
  
#### Paramètres  
 `pManagedObject`  
 \[in\]  Une interface qui représente l'objet managé qui contient la nouvelle valeur.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
## Notes  
 cette méthode est utilisée pour modifier l'objet managé comme représenté par l'objet d' [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) .  
  
## Voir aussi  
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)