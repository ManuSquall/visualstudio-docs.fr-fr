---
title: "IDebugCoreServer3::GetServerFriendlyName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer3::GetServerFriendlyName"
helpviewer_keywords: 
  - "IDebugCoreServer3::GetServerFriendlyName"
ms.assetid: 7035b904-b3d7-4d9b-98d9-65714b8a8b9f
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugCoreServer3::GetServerFriendlyName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

extrait un nom convivial pour le serveur.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetServerFriendlyName(  
   BSTR* pbstrName  
);  
```  
  
```c#  
int GetServerFriendlyName(  
   out string pbstrName  
);  
```  
  
#### Paramètres  
 `pbstrName`  
 \[out\]  Retourne un nom convivial pour le serveur.  
  
> [!NOTE]
>  L'appelant est chargé de libérer la chaîne.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, le code d'erreur de retour.  
  
## Notes  
 pour les serveurs utilisateur\-lancés, le nom retourné par cette méthode est le nom complet du serveur.  Pour les serveurs automobile\-lancés, le nom est celui de l'ordinateur que le serveur s'exécute.  
  
 Pour un nom orienté ordinateur, appelez la méthode d' [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md) .  
  
## Voir aussi  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)