---
title: "SccEndBatch (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccEndBatch"
helpviewer_keywords: 
  - "SccEndBatch (fonction)"
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# SccEndBatch (fonction)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette fonction termine un lot d'opérations de contrôle de code source. Ces lots ne peuvent pas être imbriqués.  
  
## Syntaxe  
  
```cpp#  
SCCRTN SccEndBatch(void);  
```  
  
#### Paramètres  
 Aucun  
  
## Valeur de retour  
 L'implémentation de plug\-in de contrôle de source de cette fonction est censée renvoyer une des valeurs suivantes :  
  
|Valeur|Description|  
|------------|-----------------|  
|SCC\_OK|Lot d'opérations conclu avec succès.|  
|SCC\_E\_UNKNOWNERROR|Erreur non spécifique.|  
  
## Notes  
 Lots de contrôle de code source sont utilisés pour exécuter les mêmes opérations de contrôle de code source sur plusieurs projets ou plusieurs contextes. Lots peuvent servir à éliminer les boîtes de dialogue redondante à partir de l'expérience utilisateur pendant une opération par lot. Le [SccBeginBatch](../extensibility/sccbeginbatch-function.md) et le `SccEndBatch` \(fonction\) sont utilisés en tant que paire pour indiquer le début et la fin d'une opération. Ils ne peuvent pas être imbriqués.  
  
## Voir aussi  
 [Fonctions d'API de plug\-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [SccBeginBatch](../extensibility/sccbeginbatch-function.md)