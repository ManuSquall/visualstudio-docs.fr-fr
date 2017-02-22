---
title: "SccGetVersion (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccGetVersion"
helpviewer_keywords: 
  - "SccGetVersion (fonction)"
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# SccGetVersion (fonction)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette fonction obtient le numéro de version de l'API de plug\-in de contrôle de Source pris en charge par le plug\-in de contrôle de code source.  
  
## Syntaxe  
  
```cpp#  
LONG SccGetVersion(void);  
```  
  
#### Paramètres  
 Aucun  
  
## Valeur de retour  
 Un `LONG` type de données qui contient le numéro de version de l'API de plug\-in de contrôle Source pris en charge :  
  
|WORD|Description|  
|----------|-----------------|  
|HIWORD|Version majeure|  
|LOWORD|Version mineure|  
  
## Notes  
 Par exemple, si un plug\-in de contrôle de code source prend en charge la version 1.3 de l'API de plug\-in de contrôle de Source, cette fonction renvoie 0x0103.  
  
## Voir aussi  
 [Fonctions d'API de plug\-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)