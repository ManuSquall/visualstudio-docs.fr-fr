---
title: "IDebugExpressionEvaluator::SetRegistryRoot | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionEvaluator::SetRegistryRoot"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator::SetRegistryRoot (méthode)"
ms.assetid: 790886d8-1975-4d3c-9a75-cd86c1faf4ca
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugExpressionEvaluator::SetRegistryRoot
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette méthode définit la racine de Registre.  utilisé pour déboguer côte à côte.  
  
## Syntaxe  
  
```cpp#  
HRESULT SetRegistryRoot (   
   LPCOLESTR ustrRegistryRoot  
);  
```  
  
```c#  
int SetRegistryRoot(  
   string ustrRegistryRoot  
);  
```  
  
#### Paramètres  
 `ustrRegistryRoot`  
 \[in\]  la nouvelle racine de Registre.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 La racine de Registre spécifiée est généralement définie lorsque l'évaluateur d'expression est premier instancié qui pointe vers la clé de Registre pour une version spécifique de Visual Studio \(\\SOFTWARE\\Microsoft\\VisualStudio HKEY\_LOCAL\_MACHINE \\*X.Y*, où *X.Y* est un numéro de version\).  
  
## Voir aussi  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)