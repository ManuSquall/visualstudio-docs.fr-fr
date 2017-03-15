---
title: "Mode Appelant/Appel&#233; - donn&#233;es d’&#233;chantillonnage du profileur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "méthode de profilage par échantillonnage, mode Appelant/Appelé"
  - "mode Appelant/Appelé"
ms.assetid: 28e85ed5-1512-4b59-bb84-138a2abca7dd
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Mode Appelant/Appel&#233; - donn&#233;es d’&#233;chantillonnage du profileur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le mode Appelant\/Appelé affiche les informations de profilage d'une fonction sélectionnée et ses fonctions parents et enfants.  Le mode Appelant\/Appelé contient trois grilles.  
  
 **Fonction actuelle** s'affiche dans la grille centrale et contient les informations de profilage de la fonction sélectionnée.  Les valeurs comprennent tous les appels échantillonnés à la fonction.  
  
 **Fonctions qui ont appelé la fonction active** s'affiche dans la grille supérieure et indique les contributions individuelles des fonctions \(parents\) de l'appelant aux valeurs de la fonction \(active\) sélectionnée.  
  
 **Fonctions qui ont été appelées par la fonction active** s'affiche dans la grille inférieure et indique les informations de profilage des fonctions d'appelé \(enfant\) de la fonction sélectionnée lorsque la fonction enfant a été appelée par la fonction actuelle.  
  
> [!NOTE]
>  Les fonctionnalités de sécurité renforcée dans windows 8 et Windows Server 2012 requises des modifications significatives de la manière que le profileur Visual Studio collecte des données sur ces plateformes.  Les applications de mémoire de fenêtres requièrent également de nouvelles techniques de collection.  Consultez [Profilage d'applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
|Colonne|Description|  
|-------------|-----------------|  
|**ID de processus**|ID du processus \(PID\) de l'exécution du profilage.|  
|**Nom du processus**|Nom du processus.|  
|**Nom de module**|Nom du module qui contient la fonction.|  
|**Chemin de module**|Chemin d'accès du module qui contient la fonction.|  
|**Source File**|Fichier source qui contient la définition de cette fonction.|  
|**Nom de la fonction**|Nom complet de la fonction.|  
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|  
|**Adresse de la fonction**|Adresse de la fonction.|  
|**Type**|Contexte de la fonction :<br /><br /> -   **0** \- la fonction active<br />-   **1** \- une fonction qui appelle la fonction active<br />-   **2** \- une fonction qui est appelée par la fonction active|  
|**Nom de la fonction racine**|Nom de la fonction actuelle.|  
|**Exemples inclusifs**|-   Pour la fonction active, nombre d'échantillons collectés malgré l'exécution de cette fonction ou de l'une de ses fonctions enfants.<br />-   Pour une fonction d'appelant, nombre d'échantillons inclusifs de la fonction active qui ont été collectés lorsque cette fonction a appelé la fonction active.<br />-   Pour une fonction d'appelant, nombre d'échantillons inclusifs de cette fonction qui ont été collectés lorsque la fonction active a appelé cette fonction.|  
|**% d'échantillons inclusifs**|Pourcentage de tous les échantillons au cours de l'exécution du profilage qui correspondaient à des échantillons inclusifs de cette fonction.|  
|**Exemples exclusifs**|-   Pour la fonction active, nombre d'échantillons dans l'exécution du profilage qui ont été collectés lorsque cette fonction s'exécutait directement, c'est\-à\-dire lorsque cette fonction était en haut de la pile des appels.  Les échantillons collectés lorsque les fonctions enfants de cette fonction s'exécutent ne sont pas comptés dans les nombres exclusifs.<br />-   Pour une fonction d'appelant, nombre d'échantillons exclusifs de la fonction active qui ont été collectés lorsque cette fonction a appelé la fonction active.<br />-   Pour une fonction d'appelant, nombre d'échantillons exclusifs de cette fonction qui ont été collectés lorsque la fonction active a appelé cette fonction.|  
|**% d'échantillons exclusifs**|Pourcentage de tous les échantillons dans l'exécution du profilage qui correspondaient à des échantillons exclusifs de cette fonction.|  
  
## Voir aussi  
 [Mode Appelant\/Appelé \- échantillonnage](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Mode Appelant\/Appelé \- instrumentation](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Mode Appelant\/Appelé](../profiling/caller-callee-view-instrumentation-data.md)