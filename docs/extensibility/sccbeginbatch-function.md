---
title: "SccBeginBatch (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccBeginBatch"
helpviewer_keywords: 
  - "SccBeginBatch (fonction)"
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# SccBeginBatch (fonction)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette fonction démarre une séquence d'opérations de contrôle de code source. Le [SccEndBatch](../extensibility/sccendbatch-function.md) sera appelé pour terminer le lot. Ces lots ne peuvent pas être imbriqués.  
  
## Syntaxe  
  
```cpp#  
SCCRTN SccBeginBatch(void);  
```  
  
#### Paramètres  
 Aucun  
  
## Valeur de retour  
 L'implémentation de plug\-in de contrôle de source de cette fonction est censée renvoyer une des valeurs suivantes :  
  
|Valeur|Description|  
|------------|-----------------|  
|SCC\_OK|Lot d'opérations a démarré avec succès.|  
|SCC\_E\_UNKNOWNERROR|Erreur non spécifique.|  
  
## Notes  
 Lots de contrôle de code source sont utilisés pour exécuter les mêmes opérations sur plusieurs projets ou plusieurs contextes. Lots peuvent servir à éliminer les boîtes de dialogue de projet redondante à partir de l'expérience utilisateur pendant une opération par lot. Le `SccBeginBatch` \(fonction\) et [SccEndBatch](../extensibility/sccendbatch-function.md) sont utilisées comme une paire de fonctions pour indiquer le début et la fin d'une opération. Ils ne peuvent pas être imbriqués.`SccBeginBatch` définit un indicateur qui signale qu'une opération par lot est en cours.  
  
 Pendant une opération par lot est activée, le plug\-in de contrôle de code source doit présenter au maximum une boîte de dialogue pour toute question à l'utilisateur et appliquent la réponse à partir de cette boîte de dialogue toutes les opérations suivantes.  
  
## Voir aussi  
 [Fonctions d'API de plug\-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [SccEndBatch](../extensibility/sccendbatch-function.md)