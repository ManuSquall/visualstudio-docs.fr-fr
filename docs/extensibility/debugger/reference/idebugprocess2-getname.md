---
title: "IDebugProcess2::GetName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::GetName"
helpviewer_keywords: 
  - "IDebugProcess2::GetName"
ms.assetid: a2f66ab5-53e5-4cdc-a1b5-3b8afa8ee646
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProcess2::GetName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient le titre, le nom convivial, ou le nom de fichier du processus.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetName(   
   GETNAME_TYPE  gnType,  
   BSTR*         pbstrName  
);  
```  
  
```c#  
int GetName(   
   enum_GETNAME_TYPE  gnType,  
   out string         pbstrName  
);  
```  
  
#### Paramètres  
 `gnType`  
 \[in\]  Une valeur de l'énumération de [GETNAME\_TYPE](../../../extensibility/debugger/reference/getname-type.md) qui spécifie le type de nom à retourner.  
  
 `pbstrName`  
 \[out\]  Retourne le nom du processus.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [GETNAME\_TYPE](../../../extensibility/debugger/reference/getname-type.md)