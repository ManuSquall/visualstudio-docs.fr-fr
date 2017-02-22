---
title: "IDebugCoreServer2::GetPort | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer2::GetPort"
helpviewer_keywords: 
  - "IDebugCoreServer2::GetPort"
ms.assetid: 3f5ea4a8-6085-4600-980a-9e48f8b5be56
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugCoreServer2::GetPort
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Récupère un port spécifique.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetPort(   
   REFGUID       guidPort,  
   IDebugPort2** ppPort  
);  
```  
  
```c#  
int GetPort(   
   ref Guid        guidPort,  
   out IDebugPort2 ppPort  
);  
```  
  
#### Paramètres  
 `guidPort`  
 \[in\]  GUID du port à récupérer.  
  
 `ppPort`  
 \[out\]  Retourne un objet d' [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) représentant le port souhaité.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  Retourne `E_PORTSUPPLIER_NO_PORT` s'il n'y a aucun port avec l'identificateur donné.  
  
## Voir aussi  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)