---
title: "IDebugSymbolProvider::GetContainerField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugSymbolProvider::GetContainerField"
helpviewer_keywords: 
  - "IDebugSymbolProvider::GetContainerField (méthode)"
ms.assetid: d6b56b4f-a96b-4fa7-87c1-bac4e58fa766
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugSymbolProvider::GetContainerField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode extrait le champ qui contient l'adresse de débogage.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetContainerField(   
   IDebugAddress*         pAddress,  
   IDebugContainerField** ppContainerField  
);  
```  
  
```c#  
int GetContainerField(  
   IDebugAddress            pAddress,   
   out IDebugContainerField ppContainerField  
);  
```  
  
#### Paramètres  
 `pAddress`  
 \[in\]  L'adresse telle qu'elle est représentée par une interface d' [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .  
  
 `ppContainerField`  
 \[out\]  Retourne un champ de conteneur représenté par une interface d' [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) .  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)