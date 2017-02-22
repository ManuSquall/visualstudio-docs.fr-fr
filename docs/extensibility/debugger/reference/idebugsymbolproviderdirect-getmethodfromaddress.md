---
title: "IDebugSymbolProviderDirect::GetMethodFromAddress | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSymbolProviderDirect::GetMethodFromAddress"
  - "GetMethodFromAddress"
ms.assetid: 33ffd197-1221-41bc-a9f6-f133ebdcb783
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSymbolProviderDirect::GetMethodFromAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Récupère des informations concernant la méthode à l'adresse spécifiée de débogage.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetMethodFromAddress(  
   IDebugAddress* pAddress,  
   GUID*          pGuid,  
   DWORD*         pAppID,  
   _mdToken*      pTokenClass,  
   _mdToken*      pTokenMethod,  
   DWORD*         pdwOffset,  
   DWORD*         pdwVersion  
);  
```  
  
```c#  
int GetMethodFromAddress(  
   IDebugAddress pAddress,  
   out Guid      pGuid,  
   out uint      pAppID,  
   out uint      pTokenClass,  
   out uint      pTokenMethod,  
   out uint      pdwOffset,  
   out uint      pdwVersion  
);  
```  
  
#### Paramètres  
 `pAddress`  
 \[in\]  déboguez l'adresse qui est représentée par l'interface d' [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .  
  
 `pGuid`  
 \[out\]  identificateur unique du module.  
  
 `pAppID`  
 \[out\]  identificateur du domaine d'application.  
  
 `pTokenClass`  
 \[out\]  Jeton qui représente la classe conteneur.  
  
 `pTokenMethod`  
 \[out\]  jeton qui représente le module.  
  
 `pdwOffset`  
 \[out\]  Un offset en octets du début du paramètre d' `pAddress` .  
  
 `pdwVersion`  
 \[out\]  numéro de version de la méthode.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)