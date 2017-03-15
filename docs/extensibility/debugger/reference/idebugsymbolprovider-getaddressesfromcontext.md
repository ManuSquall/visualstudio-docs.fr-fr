---
title: "IDebugSymbolProvider::GetAddressesFromContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugSymbolProvider::GetAddressesFromContext"
helpviewer_keywords: 
  - "IDebugSymbolProvider::GetAddressesFromContext (méthode)"
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugSymbolProvider::GetAddressesFromContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode mappe un contexte de document en un tableau d'adresses de débogage.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetAddressesFromContext(   
   IDebugDocumentContext2* pDocContext,  
   BOOL                    fStatmentOnly,  
   IEnumDebugAddresses**   ppEnumBegAddresses,  
   IEnumDebugAddresses**   ppEnumEndAddresses  
);  
```  
  
```c#  
int GetAddressesFromContext(  
   IDebugDocumentContext2  pDocContext,  
   bool                    fStatmentOnly,  
   out IEnumDebugAddresses ppEnumBegAddresses,  
   out IEnumDebugAddresses ppEnumEndAddresses  
);  
```  
  
#### Paramètres  
 `pDocContext`  
 \[in\]  le contexte de document.  
  
 `fStatmentOnly`  
 \[in\]  Si la valeur TRUE, limites que le débogage l'adresse à une seule instruction.  
  
 `ppEnumBegAddresses`  
 \[out\]  Retourne un énumérateur pour les adresses de début de débogage associées à cette instruction ou ligne.  
  
 `ppEnumEndAddresses`  
 \[out\]  Retourne un énumérateur d' [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) pour les adresses de débogage de fin associées à cette instruction ou ligne.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Un contexte de document indique généralement une plage de lignes sources.  Cette méthode fournit les adresses de début et de fin de débogage associées à ces lignes.  Certains langages autorisent les instructions qui couvrent plusieurs lignes, ou des lignes qui contient plusieurs instructions.  Cette méthode fournit une balise pour limiter les adresses de débogage à une seule instruction.  
  
 Il est possible qu'une seule instruction peut contenir plusieurs adresses de débogage, comme dans le cas de les modèles.  
  
## Voir aussi  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [GetAddressesFromPosition](../Topic/IDebugSymbolProvider::GetAddressesFromPosition.md)   
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)