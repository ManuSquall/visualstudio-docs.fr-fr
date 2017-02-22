---
title: "SccCloseProject (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccCloseProject"
helpviewer_keywords: 
  - "SccCloseProject (fonction)"
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# SccCloseProject (fonction)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette fonction ferme un projet, en marquant la fin d'une session particulière.  
  
## Syntaxe  
  
```cpp#  
SCCRTN SccCloseProject (  
   LPVOID pvContext  
);  
```  
  
#### Paramètres  
 pvContext  
 La structure de contexte du plug\-in de contrôle de source.  
  
## Valeur de retour  
 L'implémentation de plug\-in de contrôle de source de cette fonction est censée renvoyer une des valeurs suivantes :  
  
|Valeur|Description|  
|------------|-----------------|  
|SCC\_OK|Le projet a été correctement fermé.|  
|SCC\_E\_PROJNOTOPEN|Aucun projet n'est actuellement ouvert.|  
|SCC\_E\_NOTAUTHORIZED|L'utilisateur n'est pas autorisé à effectuer cette opération.|  
|SCC\_E\_NONSPECIFICERROR|Erreur non spécifique.|  
  
## Notes  
 Le [SccOpenProject](../extensibility/sccopenproject-function.md) est toujours appelée avant cette fonction. Un appel à cette fonction est ensuite suivi par un appel à la `SccOpenProject` fonction ou [SccUninitialize](../extensibility/sccuninitialize-function.md), qui termine complètement la connexion au système de contrôle source.  
  
## Voir aussi  
 [Fonctions d'API de plug\-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)