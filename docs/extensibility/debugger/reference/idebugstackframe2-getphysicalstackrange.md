---
title: "IDebugStackFrame2::GetPhysicalStackRange | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame2::GetPhysicalStackRange"
helpviewer_keywords: 
  - "IDebugStackFrame2::GetPhysicalStackRange"
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugStackFrame2::GetPhysicalStackRange
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient la représentation d'ordinateur\-dépendant de la plage d'adresses physiques associées à un frame de pile.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetPhysicalStackRange (   
   UINT64* paddrMin,  
   UINT64* paddrMax  
);  
```  
  
```c#  
int GetPhysicalStackRange (   
   out ulong paddrMin,  
   out ulong paddrMax  
);  
```  
  
#### Paramètres  
 `paddrMin`  
 \[out\]  Retourne la plus basse adresse physique associée à ce frame de pile.  
  
 `paddrMax`  
 \[out\]  Retourne l'adresse physique élevée associée à ce frame de pile.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 les informations retournées par cette méthode sont utilisées par le gestionnaire de débogage de session \(SDM\) pour trier des frames de pile.  
  
 On suppose que la pile des appels se développe vers le bas, c. autrement dit., que de nouveaux frames de pile sont ajoutés à des adresses mémoire de plus en plus inférieure.  Une architecture à l'exécution doit fournir des plages physiques de pile qui correspondent à cette hypothèse.  
  
## Voir aussi  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)