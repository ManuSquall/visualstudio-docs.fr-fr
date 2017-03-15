---
title: "IDebugSymbolProviderDirect::GetMetaDataImport | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetMetaDataImport"
  - "IDebugSymbolProviderDirect::GetMetaDataImport"
ms.assetid: b51a492c-af00-4b08-93fb-6c19ee4916aa
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSymbolProviderDirect::GetMetaDataImport
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Extrait des informations d'importation de métadonnées.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetMetaDataImport (  
    GUID*      guid,  
    DWORD      appID,  
    IUnknown** ppImport  
);  
```  
  
```c#  
int GetMetaDataImport (  
    Guid       guid,  
    uint       appID,  
    out object ppImport  
);  
```  
  
#### Paramètres  
 `guid`  
 \[in\]  ID unique du module.  
  
 `appID`  
 \[in\]  Identificateur du domaine d'application.  
  
 `ppImport`  
 \[out\]  Retourne un objet qui contient les informations d'importation de métadonnées.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)