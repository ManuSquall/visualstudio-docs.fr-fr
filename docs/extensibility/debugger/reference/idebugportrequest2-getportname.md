---
title: "IDebugPortRequest2::GetPortName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortRequest2::GetPortName"
helpviewer_keywords: 
  - "IDebugPortRequest2::GetPortName"
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPortRequest2::GetPortName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient le nom du port.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetPortName(   
   BSTR* pbstrPortName  
);  
```  
  
```c#  
int GetPortName(   
   out string pbstrPortName  
);  
```  
  
#### Paramètres  
 `pbstrPortName`  
 \[out\]  Retourne le nom du port.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 L'interface d' [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) est généralement passée d'un package de débogage \(le client\) à un fournisseur de port \(le serveur\) pour établir une connexion à un port.  La fois le package de débogage et le fournisseur de port connaissent des options possibles pour le port.  Si une chaîne simple peut décrire le port, la méthode d' `IDebugPortRequest2::GetPortName` dispose de suffisamment d'informations pour établir la connexion.  Sinon, des interfaces supplémentaires peuvent être fournies par le client, qui peut être obtenu par le serveur en utilisant `IDebugPortRequest2::QueryInterface`.  
  
## Voir aussi  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)