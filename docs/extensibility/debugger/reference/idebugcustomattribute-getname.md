---
title: "IDebugCustomAttribute::GetName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCustomAttribute::GetName"
helpviewer_keywords: 
  - "IDebugCustomAttribute::GetName"
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugCustomAttribute::GetName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient le nom de l'attribut personnalisé.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetName(   
   BSTR* bstrName  
);  
```  
  
```c#  
int GetName(  
   out string bstrName  
);  
```  
  
#### Paramètres  
 `bstrName`  
 \[out\]  Retourne une chaîne contenant le nom de l'attribut personnalisé.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
## Notes  
 le nommé retourné par cette méthode correspond au nom de la classe utilisée pour déclarer l'attribut.  Cela ne corresponde pas exactement au nom de la classe d'attributs personnalisés lui\-même comme c\# permet le suffixe « attribut » à supprimer d'un nom d'attribut personnalisé lorsqu'il est utilisé dans une déclaration.  
  
## Voir aussi  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)