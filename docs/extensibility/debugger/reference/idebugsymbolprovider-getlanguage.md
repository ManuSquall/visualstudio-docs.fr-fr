---
title: "IDebugSymbolProvider::GetLanguage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugSymbolProvider::GetLanguage"
helpviewer_keywords: 
  - "IDebugSymbolProvider::GetLanguage (méthode)"
ms.assetid: e4142183-3d8b-418f-907f-4ee4c753d8ce
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugSymbolProvider::GetLanguage
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode extrait le langage utilisé pour compiler le code à l'adresse de débogage.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetLanguage(   
   IDebugAddress* pAddress,  
   GUID*          pguidLanguage,  
   GUID*          pguidLanguageVendor  
);  
```  
  
```c#  
int GetLanguage(  
   IDebugAddress pAddress,   
   out Guid      pguidLanguage,   
   out Guid      pguidLanguageVendor  
);  
```  
  
#### Paramètres  
 `pAddress`  
 \[in\]  un objet d'adresse représenté par une interface d' [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .  
  
 `pguidLanguage`  
 \[out\]  Retourne `GUID` qui spécifie le langage.  
  
 `pguidLanguageVendor`  
 \[out\]  Retourne `GUID` qui spécifie le fournisseur de langage.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Le moteur de débogage appelle cette méthode pour obtenir les informations dont il a besoin sélectionner l'évaluateur d'expression correct.  
  
## Voir aussi  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)