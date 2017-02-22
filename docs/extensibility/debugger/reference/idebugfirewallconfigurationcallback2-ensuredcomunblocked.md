---
title: "IDebugFirewallConfigurationCallback2::EnsureDCOMUnblocked | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "EnsureDCOMUnblocked"
  - "IDebugFirewallConfigurationCallback2::EnsureDCOMUnblocked"
ms.assetid: acf54d27-32a6-47e7-aba6-3cc0004edc7f
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugFirewallConfigurationCallback2::EnsureDCOMUnblocked
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Demande que le débogage distant de bloc de pare\-feu pas.  
  
## Syntaxe  
  
```cpp#  
HRESULT EnsureDCOMUnblocked(   
    Void  
);  
```  
  
```c#  
public int EnsureDCOMUnblocked();  
```  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md)