---
title: Modules, vue - Données d’échantillonnage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Modules view
- sampling profiling method,Modules view
ms.assetid: 816f5633-65d7-41e5-aee1-033628d4e2df
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 04c714576a0207d4168f20a241d6f0c7dd29298c
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54784455"
---
# <a name="modules-view---sampling-data"></a>Modules, vue - Données d’échantillonnage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La vue Modules des données d’échantillonnage affiche les données de performances regroupées selon les modules contenus dans les données de profilage. Chaque module est la racine d’une arborescence hiérarchique. Les fonctions échantillonnées du module sont répertoriées sous le nœud du module.  
  
> [!NOTE]
>  Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications Windows Store demandent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Si la fonction était en cours d’exécution au moment de la collecte des échantillons (autrement dit, si elle était en haut de la pile des appels), les lignes sources et les adresses d’instruction qui s’exécutaient sont répertoriées sous le nœud de la fonction. Comme les données sont collectées pour une ligne source ou un pointeur d’instruction quand la ligne ou l’instruction est en cours d’exécution, les valeurs inclusives et exclusives sont toujours les mêmes pour les données de ligne et les données d’instruction.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Name**|Nom du module, de la fonction, du numéro de ligne ou de l’adresse du pointeur d’instruction.|  
|**ID du processus**|ID du processus (PID) de l'exécution du profilage.|  
|**Nom du processus**|Nom du processus.|  
|**Nom du module**|Nom du module qui contient la fonction, la ligne ou le pointeur d’instruction.|  
|**Chemin du module**|Chemin du module qui contient le module, la fonction, la ligne ou le pointeur d’instruction.|  
|**Fichier source**|Fichier source contenant la définition pour cette fonction.|  
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|  
|**Échantillons inclusifs**|-   Pour une fonction, nombre d’échantillons dans lesquels cette fonction ou une fonction appelée par cette fonction s’exécutait ; autrement dit, nombre d’échantillons de pile des appels qui ont contenu cette fonction.<br />-   Pour un module, nombre d’échantillons dans lesquels au moins une fonction du module s’exécutait.<br />-   Pour une ligne ou une instruction, nombre d’échantillons dans lesquels cette ligne ou cette instruction s’exécutait.|  
|**% des échantillons inclusifs**|-   Pour une fonction ou un module, pourcentage de tous les échantillons de l’exécution du profilage qui étaient des échantillons inclusifs de cette fonction ou de ce module.<br />-   Pour une ligne ou une instruction, pourcentage de tous les échantillons de l’exécution du profilage dans lesquels cette ligne ou cette instruction s’exécutait.|  
|**Échantillons exclusifs**|-   Pour une fonction, nombre d’échantillons de pile des appels dans lesquels cette fonction s’exécutait directement ; autrement dit, nombre d’échantillons dans lesquels cette fonction se trouvait en haut de la pile des appels.<br />-   Pour un module, somme des échantillons exclusifs des fonctions présentes dans le module.<br />-   Pour une ligne ou une instruction, nombre d’échantillons dans lesquels cette ligne ou cette instruction s’exécutait.|  
|**% d’échantillons exclusifs**|-   Pour une fonction ou un module, pourcentage de tous les échantillons de l’exécution du profilage qui étaient des échantillons exclusifs de cette fonction ou de ce module.<br />-   Pour une ligne ou une instruction, pourcentage de tous les échantillons de l’exécution du profilage dans lesquels cette ligne ou cette instruction s’exécutait.|  
  
## <a name="see-also"></a>Voir aussi  
 [Modules, vue - Échantillonnage](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Modules, vue - Instrumentation](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Modules, vue](../profiling/modules-view-instrumentation-data.md)
