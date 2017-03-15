---
title: "SccDirDiff (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccDirDiff"
helpviewer_keywords: 
  - "SccDirDiff (fonction)"
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# SccDirDiff (fonction)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette fonction affiche les différences entre le répertoire local actuel sur le disque du client et le projet sous contrôle de code source correspondant.  
  
## Syntaxe  
  
```cpp#  
SCCRTN SccDirDiff(  
   LPVOID    pContext,  
   HWND      hWnd,  
   LPCSTR    lpDirName,  
   LONG      dwFlags,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### Paramètres  
 pContext  
 \[in\] La structure de contexte du plug\-in de contrôle de source.  
  
 hWnd  
 \[in\] Handle vers la fenêtre de l'IDE que le plug\-in de contrôle de code source peut utiliser en tant que parent pour toutes les boîtes de dialogue qu'il fournit.  
  
 lpDirName  
 \[in\] Chemin d'accès complet vers le répertoire local pour lequel afficher une différence visuelle.  
  
 dwFlags  
 \[in\] Indicateurs de commande \(voir la section Remarques section\).  
  
 pvOptions  
 \[in\] Options spécifiques au plug\-in de contrôle source.  
  
## Valeur de retour  
 L'implémentation de plug\-in de contrôle de source de cette fonction est censée renvoyer une des valeurs suivantes :  
  
|Valeur|Description|  
|------------|-----------------|  
|SCC\_OK|Le répertoire sur le disque est le même que le projet de contrôle de code source.|  
|SCC\_I\_FILESDIFFER|Le répertoire sur le disque est différent du projet de contrôle de code source.|  
|SCC\_I\_RELOADFILE|Un fichier ou un projet doit être rechargé.|  
|SCC\_E\_FILENOTCONTROLLED|Le répertoire n'est pas sous contrôle de code source.|  
|SCC\_E\_NOTAUTHORIZED|L'utilisateur n'est pas autorisé à effectuer cette opération.|  
|SCC\_E\_ACCESSFAILURE|Impossible d'accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention. Une nouvelle tentative est recommandée.|  
|SCC\_E\_NONSPECIFICERROR<br /><br /> SCC\_E\_UNKNOWNERROR|Erreur non spécifique.|  
|SCC\_E\_FILENOTEXIST|Répertoire local est introuvable.|  
  
## Notes  
 Cette fonction est utilisée pour demander le contrôle de code source du plug\-in pour afficher la liste des modifications apportées à un répertoire spécifié à l'utilisateur. Le plug\-in ouvre sa propre fenêtre, dans un format de son choix, pour afficher les différences entre le répertoire de l'utilisateur sur le disque et le projet correspondant sous contrôle de version.  
  
 Si une comparaison de plug\-in prend en charge des répertoires du tout, il doit prendre en charge la comparaison des répertoires selon le nom de fichier même si les options « rapide\-diff » ne sont pas pris en charge.  
  
|`dwFlags`|Interprétation|  
|---------------|--------------------|  
|SCC\_DIFF\_IGNORECASE|Comparaison respectant la casse \(peut être utilisé pour une comparaison rapide ou visual\).|  
|SCC\_DIFF\_IGNORESPACE|Ignore les espaces blancs \(peut être utilisé pour rapide\-diff ou visuel\).|  
|SCC\_DIFF\_QD\_CONTENTS|Si la prise en charge par le plug\-in de contrôle de code source, en mode silencieux compare le répertoire, octet par octet.|  
|SCC\_DIFF\_QD\_CHECKSUM|Si pris en charge par le plug\-in, en mode silencieux compare le répertoire via une somme de contrôle ou, si ne pas pris en charge, revient à SCC\_DIFF\_QD\_CONTENTS.|  
|SCC\_DIFF\_QD\_TIME|Si pris en charge par le plug\-in, en mode silencieux compare le répertoire via son horodatage ou, si ne pas pris en charge, revient sur SCC\_DIFF\_QD\_CHECKSUM ou SCC\_DIFF\_QD\_CONTENTS.|  
  
> [!NOTE]
>  Cette fonction utilise les mêmes indicateurs de commande en tant que le [SccDiff](../extensibility/sccdiff-function.md). Toutefois, un plug\-in de contrôle de code source peut choisir de ne prend ne pas en charge l'opération « rapide\-diff » pour les répertoires.  
  
## Voir aussi  
 [Fonctions d'API de plug\-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)