---
title: "SccAdd (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccAdd"
helpviewer_keywords: 
  - "SccAdd (fonction)"
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# SccAdd (fonction)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette fonction ajoute de nouveaux fichiers au système de contrôle source.  
  
## Syntaxe  
  
```cpp#  
SCCRTN SccAdd(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
   LONG*     pfOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### Paramètres  
 pvContext  
 \[in\] La structure de contexte du plug\-in de contrôle de source.  
  
 hWnd  
 \[in\] Handle vers la fenêtre de l'IDE que le plug\-in de contrôle de code source peut utiliser en tant que parent pour toutes les boîtes de dialogue qu'il fournit.  
  
 nFiles  
 \[in\] Nombre de fichiers sélectionnés à ajouter au projet actuel en tant que donnée dans le `lpFileNames` tableau.  
  
 lpFileNames  
 \[in\] Tableau de noms locaux complets des fichiers à ajouter.  
  
 lpComment  
 \[in\] Le commentaire à appliquer à tous les fichiers à ajouter.  
  
 pfOptions  
 \[in\] Tableau d'indicateurs de commande, fourni sur une base par fichier.  
  
 pvOptions  
 \[in\] Options spécifiques au plug\-in de contrôle source.  
  
## Valeur de retour  
 L'implémentation de plug\-in de contrôle de source de cette fonction est censée renvoyer une des valeurs suivantes :  
  
|Valeur|Description|  
|------------|-----------------|  
|SCC\_OK|L'opération d'ajout a réussi.|  
|SCC\_E\_FILEALREADYEXISTS|Le fichier sélectionné est déjà sous contrôle de code source.|  
|SCC\_E\_TYPENOTSUPPORTED|Le type de fichier \(par exemple, binaire\) n'est pas pris en charge par le système de contrôle de code source.|  
|SCC\_E\_OPNOTSUPPORTED|Le système de contrôle de code source ne prend pas en charge cette opération.|  
|SCC\_E\_ACCESSFAILURE|Impossible d'accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention. Une nouvelle tentative est recommandée.|  
|SCC\_E\_NOTAUTHORIZED|L'utilisateur n'est pas autorisé à effectuer cette opération.|  
|SCC\_E\_NONSPECIFICERROR|Erreur non spécifique ; Ajoutez ne pas effectuée.|  
|SCC\_I\_OPERATIONCANCELED|L'opération a été annulée avant la fin.|  
|SCC\_I\_RELOADFILE|Un fichier ou un projet doit être rechargé.|  
|SCC\_E\_FILENOTEXIST|Impossible de trouver le fichier local.|  
  
## Notes  
 Classiques `fOptions` sont remplacés ici par un tableau, `pfOptions`, avec une `LONG` option spécification par fichier. Il s'agit, car le type de fichier peut varier d'un fichier.  
  
> [!NOTE]
>  Vous ne pouvez pas spécifier à la fois `SCC_FILETYPE_TEXT` et `SCC_FILETYPE_BINARY` options pour le même fichier, mais il ne spécifier aucune des deux. Aucun paramètre est le même que `SCC_FILETYPE_AUTO`, auquel cas la contrôle du code source du plug\-in détecte automatiquement le type de fichier.  
  
 Voici la liste des indicateurs utilisés pour le `pfOptions` tableau :  
  
|Option|Valeur|Signification|  
|------------|------------|-------------------|  
|SCC\_FILETYPE\_AUTO|0 x 00|Le plug\-in de contrôle de code source doit détecter le type de fichier.|  
|SCC\_FILETYPE\_TEXT|0 x 01|Indique un fichier texte ASCII.|  
|SCC\_FILETYPE\_BINARY|0 x 02|Indique un type de fichier autre que texte ASCII.|  
|SCC\_ADD\_STORELATEST|0 x 04|Enregistre uniquement la dernière copie du fichier, aucun deltas.|  
|SCC\_FILETYPE\_TEXT\_ANSI|0 x 08|Traite le fichier en tant que texte ANSI.|  
|SCC\_FILETYPE\_UTF8|0 x 10|Traite le fichier en tant que texte Unicode au format UTF8.|  
|SCC\_FILETYPE\_UTF16LE|0 x 20|Traite le fichier en tant que texte Unicode dans UTF16 format Little Endian.|  
|SCC\_FILETYPE\_UTF16BE|0 x 40|Mettre en forme traite le fichier en tant que texte Unicode Big Endian UTF16.|  
  
## Voir aussi  
 [Fonctions d'API de plug\-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)