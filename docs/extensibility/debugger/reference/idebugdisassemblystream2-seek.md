---
title: "IDebugDisassemblyStream2::Seek | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDisassemblyStream2::Seek"
helpviewer_keywords: 
  - "IDebugDisassemblyStream2::Seek"
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDisassemblyStream2::Seek
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Déplace le pointeur de lecture dans le flux de code machine un nombre donné d'instruction par rapport à la position spécifiée.  
  
## Syntaxe  
  
```cpp#  
HRESULT Seek(   
   SEEK_START          dwSeekStart,  
   IDebugCodeContext2* pCodeContext,  
   UINT64              uCodeLocationId,  
   INT64               iInstructions  
);  
```  
  
```c#  
int Seek(   
   enum_SEEK_START    dwSeekStart,  
   IDebugCodeContext2 pCodeContext,  
   ulong              uCodeLocationId,  
   long               iInstructions  
);  
```  
  
#### Paramètres  
 `dwSeekStart`  
 \[in\]  Une valeur de l'énumération de [SEEK\_START](../../../extensibility/debugger/reference/seek-start.md) qui spécifie la position relative pour démarrer le processus d'accès.  
  
 `pCodeContext`  
 \[in\]  L'objet d' [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) représentant le contexte de code que l'opération de recherche est associée.  Ce paramètre est utilisé uniquement si `dwSeekStart` \= `SEEK_START_CODECONTEXT`; sinon, ce paramètre est ignoré et peut être une valeur NULL.  
  
 `uCodeLocationId`  
 \[in\]  L'identificateur de l'emplacement du code que l'opération de recherche est associée.  Cette valeur est utilisée si `dwSeekStart` \= `SEEK_START_CODELOCID`; sinon, ce paramètre est ignoré et peut avoir la valeur 0.  Consultez la section Notes de la méthode d' [GetCodeLocationId](../Topic/IDebugDisassemblyStream2::GetCodeLocationId.md) pour une description d'un identificateur d'emplacement du code.  
  
 `iInstructions`  
 \[in\]  Le nombre d'instructions de déplacer par rapport à la position spécifiée dans `dwSeekStart`.  cette valeur peut être négative pour déplacer vers l'arrière.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` si la position d'accès se trouvait à un point au delà de la liste d'instructions disponible.  Sinon, retourne un code d'erreur.  
  
## Notes  
 Si l'accès est à une position avant le début de la liste, la position de lecture soit défini à la première instruction dans la liste.  Si le voir était à une position après la fin de la liste, la position de lecture soit définie à la dernière instruction dans la liste.  
  
## Voir aussi  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [SEEK\_START](../../../extensibility/debugger/reference/seek-start.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../Topic/IDebugDisassemblyStream2::GetCodeLocationId.md)