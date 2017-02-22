---
title: "IDiaFrameData::execute | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaFrameData::execute (méthode)"
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaFrameData::execute
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Exécute le déroulement de pile et retourne des résultats dans une interface de frame de parcours de la pile.  
  
## Syntaxe  
  
```cpp#  
HRESULT execute (   
   IDiaStackWalkFrame* frame  
);  
```  
  
#### Paramètres  
 `frame`  
 \[in\]  Un objet d' [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) qui conserve l'état du frame sont enregistrées.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  Le tableau suivant montre les valeurs de retour possibles de cette méthode.  
  
|Valeur|Description|  
|------------|-----------------|  
|E\_DIA\_INPROLOG|Ne peut pas exécuter un frame de pile alors que dans le code du prologue.|  
|E\_DIA\_SYNTAX|Erreur d'analyse rencontrée dans le programme de frame.|  
|E\_DIA\_FRAME\_ACCESS|Impossible d'accéder aux registres ou à la mémoire.|  
|E\_DIA\_VALUE|erreur dans le calcul d'une valeur \(par exemple, division par zéro\).|  
  
## Notes  
 cette méthode est appelée pendant le débogage pour dérouler la pile.  L'objet d' [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) est implémenté par l'application cliente de recevoir des mises à jour des registres et de fournir les méthodes utilisées par la méthode d' `execute` .  
  
## Voir aussi  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)