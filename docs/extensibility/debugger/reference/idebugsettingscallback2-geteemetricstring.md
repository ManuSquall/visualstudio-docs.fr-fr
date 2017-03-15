---
title: "IDebugSettingsCallback2::GetEEMetricString | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSettingsCallback2::GetEEMetricString"
ms.assetid: 85e3c093-6a91-4101-ab32-d8ac6eed4918
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSettingsCallback2::GetEEMetricString
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Extrait la chaîne de valeur d'un métriques évaluateur d'expression avec son nom.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetEEMetricString(  
   REFGUID guidLang,  
   REFGUID guidVendor,  
   LPCWSTR pszMetric,  
   BSTR*   pbstrValue  
);  
```  
  
```c#  
private int GetEEMetricString(  
   ref Guid   guidLang,  
   ref Guid   guidVendor,  
   string     pszMetric,  
   out string pbstrValue  
);  
```  
  
#### Paramètres  
 `guidLang`  
 \[in\]  identificateur unique du langage de programmation.  
  
 `guidVendor`  
 \[in\]  identificateur unique du fournisseur.  
  
 `pszMetric`  
 \[in\]  Nom de la métrique.  
  
 `pbstrValue`  
 \[out\]  Retourne la chaîne métrique de valeur.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)