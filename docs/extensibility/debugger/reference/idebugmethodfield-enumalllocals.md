---
title: "IDebugMethodField::EnumAllLocals | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField::EnumAllLocals"
helpviewer_keywords: 
  - "IDebugMethodField::EnumAllLocals (méthode)"
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugMethodField::EnumAllLocals
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crée un énumérateur pour toutes les variables locales de la méthode, y compris celles créées en interne par un compilateur.  
  
## Syntaxe  
  
```cpp#  
HRESULT EnumAllLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```c#  
int EnumAllLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### Paramètres  
 `pAddress`  
 \[in\]  Un objet d' [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) représentant une adresse de débogage dans la méthode, qui pointe vers une portée ou un contexte particulier.  
  
 `ppLocals`  
 \[out\]  Retourne un objet d' [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) représentant la liste de toutes les heures locales dans la portée spécifiée ; sinon, retourne une valeur NULL n'indiquant aucun local.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ou retourne S\_FALSE s'il n'y a aucun local.  Sinon, retourne un code d'erreur.  
  
## Notes  
 Seuls les variables définies dans le bloc qui contient l'adresse donnée de débogage sont énumérées.  Cette méthode inclut toutes les heures locales générés par le compilateur.  Si toutes les qui sont nécessaires sont les données locales explicitement définies dans la source, appelez la méthode d' [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) .  
  
 Une méthode peut contenir plusieurs contextes ou blocs de portée.  
  
## Voir aussi  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)