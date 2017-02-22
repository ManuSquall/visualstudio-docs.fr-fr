---
title: "IDebugSettingsCallback2::GetEELocalObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSettingsCallback2::GetEELocalObject"
ms.assetid: e69a3469-a049-420c-b918-c48a1e7b9baf
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugSettingsCallback2::GetEELocalObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Récupère un objet local évaluateur d'expression donné le nom métrique.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetEELocalObject(  
   REFGUID     guidLang,  
   REFGUID     guidVendor,  
   LPCWSTR     pszMetric,  
   IUnknown ** ppUnk  
);  
```  
  
```c#  
private int GetEELocalObject(  
   ref Guid          guidLang,  
   ref Guid          guidVendor,  
   string            pszMetric,  
   out System.Object ppUnk  
);  
```  
  
#### Paramètres  
 `guidLang`  
 \[in\]  identificateur unique du langage de programmation.  
  
 `guidVendor`  
 \[in\]  identificateur unique du fournisseur.  
  
 `pszMetric`  
 \[in\]  Nom de la métrique.  
  
 `ppUnk`  
 \[out\]  Retourne l'objet local de votre évaluateur d'expression.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)