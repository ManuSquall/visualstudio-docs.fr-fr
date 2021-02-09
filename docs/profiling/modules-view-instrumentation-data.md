---
title: Modules, vue - Données d’instrumentation | Microsoft Docs
description: Découvrez comment la vue modules affiche les données de performances regroupées par les modules qui se trouvaient dans les données de profilage.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 895b9589-1987-4160-916f-53b898a69cf0
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 031068d159b7004b7cfe7fcf1c747c2eb582afc8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879772"
---
# <a name="modules-view---instrumentation-data"></a>Modules, vue - données d’instrumentation
La vue Modules affiche les données de performances regroupées selon les modules contenus dans les données de profilage. Les fonctions du module sont répertoriées sous le nœud du module.

## <a name="general"></a>Général
 Les colonnes générales permettent d’identifier la fonction dans une ligne de la vue.

|Colonne|Description|
|------------|-----------------|
|**Nom**|Nom de la fonction ou du module.|
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|
|**Nombre d’appels**|Nombre total d’appels effectués à cette fonction ou à ce module.|
|**Source File**|Fichier source contenant la définition pour cette fonction.|
|**Nom du module**|Nom du module qui contient la fonction.|
|**Chemin du module**|Chemin d’accès du module qui contient la fonction.|
|**ID de processus**|ID du processus (PID) de l'exécution du profilage.|
|**Nom du processus**|Nom du processus dans lequel le module ou la fonction s’exécutait.|
|**Traitement de sondes du temps exclusif**|Surcharge de temps pour cette fonction ou ce module en raison de l’instrumentation.|
|**Traitement des sondes temps inclus**|Surcharge de temps pour cette fonction ou ce module et ses fonctions enfants en raison de l’instrumentation.|

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
 Les valeurs de temps inclusif d’application indiquent le temps qu’a passé une fonction dans la pile des appels. Cette durée n’inclut pas le temps consacré aux appels au système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S. Toutefois, elle inclut le temps passé dans les fonctions enfants.

|Colonne|Description|
|------------|-----------------|
|**Temps inclusif d’application**|-   Pour une fonction, temps consacré aux appels à la fonction. Cela inclut le temps passé dans les fonctions enfants, mais exclut le temps consacré aux appels au système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S.<br />-   Pour un module, période pendant laquelle au moins une fonction du module était sur la pile des appels. Cela exclut le temps consacré aux appels au système d’exploitation.|
|**% du temps inclusif d’application**|Pourcentage du temps inclusif écoulé total de l’exécution du profilage passé dans le temps inclusif d’application de ce module ou de cette fonction.|
|**Temps inclusif d’application moy.**|-   Pour une fonction, temps inclusif d’application moyen d’un appel à cette fonction.<br />-   Pour un module, temps inclusif d’application moyen de tous les appels aux fonctions du module.|
|**Temps inclusif d’application max.**|-   Pour une fonction, temps inclusif d’application maximal d’un appel à cette fonction.<br />-   Pour un module, temps inclusif d’application maximal de tous les appels aux fonctions du module.|
|**Temps inclusif d’application min.**|-   Pour une fonction, temps inclusif d’application minimal d’un appel à ce module ou à cette fonction.<br />-   Pour un module, temps inclusif d’application minimal de tous les appels aux fonctions du module.|

## <a name="application-exclusive-values"></a>Valeurs de temps exclusif d’application
 Les valeurs de temps exclusif d’application indiquent le temps passé dans le module ou la fonction. Ces valeurs n’incluent ni le temps passé dans les fonctions enfants, ni le temps consacré aux appels au système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S.

|Colonne|Description|
|------------|-----------------|
|**Temps exclusif d’application**|Temps exclusif d’application total de tous les appels à ce module ou à cette fonction.|
|**% du temps exclusif d’application**|Pourcentage du temps exclusif écoulé total de l’exécution du profilage passé dans le temps exclusif d’application de ce module ou de cette fonction.|
|**Temps exclusif d’application moy.**|-   Pour une fonction, temps exclusif d’application moyen d’un appel à cette fonction.<br />-   Pour un module, temps exclusif d’application moyen de tous les appels aux fonctions du module.|
|**Temps exclusif d’application max.**|-   Pour une fonction, temps exclusif d’application maximal d’un appel à cette fonction.<br />-   Pour un module, temps exclusif d’application maximal de tous les appels aux fonctions du module.|
|**Temps exclusif d’application min.**|-   Pour une fonction, temps exclusif d’application minimal d’un appel à ce module ou à cette fonction.<br />-   Pour un module, temps exclusif d’application minimal de tous les appels aux fonctions du module.|

## <a name="see-also"></a>Voir aussi
- [Vue Modules](../profiling/modules-view-sampling-data.md)
- [Vue modules-Instrumentation](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [Vue modules-échantillonnage](../profiling/modules-view-dotnet-memory-sampling-data.md)
