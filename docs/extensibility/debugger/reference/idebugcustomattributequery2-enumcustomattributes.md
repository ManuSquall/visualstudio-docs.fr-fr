---
title: "IDebugCustomAttributeQuery2::EnumCustomAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCustomAttributeQuery2::EnumCustomAttributes"
helpviewer_keywords: 
  - "IDebugCustomAttributeQuery2::EnumCustomAttributes"
ms.assetid: 94bfce74-aa3d-45f0-8e04-5715faf85217
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugCustomAttributeQuery2::EnumCustomAttributes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient un énumérateur pour tous les attributs personnalisés attachés à ce champ.  
  
## Syntaxe  
  
```cpp#  
HRESULT EnumCustomAttributes(   
   IEnumDebugCustomAttributes** ppEnum  
);  
```  
  
```c#  
int EnumCustomAttributes(  
   out IEnumDebugCustomAttributes ppEnum  
);  
```  
  
#### Paramètres  
 `ppEnum`  
 \[out\]  Retourne un objet d' [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) représentant la liste d'attributs personnalisés ; sinon, retourne la valeur qu'une valeur NULL s'il n'y a aucune personnalisé les attributs.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ou S\_FALSE s'il n'y a pas d'attributs personnalisés dans ce champ.  Sinon, retourne un code d'erreur ;  
  
## Notes  
 Un champ peut avoir plusieurs attributs personnalisés.  
  
## Voir aussi  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)