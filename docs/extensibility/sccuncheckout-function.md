---
title: "SccUncheckout (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccUncheckout"
helpviewer_keywords: 
  - "SccUncheckout (fonction)"
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# SccUncheckout (fonction)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette fonction annule une opération d'extraction précédente, restaurant ainsi le contenu du fichier sélectionné ou des fichiers à l'état précédant l'extraction. Toutes les modifications apportées au fichier depuis l'extraction sont perdues.  
  
## Syntaxe  
  
```cpp#  
SCCRTN SccUncheckout (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
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
 \[in\] Tableau des noms de chemin d'accès local complet des fichiers pour lequel annuler une extraction.  
  
 Options  
 \[in\] Indicateurs de commande \(non utilisés\).  
  
 pvOptions  
 \[in\] Options spécifiques au plug\-in de contrôle source.  
  
## Valeur de retour  
 L'implémentation de plug\-in de contrôle de source de cette fonction est censée renvoyer une des valeurs suivantes :  
  
|Valeur|Description|  
|------------|-----------------|  
|SCC\_OK|Annuler l'extraction a réussi.|  
|SCC\_E\_FILENOTCONTROLLED|Le fichier sélectionné n'est pas sous contrôle de code source.|  
|SCC\_E\_ACCESSFAILURE|Impossible d'accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention. Une nouvelle tentative est recommandée.|  
|SCC\_E\_NONSPECIFICERROR|Erreur non spécifique. Annuler l'extraction a échoué.|  
|SCC\_E\_NOTCHECKEDOUT|L'utilisateur n'a pas extrait le fichier.|  
|SCC\_E\_NOTAUTHORIZED|L'utilisateur n'est pas autorisé à effectuer cette opération.|  
|SCC\_E\_PROJNOTOPEN|Le projet n'a pas été ouverte à partir du contrôle de code source.|  
|SCC\_I\_OPERATIONCANCELED|L'opération a été annulée avant la fin.|  
  
## Notes  
 Après cette opération, le `SCC_STATUS_CHECKEDOUT` et `SCC_STATUS_MODIFIED` indicateurs seront désactivées pour les fichiers sur lesquels l'extraction a été effectuée.  
  
## Voir aussi  
 [Fonctions d'API de plug\-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)