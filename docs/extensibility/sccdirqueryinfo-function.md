---
title: "SccDirQueryInfo (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccDirQueryInfo"
helpviewer_keywords: 
  - "SccDirQueryInfo (fonction)"
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# SccDirQueryInfo (fonction)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette fonction examine une liste de répertoires complets pour leur état actuel.  
  
## Syntaxe  
  
```cpp#  
SCCRTN SccDirQueryInfo(  
LPVOID  pContext,  
LONG    nDirs,  
LPCSTR* lpDirNames,  
LPLONG  lpStatus  
);  
```  
  
#### Paramètres  
 pContext  
 \[in\] La structure de contexte du plug\-in de contrôle de source.  
  
 nDirs  
 \[in\] Le nombre de répertoires sélectionnés à interroger.  
  
 lpDirNames  
 \[in\] Tableau des chemins d'accès complets des répertoires à interroger.  
  
 lpStatus  
 \[dans, out\] Une structure de tableau pour le plug\-in pour retourner les indicateurs d'état de contrôle de code source \(voir [Code d'état Active](../extensibility/directory-status-code-enumerator.md) Pour plus d'informations\).  
  
## Valeur de retour  
 L'implémentation de plug\-in de contrôle de source de cette fonction est censée renvoyer une des valeurs suivantes :  
  
|Valeur|Description|  
|------------|-----------------|  
|SCC\_OK|La requête a réussi.|  
|SCC\_E\_OPNOTSUPPORTED|Le système de contrôle de code source ne prend pas en charge cette opération.|  
|SCC\_E\_ACCESSFAILURE|Impossible d'accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention. Une nouvelle tentative est recommandée.|  
|SCC\_E\_NONSPECIFICERROR<br /><br /> SCC\_E\_UNKNOWNERROR|Erreur non spécifique.|  
  
## Notes  
 La fonction remplit le tableau de résultats avec un masque de bits à partir de la `SCC_DIRSTATUS` famille \(voir [Code d'état Active](../extensibility/directory-status-code-enumerator.md)\), une entrée pour chaque répertoire donné. Le tableau d'états est alloué par l'appelant.  
  
 L'IDE utilise cette fonction avant qu'un répertoire est renommé pour vérifier si le répertoire est sous contrôle de code source en interrogeant s'il dispose d'un projet correspondant. Si le répertoire n'est pas sous contrôle de code source, l'IDE peut fournir l'avertissement approprié à l'utilisateur.  
  
> [!NOTE]
>  Si un plug\-in de contrôle de code source choisit ne pas implémenter une ou plusieurs valeurs d'état, non implémentées bits doivent être définis sur zéro.  
  
## Voir aussi  
 [Fonctions d'API de plug\-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [Code d'état Active](../extensibility/directory-status-code-enumerator.md)