---
title: "IDebugSymbolProviderDirect::GetCurrentModulesInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSymbolProviderDirect::GetCurrentModulesInfo"
  - "GetCurrentModulesInfo"
ms.assetid: b3b45ed2-ea4e-4389-b78a-11fc9796a6c1
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugSymbolProviderDirect::GetCurrentModulesInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Récupère des informations à propos de les modules au groupe de symbole.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetCurrentModulesInfo(  
   unsigned long * pCount,  
   GUID *          ppGuids,  
   DWORD *         pADIds,  
   DWORD *         pCurrentState,  
   IUnknown **     ppCDModItfs  
);  
```  
  
```c#  
int GetCurrentModulesInfo(  
   uint       pCount,  
   Guid       ppGuids,  
   uint       pADIds,  
   uint       pCurrentState,  
   out object ppCDModItfs  
);  
```  
  
#### Paramètres  
 `pCount`  
 \[in\]  Numéro de modules dans le tableau d' `ppGuids` .  
  
 `ppGuids`  
 \[in\]  rangez qui contient les identificateurs uniques pour les modules.  
  
 `pADIds`  
 \[in\]  Identificateurs des domaines d'application.  
  
 `pCurrentState`  
 \[in\]  état actuel du groupe de symbole.  
  
 `ppCDModItfs`  
 \[out\]  Retourne un objet qui contient les modules au groupe de symbole.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)