---
title: "IDebugDocument2::GetName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocument2::GetName"
helpviewer_keywords: 
  - "IDebugDocument2::GetName"
ms.assetid: 6f09ff09-b0cf-4472-8fc8-143991f0ceb1
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocument2::GetName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient le nom du document dans un plusieurs formes.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetName(   
   GETNAME_TYPE gnType,  
   BSTR*        pbstrFileName  
);  
```  
  
```c#  
int GetName(   
   enum_GETNAME_TYPE gnType,  
   out string        pbstrFileName  
);  
```  
  
#### Paramètres  
 `gnType`  
 \[in\]  Une valeur de l'énumération de [GETNAME\_TYPE](../../../extensibility/debugger/reference/getname-type.md) qui détermine le type de nom à retourner.  
  
 `pbstrFileName`  
 \[out\]  Retourne une chaîne contenant le nom du document.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Cette méthode peut, par exemple, retourner le nom du document comme titre ou comme un nom de fichier ou même partie d'un nom de fichier.  
  
## Voir aussi  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [GETNAME\_TYPE](../../../extensibility/debugger/reference/getname-type.md)