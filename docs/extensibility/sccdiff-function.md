---
title: "SccDiff (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccDiff"
helpviewer_keywords: 
  - "SccDiff (fonction)"
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# SccDiff (fonction)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette fonction affiche \(ou éventuellement simplement vérifie\) les différences entre le fichier en cours \(sur le disque local\) et de sa dernière version archivée dans la source de système de contrôle.  
  
## Syntaxe  
  
```cpp#  
SCCRTN SccDiff(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LPCSTR    lpFileName,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### Paramètres  
 pvContext  
 \[in\] La structure de contexte du plug\-in de contrôle de source.  
  
 hWnd  
 \[in\] Handle vers la fenêtre de l'IDE que le plug\-in de contrôle de code source peut utiliser en tant que parent pour toutes les boîtes de dialogue qu'il fournit.  
  
 lpFileName  
 \[in\] Nom de fichier pour lequel la différence est demandée.  
  
 Options  
 \[in\] Indicateurs de commande. Pour plus d'informations, consultez la section Notes.  
  
 pvOptions  
 \[in\] Options spécifiques au plug\-in de contrôle source.  
  
## Valeur de retour  
 L'implémentation de plug\-in de contrôle de source de cette fonction est censée renvoyer une des valeurs suivantes :  
  
|Valeur|Description|  
|------------|-----------------|  
|SCC\_OK|La version de copie et le serveur de travail sont identiques.|  
|SCC\_I\_FILESDIFFERS|La copie de travail diffère de la version sous contrôle de code source.|  
|SCC\_I\_RELOADFILE|Un fichier ou un projet doit être rechargé.|  
|SCC\_E\_FILENOTCONTROLLED|Le fichier n'est pas sous contrôle de code source.|  
|SCC\_E\_NOTAUTHORIZED|L'utilisateur n'est pas autorisé à effectuer cette opération.|  
|SCC\_E\_ACCESSFAILURE|Impossible d'accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention. Une nouvelle tentative est recommandée.|  
|SCC\_E\_NONSPECIFICERROR|Erreur non spécifique ; différence de fichier n'a pas été obtenu.|  
|SCC\_E\_FILENOTEXIST|Le fichier local est introuvable.|  
  
## Notes  
 Cette fonction remplit deux fonctions différentes. Par défaut, il affiche une liste des modifications apportées à un fichier. Le plug\-in de contrôle de code source s'ouvre sa propre fenêtre, dans le format choisit, pour afficher les différences entre le fichier de l'utilisateur sur le disque et la dernière version du fichier sous contrôle de code source.  
  
 Sinon, l'IDE peut suffit déterminer si un fichier a changé. Par exemple, l'IDE peut\-être déterminer si elle est sécurisée pour extraire un fichier sans en informer l'utilisateur. Dans ce cas, l'IDE passe dans le `SCC_DIFF_CONTENTS` indicateur. Le plug\-in de contrôle de code source doit vérifier le fichier sur disque, octet par octet, par rapport au fichier de contrôle de code source et renvoyer une valeur indiquant si les deux fichiers sont différents sans rien afficher à l'utilisateur.  
  
 Optimiser les performances, le plug\-in de contrôle de code source peut utiliser une alternative basée sur une somme de contrôle ou un horodatage au lieu de la comparaison octet par octet demandée par `SCC_DIFF_CONTENTS`: ces formes de comparaison sont évidemment plus rapide mais moins fiable. Pas tous les systèmes de contrôle source peuvent prendre en charge ces méthodes de comparaison de l'autre, et le plug\-in peut avoir à revenir à une comparaison de contenu. Tous les plug\-ins de contrôle de code source doit, au minimum, prendre en charge une comparaison de contenu.  
  
> [!NOTE]
>  Les indicateurs de différence rapide s'excluent mutuellement. Il est valide de ne passer aucun indicateur, mais il n'est pas valide pour transmettre simultanément plusieurs.`SCC_DIFF_QUICK_DIFF`, qui est un masque qui combine tous les indicateurs, peut être utilisé pour tester, mais elles ne doivent jamais être transmises en tant que paramètre.  
  
|`fOption`|Signification|  
|---------------|-------------------|  
|SCC\_DIFF\_IGNORECASE|Comparaison respectant la casse \(peut être utilisé pour différence rapide ou visuel\).|  
|SCC\_DIFF\_IGNORESPACE|Ignore les espaces blancs \(peut être utilisé pour différence rapide ou visuel\).|  
|SCC\_DIFF\_QD\_CONTENTS|En mode silencieux compare le fichier, octet par octet.|  
|SCC\_DIFF\_QD\_CHECKSUM|En mode silencieux compare le fichier via une somme de contrôle sont prises en charge. Si non pris en charge, revient à une comparaison de contenu.|  
|SCC\_DIFF\_QD\_TIME|En mode silencieux compare le fichier via son horodatage lors de la prise en charge. Si non pris en charge, revient à une comparaison de contenu.|  
  
## Voir aussi  
 [Fonctions d'API de plug\-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)