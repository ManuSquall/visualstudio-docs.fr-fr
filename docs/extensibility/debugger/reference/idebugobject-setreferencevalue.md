---
title: "IDebugObject::SetReferenceValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject::SetReferenceValue"
helpviewer_keywords: 
  - "IDebugObject::SetReferenceValue (méthode)"
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugObject::SetReferenceValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

définit la valeur de référence de cet objet.  
  
## Syntaxe  
  
```cpp#  
HRESULT SetReferenceValue(   
   IDebugObject* pObject  
);  
```  
  
```c#  
int SetReferenceValue(  
   [In] IDebugObject pObject  
);  
```  
  
#### Paramètres  
 `pObject`  
 \[in\]  un objet d' [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) représentant la nouvelle valeur de référence.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
## Notes  
 Cette méthode attribue à cet objet d' [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) une référence à la valeur de l'objet donné dans le paramètre d' `pObject` , levant avant toute référence précédente.  notez que cet objet d' `IDebugObject` doit déjà être un type référence.  
  
## Voir aussi  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)