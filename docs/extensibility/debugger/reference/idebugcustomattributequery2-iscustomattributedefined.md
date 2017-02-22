---
title: "IDebugCustomAttributeQuery2::IsCustomAttributeDefined | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCustomAttributeQuery2::IsCustomAttributeDefined"
helpviewer_keywords: 
  - "IDebugCustomAttributeQuery2::IsCustomAttributeDefined"
ms.assetid: 5c07cc52-6d2d-42df-9d76-9f1f769641db
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugCustomAttributeQuery2::IsCustomAttributeDefined
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

détermine si un attribut personnalisé existe de nom.  
  
## Syntaxe  
  
```cpp#  
HRESULT IsCustomAttributeDefined(   
   LPCOLESTR pszCustomAttributeName  
);  
```  
  
```c#  
int IsCustomAttributeDefined(  
   [In] string pszCustomAttributeName  
);  
```  
  
#### Paramètres  
 `pszCustomAttributeName`  
 \[in\]  Chaîne contenant le nom de l'attribut personnalisé pour rechercher.  
  
## Valeur de retour  
 Retourne S\_OK si l'attribut personnalisé est défini sur ce champ, sinon retourne S\_FALSE.  
  
## Notes  
 Pour obtenir les octets d'attribut liés à l'attribut personnalisé, appelez la méthode d' [GetCustomAttributeByName](../Topic/IDebugCustomAttributeQuery2::GetCustomAttributeByName.md) .  
  
## Voir aussi  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)