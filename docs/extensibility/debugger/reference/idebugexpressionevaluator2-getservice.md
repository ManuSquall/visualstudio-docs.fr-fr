---
title: "IDebugExpressionEvaluator2::GetService | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator2::GetService"
  - "Méthode GetService"
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpressionEvaluator2::GetService
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Récupère un objet de service avec son identificateur unique.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetService (  
   GUID        uid,  
   IUnknown ** ppService  
);  
```  
  
```c#  
int GetService (  
   Guid       uid,  
   out object ppService  
);  
```  
  
#### Paramètres  
 `uid`  
 \[in\]  Identificateur unique du service à récupérer.  
  
 `ppService`  
 \[out\]  Retourne un objet qui représente le service.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Cela peut être consommé par un tiers évaluateur d'expression pour obtenir des services d'un autre évaluateur d'expression.  Par exemple, cette méthode peut être utilisée pour obtenir l'interface pour le service de visualiseur de l'évaluateur d'expression par défaut.  Il est improbable assignation de tiers évaluateurs d'expression implémenter cette interface.  
  
## Voir aussi  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)