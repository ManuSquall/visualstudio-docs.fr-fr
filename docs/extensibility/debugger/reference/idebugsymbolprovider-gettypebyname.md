---
title: "IDebugSymbolProvider::GetTypeByName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugSymbolProvider::GetTypeByName"
helpviewer_keywords: 
  - "IDebugSymbolProvider::GetTypeByName (méthode)"
ms.assetid: b9d88d3b-8b75-484a-b9cc-dc8c0fbb4bc8
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugSymbolProvider::GetTypeByName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette méthode mappe un nom de symbole à un type de symbole.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetTypeByName(   
   LPCOLESTR     pszClassName,  
   NAME_MATCH    nameMatch,  
   IDebugField** ppField  
);  
```  
  
```c#  
int GetTypeByName(  
   string          pszClassName,   
   NAME_MATCH      nameMatch,   
   out IDebugField ppField  
);  
```  
  
#### Paramètres  
 `pszClassName`  
 \[in\]  Le nom du symbole.  
  
 `nameMatch`  
 \[in\]  Sélectionne le type de correspondance, par exemple, respecte pas la casse.  Valeur d'énumération [NAME\_MATCH](../../../extensibility/debugger/reference/name-match.md).  
  
 `ppField`  
 \[out\]  Retourne le type de symbole comme un objet d' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 cette méthode est une version générique d' [GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md).  
  
## Voir aussi  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [NAME\_MATCH](../../../extensibility/debugger/reference/name-match.md)   
 [GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)