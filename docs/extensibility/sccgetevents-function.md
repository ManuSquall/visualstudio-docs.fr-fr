---
title: "SccGetEvents (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccGetEvents"
helpviewer_keywords: 
  - "SccGetEvents (fonction)"
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# SccGetEvents (fonction)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette fonction extrait un événement d'état en file d'attente.  
  
## Syntaxe  
  
```cpp#  
SCCRTN SccGetEvents (  
   LPVOID pvContext,  
   LPSTR  lpFileName,  
   LPLONG lpStatus,  
   LPLONG pnEventsRemaining  
);  
```  
  
#### Paramètres  
 pvContext  
 \[in\] La structure de contexte du plug\-in de contrôle de source.  
  
 lpFileName  
 \[dans, out\] Mémoire tampon où le plug\-in de contrôle de code source place le nom de fichier renvoyé \(\_MAX\_PATH caractères maximum\).  
  
 lpStatus  
 \[dans, out\] Retourne le code d'état \(voir [Code d'état de fichier](../extensibility/file-status-code-enumerator.md) pour les valeurs possibles\).  
  
 pnEventsRemaining  
 \[dans, out\] Retourne le nombre d'entrées à gauche dans la file d'attente après cet appel. Si ce nombre est élevé, l'appelant peut décider d'appeler le [SccQueryInfo](../extensibility/sccqueryinfo-function.md) pour obtenir toutes les informations à la fois.  
  
## Valeur de retour  
 L'implémentation de plug\-in de contrôle de source de cette fonction est censée renvoyer une des valeurs suivantes :  
  
|Valeur|Description|  
|------------|-----------------|  
|SCC\_OK|Obtenir les événements réussis.|  
|SCC\_E\_OPNOTSUPPORTED|Cette fonction n'est pas pris en charge.|  
|SCC\_E\_NONSPECIFICERROR|Erreur non spécifique.|  
  
## Notes  
 Cette fonction est appelée pendant le traitement inactif pour voir si des mises à jour de l'état des fichiers sous contrôle de code source ont été. Le plug\-in de contrôle de code source gère l'état de tous les fichiers qu'il connaît et chaque fois qu'un changement d'état est indiqué par le plug\-in, l'état et les fichiers associés sont stockés dans une file d'attente. Lorsque `SccGetEvents` est appelée, le haut l'élément de la file d'attente est récupéré et retourné. Cette fonction est contraint pour renvoyer les informations précédemment mise en cache uniquement et doit avoir un temps de réponse très rapide \(autrement dit, aucune lecture du disque ou demandant le système de contrôle de code source pour l'état\) ; dans le cas contraire, les performances de l'IDE peuvent démarrer à se dégrader.  
  
 S'il n'existe aucune mise à jour d'état au rapport, le plug\-in de contrôle de code source stocke une chaîne vide dans la mémoire tampon pointée par `lpFileName`. Sinon, le plug\-in stocke le nom de chemin d'accès complet du fichier pour lequel les informations d'état a été modifié et renvoie le code d'état approprié \(l'une des valeurs énumérées [Code d'état de fichier](../extensibility/file-status-code-enumerator.md)\).  
  
## Voir aussi  
 [Fonctions d'API de plug\-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [Code d'état de fichier](../extensibility/file-status-code-enumerator.md)