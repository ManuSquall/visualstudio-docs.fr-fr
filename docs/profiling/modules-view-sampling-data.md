---
title: "Mode Modules - Donn&#233;es d’&#233;chantillonnage du profileur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Modules, mode"
  - "méthode de profilage par échantillonnage, mode Modules"
ms.assetid: 816f5633-65d7-41e5-aee1-033628d4e2df
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Mode Modules - Donn&#233;es d’&#233;chantillonnage du profileur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vue Modules des données d'échantillonnage affiche les données de performance groupées par les modules échantillonnés dans les données de profilage.  Chaque module correspond à la racine d'une arborescence hiérarchique.  Les fonctions échantillonnées du module sont répertoriées sous le nœud de module.  
  
> [!NOTE]
>  Les fonctionnalités de sécurité renforcée dans windows 8 et Windows Server 2012 requises des modifications significatives de la manière que le profileur Visual Studio collecte des données sur ces plateformes.  Les applications de mémoire de fenêtres requièrent également de nouvelles techniques de collection.  Consultez [Profilage d'applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Si la fonction s'exécutait lorsque les échantillons ont été collectés \(autrement dit, la fonction était en haut de la pile des appels\), les lignes sources et les adresses d'instruction qui s'exécutaient sont répertoriées sous le nœud de la fonction.  Dans la mesure où les données sont collectées pour un pointeur d'instruction ou une ligne source lorsque la ligne ou l'instruction est en cours d'exécution, les valeurs inclusives et exclusives sont toujours les mêmes pour les données de ligne et les données d'instruction.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Nom**|Nom du module, de la fonction, du numéro de ligne ou de l'adresse du pointeur d'instruction.|  
|**ID de processus**|ID du processus \(PID\) de l'exécution du profilage.|  
|**Nom du processus**|Nom du processus.|  
|**Nom de module**|Nom du module qui contient la fonction, la ligne ou le pointeur d'instruction.|  
|**Chemin de module**|Chemin d'accès du module qui contient le module, la fonction, la ligne ou le pointeur d'instruction.|  
|**Source File**|Fichier source qui contient la définition de cette fonction.|  
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|  
|**Exemples inclusifs**|-   Pour une fonction, le nombre d'échantillons dans lesquels cette fonction ou une fonction appelée par cette fonction s'exécutait; autrement dit, le nombre d'échantillons de pile des appels qui ont contenu cette fonction.<br />-   Pour un module, le nombre d'échantillons dans lesquels au moins, une fonction du module s'exécutait.<br />-   Pour une ligne ou une instruction, le nombre d'échantillons dans lesquels cette ligne ou cette instruction s'exécutait.|  
|**% d'échantillons inclusifs**|-   Pour une fonction ou un module, le pourcentage de tous les échantillons du profilage qui étaient des échantillons inclusifs pour cette fonction ou ce module.<br />-   Pour une ligne ou une instruction, pourcentage de tous les échantillons du profilage dans lesquels cette ligne ou cette instruction était exécutée.|  
|**Exemples exclusifs**|-   Pour une fonction, le nombre d'échantillons de pile des appels dans lesquels cette fonction s'exécutait directement ; autrement dit, le nombre d'échantillons dans lesquels cette fonction se trouvait en haut de la pile des appels.<br />-   Pour un module, somme des échantillons exclusifs des fonctions dans le module.<br />-   Pour une ligne ou une instruction, le nombre d'échantillons dans lesquels cette ligne ou cette instruction s'exécutait.|  
|**% d'échantillons exclusifs**|-   Pour une fonction ou un module, le pourcentage de tous les échantillons du profilage qui étaient des échantillons exclusifs de cette fonction ou ce module.<br />-   Pour une ligne ou une instruction, pourcentage de tous les échantillons du profilage dans lesquels cette ligne ou cette instruction était exécutée.|  
  
## Voir aussi  
 [Vue Modules \- échantillonnage](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Vue Modules \- instrumentation](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Modules, vue](../profiling/modules-view-instrumentation-data.md)