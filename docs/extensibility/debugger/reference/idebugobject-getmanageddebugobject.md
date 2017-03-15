---
title: "IDebugObject::GetManagedDebugObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject::GetManagedDebugObject"
helpviewer_keywords: 
  - "IDebugObject::GetManagedDebugObject (méthode)"
ms.assetid: cb89692e-7657-47ff-846d-311943521951
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugObject::GetManagedDebugObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

crée une copie de l'objet managé dans l'espace d'adressage du moteur de débogage.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetManagedDebugObject(   
   IDebugManagedObject** ppObject  
);  
```  
  
```c#  
int GetManagedDebugObject(  
   out IDebugManagedObject ppObject  
);  
```  
  
#### Paramètres  
 `ppObject`  
 \[out\]  Retourne un objet d' [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) représentant l'objet managé nouvellement créée.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  Retourne E\_FAIL si cet [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) ne représente pas une instance de classe managée de valeur.  
  
## Notes  
 cet objet d' [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) doit représenter une instance de classe managée de valeur, telle qu'une instance d' `System.Decimal` .  En établissant une copie locale, il élimine la charge d'appeler [Évaluer](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) .  
  
## Voir aussi  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)