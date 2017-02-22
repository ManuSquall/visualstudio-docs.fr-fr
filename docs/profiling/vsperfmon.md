---
title: "VSPerfMon | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPerfMon, outil"
  - "ligne de commande, outils"
  - "outils en ligne de commande, outil VSPerfMon"
  - "données [Visual Studio ALM], outil VSPerfMon"
  - "données de performances, outil VSPerfMon"
  - "outils d’analyse des performances, outil VSPerfMon"
  - "outils de profilage, VSPerfCmd"
ms.assetid: 37052afb-7a58-441f-bb17-f1587cc57068
caps.latest.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 30
---
# VSPerfMon
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez utiliser l'outil VSPerfMon pour collecter les données de performances d'une application. En général, cet outil est lancé par VSPerfCmd.exe.  VSPerfMon affiche des informations supplémentaires sur la jointure et le détachement d'un processus non disponible à l'aide de l'outil VSPerfCmd.  Pour afficher ces informations, démarrez VSPerfMon dans une fenêtre séparée.  Pour appeler VSPerfMon, utilisez la syntaxe suivante :  
  
```  
VSPerfMon [/U] </TRACE [/COUNTER:cfg] | /SAMPLE | /COVERAGE> /CROSSSESSION /OUTPUT <file name> [/WINCOUNTER:cfg] [/USER [DOMAIN\]username]  
```  
  
 Le tableau suivant décrit les options de l'outil VSPerfMon :  
  
|Options|Description|  
|-------------|-----------------|  
|**U**|La sortie de console redirigée est écrite sous Unicode.  Ce doit être la première option spécifiée.|  
|**OUTPUT:** `<` *file name* `>`|Redirige la sortie vers le nom de fichier spécifié.|  
|**TRACE**|Démarre l'analyseur de performances pour le profilage instrumenté.|  
|**SAMPLE**|Démarre l'analyseur de performances pour le profilage d'échantillonnage.|  
|**COVERAGE**|Démarre l'analyseur de performances pour la collection de couverture du code.|  
|**CONCURRENCY**|Démarre l'analyseur de performances pour le profilage de conflit de ressources.|  
|**USER:** `[` *domain* `\]` *username*|Autorise l'accès client à l'analyseur de performances à partir du compte spécifié.|  
|**CROSSSESSION**|Active le profilage intersession.|  
|**COUNTER** `:cfg`|En cas d'utilisation de la méthode de profilage par instrumentation \(TRACE\), spécifie un compteur UC à collecter à chaque point d'instrumentation.  Vous pouvez collecter les données de plusieurs compteurs en spécifiant plusieurs options Counter.<br /><br /> Pour spécifier les données du compteur \(*cfg*\), utilisez la syntaxe suivante :<br /><br /> NomCompteur\[**,**Reload\[,FriendlyName\]\]<br /><br /> -   NomCompteur correspond au nom d'un compteur retourné par la commande VSPerfCmd \/QueryCounters.<br />-   la recharge est l'intervalle d'échantillonnage des événements de compteur.  Ne pas utiliser *Reload* avec la méthode d'instrumentation.<br />-   En cas de spécification, FriendlyName remplace CounterName dans les noms de colonnes de rapport des Outils de profilage.|  
|**WINCOUNTER** `:path`|Spécifie un compteur de performance Windows à inclure avec les données de marquage.  `path` est une chaîne du compteur des Performances de Windows dans le format de chemin d'accès compteur PDH.  Par exemple :<br /><br /> \\Processor\(0\)\\% Temps processeur<br /><br /> \\System\\Changements de contexte\/sec|  
|**AUTOMARK** `:n`|Spécifie l'intervalle de temps \(en millisecondes\) entre les marques automatiques lors de l'utilisation de \/WINCOUNTER.  Arrondi aux 500 ms les plus proches.<br /><br /> Utilisez 0 pour désactiver les marques automatiques \(valeur par défaut\=500 ms en l'absence de spécification\).|  
  
## Voir aussi  
 [VSInstr](../profiling/vsinstr.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [VSPerfReport](../profiling/vsperfreport.md)   
 [Vues des rapports d’outils de profilage](../profiling/performance-report-views.md)