---
title: Vue Modules - Données d’instrumentation de la mémoire .NET | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 26516139-0981-41de-917d-ad5769391b8d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: cb3117ff480e124aab6333eaed612c0438ed3911
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62830044"
---
# <a name="modules-view---net-memory-instrumentation-data"></a>Modules, vue - Données d’instrumentation de la mémoire .NET
La vue Modules des données d’allocation de mémoire .NET collectées à l’aide de la méthode d’instrumentation regroupe les données de mémoire et de minutage selon les modules exécutés dans le cadre de l’exécution du profilage. Les données de profilage pour les fonctions du module sont répertoriées sous le nœud du module.

## <a name="general"></a>Général

|Colonne|Description|
|------------|-----------------|
|**Name**|Nom de la fonction ou du module.|
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|
|**Nombre d’appels**|Nombre total d’appels effectués à cette fonction ou à ce module.|
|**Fichier source**|Fichier source contenant la définition de cette fonction.|
|**Nom du module**|Nom du module qui contient la fonction.|
|**Chemin de module**|Chemin d’accès du module qui contient la fonction.|
|**ID du processus**|ID du processus (PID) de l'exécution du profilage.|
|**Nom du processus**|Nom du processus dans lequel le module ou la fonction s’exécutait.|
|**Traitement de sondes du temps exclusif**|Surcharge de temps pour cette fonction ou ce module en raison de l’instrumentation.|
|**Traitement des sondes temps inclus**|Surcharge de temps pour cette fonction ou ce module et ses fonctions enfants en raison de l’instrumentation.|

## <a name="net-memory-values"></a>Valeurs de mémoire .NET
 Les valeurs de mémoire .NET inclusives d’une fonction indiquent le nombre (allocations) et la taille (octets) des objets créés par la fonction et ses fonctions enfants.

 Les valeurs de mémoire exclusives indiquent le nombre et la taille des objets créés par la fonction, et non par ses fonctions enfants.

 Les valeurs de mémoire inclusives et exclusives d’un module représentent la somme des valeurs de mémoire inclusives et exclusives des fonctions présentes dans le module.

|Colonne|Description|
|------------|-----------------|
|**Allocations inclusives**|-   Pour une fonction, nombre total d’objets créés par la fonction. Ce nombre inclut les objets créés par les fonctions appelées par la fonction.<br />-   Pour un module, nombre d’objets d’une exécution du profilage alloués quand au moins une fonction du module s’exécutait. Ce nombre inclut les objets alloués dans les fonctions qui ont été générées par des appels de fonctions de module.|
|**% d’allocations inclusives**|Pourcentage de tous les objets alloués dans le cadre de l’exécution du profilage qui étaient des allocations inclusives du module ou de la fonction.|
|**Allocations exclusives**|-   Pour une fonction, nombre d’objets créés quand la fonction exécutait du code dans le corps de la fonction (autrement dit, quand elle se trouvait en haut de la pile des appels). Ce nombre n’inclut pas les objets créés dans les fonctions appelées par la fonction.<br />-   Pour un module, somme des allocations exclusives des fonctions présentes dans le module.|
|**% d’allocations exclusives**|Pourcentage de tous les objets alloués dans le cadre de l’exécution du profilage qui étaient des allocations exclusives du module ou de la fonction.|
|**Octets exclusifs**|-   Pour une fonction, nombre total d’octets de mémoire alloués quand la fonction exécutait le code dans le corps de la fonction (autrement dit, quand elle se trouvait en haut de la pile des appels). Ce nombre n’inclut pas les octets alloués dans les fonctions appelées par la fonction.<br />-   Pour un module, somme des octets exclusifs qui ont été alloués par les fonctions présentes dans le module.|
|**% d’octets exclusifs**|Pourcentage de tous les octets alloués dans le cadre de l’exécution du profilage qui étaient des octets exclusifs du module, de la fonction, de la ligne ou de l’instruction.|
|**Octets inclusifs**|-   Pour une fonction, nombre d’octets alloués par la fonction. Ce nombre inclut les octets alloués dans les fonctions appelées par la fonction.<br />-   Pour un module, nombre d’octets alloués dans le cadre d’une exécution du profilage qui ont été alloués quand au moins une fonction du module s’exécutait. Ce nombre inclut les objets créés dans toutes les fonctions appelées par les fonctions de module.|
|**% d’octets inclusifs**|Pourcentage de tous les octets alloués dans le cadre de l’exécution du profilage qui étaient des octets inclusifs du module ou de la fonction.|

## <a name="elapsed-inclusive-values"></a>Valeurs de temps inclusif écoulé
 Les valeurs de temps inclusif écoulé indiquent le temps qu’a passé une fonction dans la pile des appels. Cette durée comprend le temps passé dans les fonctions enfants, ainsi que le temps consacré aux appels au système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S.

|Colonne|Description|
|------------|-----------------|
|**Temps inclusif écoulé**|-   Pour une fonction, temps passé dans la fonction. Cela inclut le temps passé dans les fonctions enfants, ainsi que le temps consacré aux appels au système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S.<br />-   Pour un module, période pendant laquelle au moins une fonction du module était sur la pile des appels.|
|**% de temps inclusif écoulé**|Pourcentage du temps inclusif écoulé total de l’exécution du profilage passé dans le temps inclusif écoulé total de ce module ou de cette fonction.|
|**Temps inclusif écoulé moy.**|-   Pour une fonction, temps inclusif écoulé moyen d’un appel à cette fonction.<br />-   Pour un module, temps inclusif écoulé moyen de tous les appels aux fonctions du module.|
|**Temps inclusif écoulé max.**|-   Pour une fonction, temps inclusif écoulé maximal d’un appel à cette fonction.<br />-   Pour un module, temps inclusif écoulé maximal de tous les appels aux fonctions du module.|
|**Temps inclusif écoulé min.**|-   Pour une fonction, temps inclusif écoulé minimal d’un appel à ce module ou à cette fonction.<br />-   Pour un module, temps inclusif écoulé minimal de tous les appels aux fonctions du module.|

