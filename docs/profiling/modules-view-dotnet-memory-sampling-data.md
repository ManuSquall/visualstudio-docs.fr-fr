---
title: Modules, vue - Données d’échantillonnage de mémoire .NET | Microsoft Docs
description: En savoir plus sur la vue modules des données d’allocation de mémoire .NET collectées à l’aide de la méthode d’échantillonnage.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 9c05b51a-8382-44cf-a8f7-3fabdd2e8f1b
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: b9c00fd7647d6ba3da62d913e0371dc8cf300ca7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879824"
---
# <a name="modules-view---net-memory-sampling-data"></a>Modules, vue - données d’échantillonnage de la mémoire .NET
La vue Modules des données d’allocation de mémoire .NET collectées à l’aide de la méthode d’échantillonnage regroupe les données de mémoire selon les modules exécutés dans le cadre de l’exécution du profilage. Chaque module est la racine d’une arborescence hiérarchique. Les fonctions du module sont répertoriées sous le nœud du module.

 Les numéros de ligne de fichier source des instructions qui allouent la mémoire sont répertoriés sous le nœud de la fonction, et les adresses des instructions chargées de l’allocation sont répertoriées sous le nœud de la ligne. Les valeurs inclusives et exclusives sont toujours les mêmes pour les données de ligne et les données d’instruction.

|Colonne|Description|
|------------|-----------------|
|**Nom**|Nom du module, de la fonction, du numéro de ligne ou de l’adresse d’instruction.|
|**ID de processus**|ID du processus (PID) de l'exécution du profilage.|
|**Nom du processus**|Nom du processus.|
|**Nom du module**|Nom du module qui contient la fonction.|
|**Chemin du module**|Chemin du module.|
|**Source File**|Fichier source contenant la définition pour cette fonction.|
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|
|**Allocations inclusives**|-   Pour une fonction, nombre total d’objets créés par la fonction. Ce nombre inclut les objets créés dans les fonctions appelées par cette fonction.<br />-   Pour un module, nombre d’objets d’une exécution du profilage alloués alors qu’au moins une fonction du module s’exécutait. Ce nombre inclut les objets créés dans les fonctions appelées par les fonctions de module.<br />-   Pour une ligne ou une instruction, nombre total d’objets alloués par la ligne ou l’instruction.|
|**% d’allocations inclusives**|Pourcentage de tous les objets alloués dans le cadre de l’exécution du profilage qui étaient des allocations inclusives du module, de la fonction, de la ligne ou de l’instruction.|
|**Allocations exclusives**|- Pour la fonction active, nombre d’objets créés lorsque la fonction exécutait le code du corps de la fonction (autrement dit, lorsque la fonction se trouvait en haut de la pile des appels). Ce nombre n’inclut pas les objets créés dans les fonctions appelées par cette fonction.<br />-   Pour un module, somme des allocations exclusives des fonctions présentes dans le module.<br />-   Pour une ligne ou une instruction, nombre total d’objets créés par cette ligne ou cette instruction.|
|**% d’allocations exclusives**|Pourcentage de tous les objets alloués dans le cadre de l’exécution du profilage qui étaient des allocations exclusives du module, de la fonction, de la ligne ou de l’instruction.|
|**Octets inclusifs**|-   Pour une fonction, nombre d’octets alloués par la fonction. Ce nombre inclut les octets alloués dans les fonctions appelées par cette fonction.<br />-   Pour un module, nombre d’octets alloués dans le cadre d’une exécution du profilage qui ont été alloués alors qu’au moins une fonction du module s’exécutait. Ce nombre inclut les objets créés dans toutes les fonctions appelées par les fonctions de module.<br />-   Pour une ligne ou une instruction, nombre total d’objets créés par la ligne ou l’instruction.|
|**% d’octets inclusifs**|Pourcentage de tous les octets alloués dans le cadre de l’exécution du profilage qui étaient des octets inclusifs du module, de la fonction, de la ligne ou de l’instruction.|
|**Octets exclusifs**|-   Pour une fonction, nombre total d’octets alloués par la fonction. Ce nombre n’inclut pas les octets alloués dans les fonctions appelées par cette fonction.<br />-   Pour un module, somme des octets exclusifs qui ont été alloués par les fonctions présentes dans le module.<br />-   Pour une ligne ou une instruction, nombre total d’objets alloués par cette ligne ou cette instruction.|
|**% d’octets exclusifs**|Pourcentage de tous les octets alloués dans le cadre de l’exécution du profilage qui étaient des octets exclusifs du module, de la fonction, de la ligne ou de l’instruction.|

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour personnaliser les colonnes de la vue de rapport](../profiling/how-to-customize-report-view-columns.md)
- [Vue modules-Instrumentation](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [Vue Modules](../profiling/modules-view-sampling-data.md)
- [Vue Modules](../profiling/modules-view-instrumentation-data.md)
