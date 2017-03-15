---
title: "IDebugReference2::SetValueAsString | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugReference2::SetValueAsString"
helpviewer_keywords: 
  - "IDebugReference2::SetValueAsString"
ms.assetid: 9a508ced-fd54-44f5-bb42-ec15c80384d7
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugReference2::SetValueAsString
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

définit la valeur d'une référence d'une chaîne.  Réservé à une utilisation future.  
  
## Syntaxe  
  
```cpp#  
HRESULT SetValueAsString (   
   LPCOLESTR pszValue,  
   DWORD     dwRadix,  
   DWORD     dwTimeout  
);  
```  
  
```c#  
int SetValueAsString (   
   string pszValue,  
   uint   dwRadix,  
   uint   dwTimeout  
);  
```  
  
#### Paramètres  
 `pszValue`  
 \[in\]  La valeur comme une chaîne.  
  
 `dwRadix`  
 \[in\]  La base à utiliser lors de la mise en forme toute information numériques.  
  
 `dwTimeout`  
 \[in\]  Durée maximale, en millisecondes, d'attendre avant le retour de cette méthode.  Utilisation `INFINITE` d'attente dure indéfiniment.  
  
## Valeur de retour  
 Retourne toujours `E_NOTIMPL`.  
  
## Voir aussi  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)