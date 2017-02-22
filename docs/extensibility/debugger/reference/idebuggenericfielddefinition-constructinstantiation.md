---
title: "IDebugGenericFieldDefinition::ConstructInstantiation | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ConstructInstantiation"
  - "IDebugGenericFieldDefinition::ConstructInstantiation"
ms.assetid: ef8ae261-a98b-4dc2-93b3-7c5191818ba2
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugGenericFieldDefinition::ConstructInstantiation
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Construit une instance de champ et un tableau d'arguments de type.  
  
## Syntaxe  
  
```cpp#  
HRESULT ConstructInstantiation(  
   ULONG32       cArgs,  
   IDebugField** ppArgs,  
   IDebugField** ppConstructedField  
);  
```  
  
```c#  
int ConstructInstantiation(  
   uint            cArgs,  
   IDebugField[]   ppArgs,  
   out IDebugField ppConstructedField  
);  
```  
  
#### Paramètres  
 `cArgs`  
 \[in\]  Nombre d'arguments dans le tableau d' `ppArgs` .  
  
 `ppArgs`  
 \[in\]  rangez qui contient les arguments de type.  Les arguments de type doivent être des types fermés \(non génériques ou les génériques pleinement instanciés\).  
  
 `ppConstructedField`  
 \[out\]  Retourne l'interface d' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) qui représente le nouveau champ.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Les contraintes ne sont pas activées.  
  
## Voir aussi  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)