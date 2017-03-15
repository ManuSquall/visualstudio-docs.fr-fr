---
title: "IDebugSettingsCallback2::GetMetricDword | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSettingsCallback2::GetMetricDword"
ms.assetid: 831a5a1a-c4af-4520-9fdf-3a731aeff85c
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSettingsCallback2::GetMetricDword
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Extrait la valeur d'un métriques avec son nom.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetMetricDword(  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   DWORD*  pdwValue  
);  
```  
  
```c#  
private int GetMetricDword(  
   string   pszType,  
   ref Guid guidSection,  
   string   pszMetric,  
   out uint pdwValue  
);  
```  
  
#### Paramètres  
 `pszType`  
 \[in\]  Type de la métrique.  
  
 `guidSection`  
 \[in\]  ID unique de la section.  
  
 `pszMetric`  
 \[in\]  Nom de la métrique.  
  
 `pdwValue`  
 \[out\]  Retourne la valeur de la métrique.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)