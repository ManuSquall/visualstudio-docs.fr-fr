---
title: "IDebugSettingsCallback2::GetMetricGuid | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSettingsCallback2::GetMetricGuid"
ms.assetid: 91092763-3362-4857-adf0-231bc1254206
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSettingsCallback2::GetMetricGuid
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Extrait l'identificateur unique d'un métriques avec son nom.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetMetricGuid(  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   GUID*   pguidValue  
);  
```  
  
```c#  
private int GetMetricGuid(  
   string   pszType,  
   ref Guid guidSection,  
   string   pszMetric,  
   out Guid pguidValue  
);  
```  
  
#### Paramètres  
 `pszType`  
 \[in\]  Type de la métrique.  
  
 `guidSection`  
 \[in\]  ID unique de la section.  
  
 `pszMetric`  
 \[in\]  Nom de la métrique.  
  
 `pguidValue`  
 \[out\]  Retourne l'identificateur unique de la métrique.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)