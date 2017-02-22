---
title: "IDebugObject2::GetBackingFieldForProperty | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject2::GetBackingFieldForProperty"
helpviewer_keywords: 
  - "IDebugObject2::GetBackingFieldForProperty (méthode)"
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugObject2::GetBackingFieldForProperty
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient le champ ou la variable \(le cas échéant\) qui peuvent sauvegarder la propriété représentée par cet objet.  
  
## Syntaxe  
  
```cpp  
HRESULT GetBackingFieldForProperty(  
   IDebugObject2** ppObject  
);  
```  
  
```c#  
int GetBackingFieldForProperty(  
   out IDebugObject2 ppObject  
);  
```  
  
#### Paramètres  
 `ppObject`  
 \[out\]  un objet d' [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) décrivant le champ de stockage.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
## Notes  
 L'objet d' [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) représente une propriété de la classe de code managé, c. autrement dit., une méthode avec une commande get et\/ou un accesseur set.  De telles propriétés requièrent généralement d'une variable pour contenir la valeur manipulées par la propriété.  cette variable est appelé le champ de stockage.  S'il n'y a aucun champ de stockage pour l'objet, ensuite veillez à retourner une valeur NULL : certains appelants ne peuvent pas prêter attention à la valeur de retour mais les conservent à la place déterminer si une valeur NULL est retournée dans `ppObject`.  
  
## Voir aussi  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)