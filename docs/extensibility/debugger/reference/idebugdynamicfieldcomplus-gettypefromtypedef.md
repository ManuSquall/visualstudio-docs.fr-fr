---
title: "IDebugDynamicFieldCOMPlus::GetTypeFromTypeDef | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetTypeFromTypeDef"
  - "IDebugDynamicFieldCOMPlus::GetTypeFromTypeDef"
ms.assetid: 7f6cd3d3-f4da-4893-be91-8dd104be8010
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDynamicFieldCOMPlus::GetTypeFromTypeDef
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Récupère un type donné son jeton.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetTypeFromTypeDef(  
   ULONG32       ulAppDomainID,  
   GUID          guidModule,  
   _mdToken      tokClass,  
   IDebugField** ppType  
);  
```  
  
```c#  
int GetTypeFromTypeDef(  
   uint            ulAppDomainID,  
   Guid            guidModule,  
   int             tokClass,  
   out IDebugField ppType  
);  
```  
  
#### Paramètres  
 `ulAppDomainID`  
 \[in\]  identificateur du domaine d'application.  
  
 `guidModule`  
 \[in\]  identificateur unique du module.  
  
 `tokClass`  
 \[in\]  jeton qui représente le type.  
  
 `ppType`  
 \[out\]  Retourne un objet d' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) qui contient le type.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)