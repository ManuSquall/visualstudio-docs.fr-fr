---
title: "IDebugField::GetInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugField::GetInfo"
helpviewer_keywords: 
  - "IDebugField::GetInfo (méthode)"
ms.assetid: 7d508200-89ce-400f-a8ea-f28e7610cb2b
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugField::GetInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode extrait des informations accessibles sur le champ.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetInfo(   
   FIELD_INFO_FIELDS dwFields,  
   FIELD_INFO* pFieldInfo  
);  
```  
  
```c#  
int GetInfo(  
   enum_FIELD_INFO_FIELDS dwFields,  
   FIELD_INFO[] pFieldInfo  
);  
```  
  
#### Paramètres  
 `dwFields`  
 \[in\]  une combinaison des constantes de [FIELD\_INFO\_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) qui sélectionne les informations à afficher.  Si le champ représente un symbole, c'est généralement le nom et le type de symbole.  
  
 `pFieldInfo`  
 \[out\]  Retourne les informations de la structure fournie de [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md) .  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md)