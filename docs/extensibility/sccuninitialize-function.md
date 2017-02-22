---
title: "SccUninitialize (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccUninitialize"
helpviewer_keywords: 
  - "SccUninitialize (fonction)"
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# SccUninitialize (fonction)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette fonction nettoie toutes les allocations ou les connexions ouvertes créées par un appel précédent à la [SccInitialize](../extensibility/sccinitialize-function.md) en préparation pour l'arrêt du plug\-in de contrôle de code source.  
  
## Syntaxe  
  
```cpp#  
SCCRTN SccUninitialize (  
   LPVOID pvContext  
);  
```  
  
#### Paramètres  
 pvContext  
 \[in\] Le pointeur vers la structure de contexte du plug\-in de contrôle de source créée dans le [SccInitialize](../extensibility/sccinitialize-function.md).  
  
## Valeur de retour  
 L'implémentation de plug\-in de contrôle de source de cette fonction est censée renvoyer une des valeurs suivantes :  
  
|Valeur|Description|  
|------------|-----------------|  
|SCC\_OK|Le nettoyage s'est terminé correctement.|  
  
## Notes  
 Le plug\-in de contrôle de code source est chargé pour la préparation de s'arrêter et de libération de mémoire que le plug\-in a alloué pour la structure de contexte. La fonction est appelée une fois pour chaque instance donnée d'un plug\-in. Un appel à la [SccInitialize](../extensibility/sccinitialize-function.md) précède cet appel. Aucun projet ne peut toujours être ouvert au moment de l'appel à `SccUninitialize`.  
  
## Voir aussi  
 [Fonctions d'API de plug\-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)