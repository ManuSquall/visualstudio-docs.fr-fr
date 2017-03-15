---
title: "IDebugExpressionEvaluator::SetLocale | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionEvaluator::SetLocale"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator::SetLocale (méthode)"
ms.assetid: d3d2027d-74e2-4ae6-bcc7-59d12f873b7c
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugExpressionEvaluator::SetLocale
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode définit la langue à utiliser pour créer des résultats imprimables.  
  
## Syntaxe  
  
```cpp#  
HRESULT SetLocale(   
   WORD wLangID  
);  
```  
  
```c#  
int SetLocale(  
   ushort wLangID  
);  
```  
  
#### Paramètres  
 `wLangID`  
 \[in\]  l'identificateur de langue.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Cette méthode peut être appelée plusieurs fois pendant que l'évaluateur d'expression \(EE\) est chargé, afin que l'évaluateur d'expression doit pouvoir basculer les langages à la volée.  L'évaluateur d'expression utilise ces paramètres régionaux pour retourner les messages d'erreur et les chaînes dans la langue appropriée.  
  
## Voir aussi  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)