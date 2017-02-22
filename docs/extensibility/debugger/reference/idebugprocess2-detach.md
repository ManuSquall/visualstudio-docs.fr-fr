---
title: "IDebugProcess2::Detach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::Detach"
helpviewer_keywords: 
  - "IDebugProcess2::Detach"
ms.assetid: ee2b9084-2db1-4e49-a1d9-387284b7c3f8
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess2::Detach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Détache le débogueur de ce processus en arrêter tous les programmes dans le processus.  
  
## Syntaxe  
  
```cpp#  
HRESULT Detach(   
   void   
);  
```  
  
```c#  
int Detach();  
```  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Tous les programmes et le processus continuent de s'exécuter, mais ne sont plus partie de la session de débogage.  Une fois l'opération de détachement terminée, pas plus les événements de débogage pour cela ne traitent \(et ses programmes\) seront envoyés.  
  
## Voir aussi  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)