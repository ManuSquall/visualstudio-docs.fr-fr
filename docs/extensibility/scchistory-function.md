---
title: "SccHistory (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccHistory"
helpviewer_keywords: 
  - "SccHistory (fonction)"
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# SccHistory (fonction)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette fonction affiche l'historique des fichiers spécifiés.  
  
## Syntaxe  
  
```cpp#  
SCCRTN SccHistory(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### Paramètres  
 `pvContext`  
 \[in\] La structure de contexte du plug\-in de contrôle de source.  
  
 `hWnd`  
 \[in\] Handle vers la fenêtre de l'IDE que le plug\-in de contrôle de code source peut utiliser en tant que parent pour toutes les boîtes de dialogue qu'il fournit.  
  
 `nFiles`  
 \[in\] Nombre de fichiers spécifié dans le `lpFileName` tableau.  
  
 `lpFileName`  
 \[in\] Tableau des noms qualifiés complets de fichiers.  
  
 `fOptions`  
 \[in\] Indicateurs de commande \(actuellement non utilisés\).  
  
 `pvOptions`  
 \[in\] Options spécifiques au plug\-in de contrôle source.  
  
## Valeur de retour  
 L'implémentation de plug\-in de contrôle de source de cette fonction est censée renvoyer une des valeurs suivantes :  
  
|Valeur|Description|  
|------------|-----------------|  
|SCC\_OK|Historique des versions a été obtenue avec succès.|  
|SCC\_I\_RELOADFILE|Le système de contrôle de code source en fait modifié le fichier sur le disque lors de l'extraction de l'historique \(par exemple, par l'obtention d'une ancienne version de celui\-ci\), donc l'IDE doit recharger ce fichier.|  
|SCC\_E\_FILENOTCONTROLLED|Le fichier n'est pas sous contrôle de code source.|  
|SCC\_E\_OPNOTSUPPORTED|Le système de contrôle de code source ne prend pas en charge cette opération.|  
|SCC\_E\_NOTAUTHORIZED|L'utilisateur n'est pas autorisé à effectuer cette opération.|  
|SCC\_E\_ACCESSFAILURE|Impossible d'accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention. Une nouvelle tentative est recommandée.|  
|SCC\_E\_PROJNOTOPEN|Le projet n'a pas été ouvert.|  
|SCC\_E\_NONSPECIFICERROR|Erreur non spécifique. L'historique des fichiers n'a pas pu être obtenu.|  
  
## Notes  
 Le plug\-in de contrôle de code source peut afficher une boîte de dialogue pour afficher l'historique de chaque fichier, à l'aide de `hWnd` en tant que la fenêtre parente. Ou bien, le texte facultatif sortie rappel fonction fournie à la [SccOpenProject](../extensibility/sccopenproject-function.md) peut être utilisée, si elle est prise en charge.  
  
 Notez que dans certaines circonstances, le fichier en cours d'examen peut changer pendant l'exécution de cet appel. Par exemple, le [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] commande historique permet de l'utilisateur pour obtenir une version ancienne du fichier. Dans ce cas, la contrôle du code source retourne plug\-in `SCC_I_RELOAD` pour avertir l'IDE qu'il doit recharger le fichier.  
  
> [!NOTE]
>  Si le plug\-in de contrôle de code source ne prend pas en charge cette fonction pour un tableau de fichiers, l'historique du fichier uniquement pour le premier fichier peut être affiché.  
  
## Voir aussi  
 [Fonctions d'API de plug\-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)