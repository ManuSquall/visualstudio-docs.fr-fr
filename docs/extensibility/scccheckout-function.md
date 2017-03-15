---
title: "SccCheckout (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccCheckout"
helpviewer_keywords: 
  - "SccCheckout (fonction)"
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# SccCheckout (fonction)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Obtenez la liste des noms de fichier complet, cette fonction extrait les sur le disque local. Le commentaire s'applique à tous les fichiers extraits. L'argument de commentaire peut être un `null` chaîne.  
  
## Syntaxe  
  
```cpp#  
SCCRTN SccCheckout (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### Paramètres  
 pvContext  
 \[in\] La structure de contexte du plug\-in de contrôle de source.  
  
 hWnd  
 \[in\] Handle vers la fenêtre de l'IDE que le plug\-in de contrôle de code source peut utiliser en tant que parent pour toutes les boîtes de dialogue qu'il fournit.  
  
 nFiles  
 \[in\] Nombre de fichiers sélectionnés à récupérer.  
  
 lpFileNames  
 \[in\] Tableau des noms de chemin d'accès local complet des fichiers à récupérer.  
  
 lpComment  
 \[in\] Commentaire à appliquer à chaque fichier sélectionné en cours d'extraction.  
  
 Options  
 \[in\] Indicateurs de commande \(voir [Indicateurs de bits utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md)\).  
  
 pvOptions  
 \[in\] Options spécifiques au plug\-in de contrôle source.  
  
## Valeur de retour  
 L'implémentation de plug\-in de contrôle de source de cette fonction est censée renvoyer une des valeurs suivantes :  
  
|Valeur|Description|  
|------------|-----------------|  
|SCC\_OK|Extraction réussie.|  
|SCC\_E\_FILENOTCONTROLLED|Le fichier sélectionné n'est pas sous contrôle de code source.|  
|SCC\_E\_ACCESSFAILURE|Impossible d'accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention. Une nouvelle tentative est recommandée.|  
|SCC\_E\_NOTAUTHORIZED|L'utilisateur n'est pas autorisé à effectuer cette opération.|  
|SCC\_E\_NONSPECIFICERROR|Erreur non spécifique. Le fichier n'a pas été extrait.|  
|SCC\_E\_ALREADYCHECKEDOUT|L'utilisateur a déjà extrait le fichier.|  
|SCC\_E\_FILEISLOCKED|Le fichier est verrouillé, ce qui interdit la création de nouvelles versions.|  
|SCC\_E\_FILEOUTEXCLUSIVE|Un autre utilisateur a effectué une extraction exclusive sur ce fichier.|  
|SCC\_I\_OPERATIONCANCELED|L'opération a été annulée avant la fin.|  
  
## Voir aussi  
 [Fonctions d'API de plug\-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [Indicateurs de bits utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md)