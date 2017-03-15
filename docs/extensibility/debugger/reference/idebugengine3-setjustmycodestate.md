---
title: "IDebugEngine3::SetJustMyCodeState | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine3::SetJustMyCodeState"
helpviewer_keywords: 
  - "IDebugEngine3::SetJustMyCodeState"
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugEngine3::SetJustMyCodeState
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode indique au moteur de débogage à propos de les informations d'état de JustMyCode.  
  
## Syntaxe  
  
```cpp  
HRESULT SetJustMyCodeState(  
   BOOL           fUpdate,  
   DWORD          dwModules,  
   JMC_CODE_SPEC* rgJMCSpec  
);  
```  
  
```c#  
int SetJustMyCodeState(  
   int             fUpdate,   
   uint            dwModules,   
   JMC_CODE_SPEC[] rgJMCSpec  
);  
```  
  
#### Paramètres  
 `fUpdate`  
 \[in\]  Une valeur différente de zéro \(`TRUE`\) pour mettre à jour les informations les plus récentes, zéro \(`FALSE`\) pour réinitialiser toutes les informations \(en ignorant n'importe quoi défini précédemment\).  
  
 `dwModules`  
 \[in\]  Numéro de structures d'informations dans `rgJMCSpec.`  
  
 `rgJMCSpec`  
 \[in\]  Tableau de structures de [JMC\_CODE\_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) à utiliser.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, le code d'erreur de retour.  
  
## Notes  
 JustMyCode est le concept de déboguer uniquement le code qui appartient à un utilisateur et à ignorer tout le code intermédiaire tel que le système code\-égal si le code source est disponible pour le code système.  
  
## Voir aussi  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)   
 [JMC\_CODE\_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)