---
title: "IDebugCustomAttribute::GetAttributeTypeField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCustomAttribute::GetAttributeTypeField"
helpviewer_keywords: 
  - "IDebugCustomAttribute::GetAttributeTypeField"
ms.assetid: d6ce26d5-42ba-44c1-8659-0516db5bc82d
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugCustomAttribute::GetAttributeTypeField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient le type de classe personnalisée d'attributs.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetAttributeTypeField(   
   IDebugClassField** ppCAType  
);  
```  
  
```c#  
int GetAttributeTypeField(  
   out IDebugClassField ppCAType  
);  
```  
  
#### Paramètres  
 `ppCAType`  
 \[out\]  Retourne l'objet d' [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) qui représente la classe dont l'attribut personnalisé est une instance.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
## Notes  
 un attribut personnalisé est toujours une classe.  cette méthode permet d'accéder à un objet d' [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) qui décrit cette classe.  
  
## Voir aussi  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)