---
title: "SccRemove (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccRemove"
helpviewer_keywords: 
  - "SccRemove (fonction)"
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# SccRemove (fonction)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette fonction supprime les fichiers du système de contrôle source.  
  
## Syntaxe  
  
```cpp#  
SCCRTN SccRemove(  
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
 \[in\] Nombre de fichiers spécifié dans le `lpFileNames` tableau.  
  
 lpFileNames  
 \[in\] Tableau des noms de chemin d'accès local complet des fichiers à supprimer.  
  
 lpComment  
 \[in\] Le commentaire à appliquer à chaque fichier en cours de suppression.  
  
 Options  
 \[in\] Indicateurs de commande \(non utilisés\).  
  
 pvOptions  
 \[in\] Options spécifiques au plug\-in de contrôle source.  
  
## Valeur de retour  
 L'implémentation de plug\-in de contrôle de source de cette fonction est censée renvoyer une des valeurs suivantes :  
  
|Valeur|Description|  
|------------|-----------------|  
|SCC\_OK|Suppression a réussi.|  
|SCC\_E\_FILENOTCONTROLLED|Le fichier sélectionné n'est pas sous contrôle de code source.|  
|SCC\_E\_OPNOTSUPPORTED|Le système de contrôle de code source ne prend pas en charge cette opération.|  
|SCC\_E\_ISCHECKEDOUT|Impossible de supprimer un fichier, car un utilisateur a extrait.|  
|SCC\_E\_ACCESSFAILURE|Impossible d'accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention.|  
|SCC\_E\_NOTAUTHORIZED|L'utilisateur n'est pas autorisé à effectuer cette opération.|  
|SCC\_E\_NONSPECIFICERROR|Erreur non spécifique ; fichier n'a pas été supprimé.|  
|SCC\_I\_OPERATIONCANCELED|L'opération a été annulée avant la fin.|  
  
## Notes  
 Cette fonction supprime les fichiers du système de contrôle de code source, mais ne les supprime pas de disque dur local de l'utilisateur.  
  
## Voir aussi  
 [Fonctions d'API de plug\-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)