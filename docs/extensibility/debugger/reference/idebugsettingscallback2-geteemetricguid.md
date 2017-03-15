---
title: "IDebugSettingsCallback2::GetEEMetricGuid | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSettingsCallback2::GetEEMetricGuid"
ms.assetid: 3d70c19a-595d-44f1-a7b3-a0cf8f15e371
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSettingsCallback2::GetEEMetricGuid
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Extrait l'identificateur unique pour une métrique évaluateur d'expression avec son nom.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetEEMetricGuid(  
   REFGUID guidLang,  
   REFGUID guidVendor,  
   LPCWSTR pszMetric,  
   GUID*   pguidValue  
);  
```  
  
```c#  
HRESULT GetEEMetricGuid(  
   ref Guid guidLang,  
   ref Guid guidVendor,  
   string   pszMetric,  
   out Guid pguidValue  
);  
```  
  
#### Paramètres  
 `guidLang`  
 \[in\]  identificateur unique du langage de programmation.  
  
 `guidVendor`  
 \[in\]  identificateur unique du fournisseur.  
  
 `pszMetric`  
 \[in\]  Nom de la métrique.  
  
 `pguidValue`  
 \[out\]  Retourne l'identificateur unique de la métrique.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)