## <a name="elapsed-exclusive-values"></a>Valeurs de temps exclusif écoulé
 Les valeurs de temps exclusif écoulé indiquent la durée pendant laquelle une fonction s’est exécutée directement en haut de la pile des appels. Cette durée inclut le temps consacré aux appels au système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S, mais elle n’inclut pas le temps passé dans les fonctions enfants.

|Colonne|Description|
|------------|-----------------|
|**Temps exclusif écoulé**|-   Pour une fonction, temps passé dans le module ou la fonction. Cela inclut le temps consacré aux appels au système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S, mais exclut le temps passé dans les fonctions enfants.<br />-   Pour un module, somme des temps exclusifs écoulés des fonctions présentes dans le module.|
|**% de temps exclusif écoulé**|Pourcentage du temps exclusif écoulé total de l’exécution du profilage passé dans le temps exclusif écoulé total de ce module ou de cette fonction.|
|**Temps exclusif écoulé moy.**|-   Pour une fonction, temps exclusif écoulé moyen d’un appel à cette fonction.<br />-   Pour un module, temps exclusif écoulé moyen de tous les appels aux fonctions du module.|
|**Temps exclusif écoulé max.**|-   Pour une fonction, temps exclusif écoulé maximal d’un appel à cette fonction.<br />-   Pour un module, temps exclusif écoulé maximal de tous les appels aux fonctions du module.|
|**Temps exclusif écoulé min.**|-   Pour une fonction, temps exclusif écoulé minimal d’un appel à ce module ou à cette fonction.<br />-   Pour un module, temps exclusif écoulé minimal de tous les appels aux fonctions du module.|

## <a name="application-inclusive-values"></a>Valeurs de temps inclusif d’application
 Les valeurs de temps inclusif d’application indiquent le temps qu’a passé une fonction dans la pile des appels. Cette durée n’inclut pas le temps consacré aux appels au système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S, mais elle inclut le temps passé dans les fonctions enfants.

|Colonne|Description|
|------------|-----------------|
|**Temps inclusif d’application**|-   Pour une fonction, temps consacré aux appels à la fonction. Cela inclut le temps passé dans les fonctions enfants, mais exclut le temps consacré aux appels au système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S.<br />-   Pour un module, période pendant laquelle au moins une fonction du module était sur la pile des appels, à l’exclusion du temps consacré aux appels au système d’exploitation.|
|**% du temps inclusif d’application**|Pourcentage du temps inclusif écoulé total de l’exécution du profilage passé dans le temps inclusif d’application de ce module ou de cette fonction.|
|**Temps inclusif d’application moy.**|-   Pour une fonction, temps inclusif d’application moyen d’un appel à cette fonction.<br />-   Pour un module, temps inclusif d’application moyen de tous les appels aux fonctions du module.|
|**Temps inclusif d’application max.**|-   Pour une fonction, temps inclusif d’application maximal d’un appel à cette fonction.<br />-   Pour un module, temps inclusif d’application maximal de tous les appels aux fonctions du module.|
|**Temps inclusif d’application min.**|-   Pour une fonction, temps inclusif d’application minimal d’un appel à ce module ou à cette fonction.<br />-   Pour un module, temps inclusif d’application minimal de tous les appels aux fonctions du module.|

## <a name="application-exclusive-values"></a>Valeurs de temps exclusif d’application
 Les valeurs de temps exclusif d’application indiquent le temps passé dans le module ou la fonction, à l’exclusion du temps passé dans les fonctions enfants. Le temps indiqué exclut également le temps consacré aux appels au système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S.

|Colonne|Description|
|------------|-----------------|
|**Temps exclusif d’application**|-   Pour une fonction, temps exclusif d’application total des les appels à cette fonction.<br />-   Pour un module, temps exclusif d’application total de tous les appels aux fonctions du module.|
|**% du temps exclusif d’application**|Pourcentage du temps exclusif écoulé total de l’exécution du profilage passé dans le temps exclusif d’application de ce module ou de cette fonction.|
|**Temps exclusif d’application moy.**|-   Pour une fonction, temps exclusif d’application moyen d’un appel à cette fonction.<br />-   Pour un module, temps exclusif d’application moyen de tous les appels aux fonctions du module.|
|**Temps exclusif d’application max.**|-   Pour une fonction, temps exclusif d’application maximal d’un appel à cette fonction.<br />-   Pour un module, temps exclusif d’application maximal de tous les appels aux fonctions du module.|
|**Temps exclusif d’application min.**|-   Pour une fonction, temps exclusif d’application minimal d’un appel à ce module ou à cette fonction.<br />-   Pour un module, temps exclusif d’application minimal de tous les appels aux fonctions du module.|

## <a name="see-also"></a>Voir aussi
- [Modules, vue - échantillonnage](../profiling/modules-view-dotnet-memory-sampling-data.md)
- [Modules, mode](../profiling/modules-view-instrumentation-data.md)
- [Modules, mode](../profiling/modules-view-sampling-data.md)