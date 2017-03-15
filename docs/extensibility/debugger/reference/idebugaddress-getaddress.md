---
title: "IDebugAddress::GetAddress | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugAddress::GetAddress"
helpviewer_keywords: 
  - "IDebugAddress:GetAddress (méthode)"
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugAddress::GetAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Retourne une structure qui décrivent un objet et son emplacement dans sa portée ou conteneur.  
  
## Syntaxe  
  
```cpp  
HRESULT GetAddress (  
   DEBUG_ADDRESS * pAddress  
);  
```  
  
```c#  
int GetAddress(  
   DEBUG_ADDRESS[] pAddress  
);  
```  
  
#### Paramètres  
 `pAddress`  
 \[in, out\]  Une structure de [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) qui est terminée par cette méthode.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
## Notes  
 La structure de [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) est passée à cette méthode, qui qu'il remplisse il dans avec les informations appropriées.  Comment ces informations sont interprétées dépend du type d'informations retournées et de gestionnaire de symboles lui\-même.  Pour plus d'informations, consultez [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md).  
  
## Voir aussi  
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)