---
title: "IDiaEnumDebugStreamData::Clone | Microsoft Docs"
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
  - "IDiaEnumDebugStreamData::Clone (méthode)"
ms.assetid: e7f17750-0694-4634-bf34-c821cd265c2f
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumDebugStreamData::Clone
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Crée un énumérateur qui contient la même séquence énumérée que l'énumérateur actuel.  
  
## Syntaxe  
  
```cpp#  
HRESULT Clone (   
   IDiaEnumDebugStreamData** ppenum  
);  
```  
  
#### Paramètres  
 ppenum  
 \[out\]  Retourne un objet d' [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) qui contient la séquence en double d'enregistrements de flux de données de débogage.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)