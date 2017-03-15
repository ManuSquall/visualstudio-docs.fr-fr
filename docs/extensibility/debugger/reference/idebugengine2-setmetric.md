---
title: "IDebugEngine2::SetMetric | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2:::SetMetric"
helpviewer_keywords: 
  - "IDebugEngine2:::SetMetric"
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# IDebugEngine2::SetMetric
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode définit une valeur de Registre appelé " métriques.  
  
## Syntaxe  
  
```cpp#  
HRESULT SetMetric(  
   LPCOLESTR pszMetric,  
   VARIANT   varValue  
);  
```  
  
```c#  
int SetMetric(  
   string pszMetric,  
   object varValue  
);  
```  
  
#### Paramètres  
 `pszMetric`  
 \[in\]  le nom métrique.  
  
 `varValue`  
 \[in\]  spécifie la valeur métrique.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Un métriques est une valeur de Registre utilisée pour modifier le comportement d'un moteur de débogage ou pour publier la fonctionnalité prise en charge.  Cette méthode peut transférer l'appel au format approprié de la fonction de [« Helpers » du Kit de développement logiciel pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) , `SetMetric`.  
  
## Voir aussi  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [« Helpers » du Kit de développement logiciel pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)