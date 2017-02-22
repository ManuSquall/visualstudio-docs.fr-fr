---
title: "IDebugBinder3::GetExceptionObjectAndType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder3::GetExceptionObjectAndType"
helpviewer_keywords: 
  - "IDebugBinder3::GetExceptionObjectAndType (méthode)"
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugBinder3::GetExceptionObjectAndType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode récupère l'exception associée à un objet échéant.  
  
## Syntaxe  
  
```cpp  
HRESULT GetExceptionObjectAndType(  
   IDebugObject** ppException,  
   IDebugField**  ppField  
);  
```  
  
```c#  
int GetExceptionObjectAndType(  
   out IDebugObject ppException,  
   out IDebugField  ppField  
);  
```  
  
#### Paramètres  
 `ppException`  
 \[out\]  Retourne l'objet qui représente l'exception.  
  
 `ppField`  
 \[out\]  Retourne l'objet qui représente un champ spécifique qui a pu provoqué l'exception \(cela peut être une valeur NULL\).  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
> [!NOTE]
>  Pour vérifier s'il existe une exception, vérifiez la valeur retournée par `ppException`: s'il s'agit d'une valeur NULL, aucune exception n'est pas associé à cet objet.  
  
## Voir aussi  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)