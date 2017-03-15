---
title: "IDebugMethodField::IsCustomAttributeDefined | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField::IsCustomAttributeDefined"
helpviewer_keywords: 
  - "IDebugMethodField::IsCustomAttributeDefined (méthode)"
ms.assetid: 1b5d95a8-cc87-4acb-9e6a-3928f3632b7c
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugMethodField::IsCustomAttributeDefined
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

détermine si un attribut personnalisé spécifique a été défini.  
  
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
 Retourne S\_OK si l'attribut personnalisé est défini sur cette méthode, sinon retourne S\_FALSE.  
  
## Voir aussi  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)