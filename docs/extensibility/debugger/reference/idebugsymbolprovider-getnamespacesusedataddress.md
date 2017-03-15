---
title: "IDebugSymbolProvider::GetNamespacesUsedAtAddress | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugSymbolProvider::GetNamespacesUsedAtAddress"
helpviewer_keywords: 
  - "IDebugSymbolProvider::GetNamespacesUsedAtAddress (méthode)"
ms.assetid: 392de54b-9af0-4567-953b-1b41acd1e05c
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugSymbolProvider::GetNamespacesUsedAtAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode crée un énumérateur pour les espaces de noms associés à l'adresse de débogage.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetNamespacesUsedAtAddress(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int GetNamespacesUsedAtAddress(  
   IDebugAddress        pAddress,  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### Paramètres  
 `pAddress`  
 \[in\]  l'adresse de débogage.  
  
 `ppEnum`  
 \[out\]  retourne un énumérateur d' [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) pour les espaces de noms.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Il peut exister plusieurs espaces de noms associés à une adresse donnée de débogage, par exemple, des espaces de noms imbriqués ou plusieurs instructions d' `using` .  
  
## Voir aussi  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)