---
title: Vue Appelant/Appelé - Données d’échantillonnage | Microsoft Docs
description: Lisez comment la vue appelant/appelé affiche les informations de profilage pour une fonction sélectionnée et ses fonctions parentes et enfants dans Explorateur de performances.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Caller/Callee view
- Caller/Callee view
ms.assetid: 28e85ed5-1512-4b59-bb84-138a2abca7dd
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 376475d2a392b86b14a73ba45c5669eaaf338898
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886403"
---
# <a name="callercallee-view---sampling-data"></a>Vue Appelant/Appelé - Données d’échantillonnage
La vue Appelant/Appelé affiche des données de profilage pour la fonction sélectionnée, ainsi que pour ses fonctions parents et enfants. La vue Appelant/Appelé comprend trois grilles.

 La grille centrale intitulée **Fonction active** contient les informations de profilage associées à la fonction sélectionnée. Ces valeurs incluent tous les appels échantillonnés émis vers la fonction.

 La grille supérieure intitulée **Fonctions qui ont appelé la fonction active** contient les contributions de chaque fonction d’appelant (parent) aux valeurs de la fonction sélectionnée (active).

 La grille inférieure intitulée **Fonctions qui ont été appelées par la fonction active** contient des informations de profilage pour les fonctions d’appelé (enfants) de la fonction sélectionnée lorsque la fonction enfant a été appelée par la fonction active.

> [!NOTE]
> Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications UWP nécessitent aussi de nouvelles techniques de collecte. Consultez [Outils d’exécution des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

|Colonne|Description|
|------------|-----------------|
|**ID de processus**|ID du processus (PID) de l'exécution du profilage.|
|**Nom du processus**|Nom du processus.|
|**Nom du module**|Nom du module qui contient la fonction.|
|**Chemin du module**|Chemin d’accès du module qui contient la fonction.|
|**Source File**|Fichier source contenant la définition pour cette fonction.|
|**Nom de la fonction**|Nom complet de la fonction.|
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|
|**Adresse de la fonction**|Adresse de la fonction.|
|**Type**|Contexte de la fonction :<br /><br /> -   **0** -la fonction active<br />-   **1** -fonction qui appelle la fonction active<br />-   **2** -fonction appelée par la fonction active|
|**Nom de fonction racine**|Nom de la fonction actuelle.|
|**Échantillons inclusifs**|- Pour la fonction active, nombre d’échantillons collectés malgré l’exécution de cette fonction ou de l’une de ses fonctions enfants.<br />- Pour une fonction d’appelant, nombre d’échantillons inclusifs de la fonction active qui ont été collectés lorsque cette fonction a appelé la fonction active.<br />- Pour une fonction d’appelé, nombre d’échantillons inclusifs de cette fonction qui ont été collectés lorsque la fonction active a appelé cette fonction.|
|**% des échantillons inclusifs**|Pourcentage de tous les échantillons de l’exécution du profilage qui étaient des échantillons inclusifs de cette fonction.|
|**Échantillons exclusifs**|- Pour la fonction active, nombre d’échantillons de l’exécution du profilage qui ont été collectés pendant l’exécution directe de cette fonction ; autrement dit, lorsque cette fonction se trouvait en haut de la pile des appels. Les échantillons collectés lors de l’exécution des fonctions enfants de cette fonction ne sont pas comptabilisés comme des échantillons exclusifs.<br />- Pour une fonction d’appelant, nombre d’échantillons exclusifs de la fonction active qui ont été collectés lorsque cette fonction a appelé la fonction active.<br />- Pour une fonction d’appelé, nombre d’échantillons exclusifs de cette fonction qui ont été collectés lorsque la fonction active a appelé cette fonction.|
|**% d’échantillons exclusifs**|Pourcentage de tous les échantillons de l’exécution du profilage qui étaient des échantillons exclusifs de cette fonction.|

## <a name="see-also"></a>Voir aussi
- [Vue appelant/appelé-données d’échantillonnage de la mémoire .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Vue appelant/appelé-données d’instrumentation de la mémoire .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
- [Vue appelant/appelé-données d’instrumentation](../profiling/caller-callee-view-instrumentation-data.md)
