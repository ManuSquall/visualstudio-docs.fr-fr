---
title: "IDebugSymbolSearchEvent2::GetSymbolSearchInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugSymbolSearchEvent2::GetSymbolSearchInfo"
helpviewer_keywords: 
  - "IDebugSymbolSearchEvent2::GetSymbolSearchInfo"
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSymbolSearchEvent2::GetSymbolSearchInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Appelé par un gestionnaire d'événements pour récupérer des résultats sur un processus de chargement de symboles.  
  
## Syntaxe  
  
```cpp  
HRESULT GetSymbolSearchInfo(  
   IDebugModule3**    pModule,  
   BSTR*              pbstrDebugMessage,  
   MODULE_INFO_FLAGS* pdwModuleInfoFlags  
);  
```  
  
```c#  
int GetSymbolSearchInfo(  
   IDebugModule3              pModule,   
   ref string                 pbstrDebugMessage,   
   out enum_MODULE_INFO_FLAGS pdwModuleInfoFlags  
);  
  
```  
  
#### Paramètres  
 `pModule`  
 \[out\]  Un objet IDebugModule3 représentant le module pour lequel des symboles auront été chargés.  
  
 `pbstrDebugMessage`  
 \[in, out\]  Retourne une chaîne contenant tous les messages d'erreur du module.  S'il n'existe aucune erreur, cette chaîne contient simplement le nom de module mais elle n'est jamais vide.  
  
> [!NOTE]
>  \[C\+\+\] `pbstrDebugMessage` ne peut pas être `NULL` et doit être fourni avec `SysFreeString`.  
  
 `pdwModuleInfoFlags`  
 \[out\]  Une combinaison des indicateurs d'énumération de [MODULE\_INFO\_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) qui indique si les symboles auront été chargés.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon retourne un code d'erreur.  
  
## Notes  
 Lorsqu'un gestionnaire reçoit l'événement d' [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) après qu'une tentative soit a réalisé charger des symboles de débogage pour un module, le gestionnaire peut appeler le thismethod pour déterminer les résultats de cette charge.  
  
## Voir aussi  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [MODULE\_INFO\_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)