---
title: "IDiaEnumFrameData::Clone | Microsoft Docs"
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
  - "IDiaEnumFrameData::Clone (méthode)"
ms.assetid: 28a17300-1626-422f-a17a-3a4d3872c37c
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumFrameData::Clone
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

crée un énumérateur qui contient le même état d'énumération que l'énumérateur actuel.  
  
## Syntaxe  
  
```cpp#  
HRESULT Clone(   
   IDiaEnumFrameData** ppenum  
);  
```  
  
#### Paramètres  
 ppenum  
 \[out\]  Retourne un objet d' [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md) qui contient un doublon de l'énumérateur.  Les données de frame n'est pas dupliquée, seul l'énumérateur.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)