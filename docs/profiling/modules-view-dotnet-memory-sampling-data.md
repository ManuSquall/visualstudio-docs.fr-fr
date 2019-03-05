---
title: Modules, vue - Données d’échantillonnage de mémoire .NET | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 9c05b51a-8382-44cf-a8f7-3fabdd2e8f1b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0b4870a17988c4f926e04aca24e50419c4a27165
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56645795"
---
# <a name="modules-view---net-memory-sampling-data"></a>Modules, vue - données d’échantillonnage de la mémoire .NET
La vue Modules des données d’allocation de mémoire .NET collectées à l’aide de la méthode d’échantillonnage regroupe les données de mémoire selon les modules exécutés dans le cadre de l’exécution du profilage. Chaque module est la racine d’une arborescence hiérarchique. Les fonctions du module sont répertoriées sous le nœud du module.

 Les numéros de ligne de fichier source des instructions qui allouent la mémoire sont répertoriés sous le nœud de la fonction, et les adresses des instructions chargées de l’allocation sont répertoriées sous le nœud de la ligne. Les valeurs inclusives et exclusives sont toujours les mêmes pour les données de ligne et les données d’instruction.

|Colonne|Description|
|------------|-----------------|
|**Name**|Nom du module, de la fonction, du numéro de ligne ou de l’adresse d’instruction.|
|**ID du processus**|ID du processus (PID) de l'exécution du profilage.|
|**Nom du processus**|Nom du processus.|
|**Nom du module**|Nom du module qui contient la fonction.|
|**Chemin du module**|Chemin du module.|
|**Fichier source**|Fichier source contenant la définition pour cette fonction.|
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|
|**Allocations inclusives**|-   Pour une fonction, nombre total d’objets créés par la fonction. Ce nombre inclut les objets créés dans les fonctions appelées par cette fonction.<br />-   Pour un module, nombre d’objets d’une exécution du profilage alloués alors qu’au moins une fonction du module s’exécutait. Ce nombre inclut les objets créés dans les fonctions appelées par les fonctions de module.<br />-   Pour une ligne ou une instruction, nombre total d’objets alloués par la ligne ou l’instruction.|
|**% d’allocations inclusives**|Pourcentage de tous les objets alloués dans le cadre de l’exécution du profilage qui étaient des allocations inclusives du module, de la fonction, de la ligne ou de l’instruction.|
|**Allocations exclusives**|-   Pour la fonction active, nombre d’objets créés quand la fonction exécutait le code du corps de la fonction (autrement dit, quand elle se trouvait en haut de la pile des appels). Ce nombre n’inclut pas les objets créés dans les fonctions appelées par cette fonction.<br />-   Pour un module, somme des allocations exclusives des fonctions présentes dans le module.<br />-   Pour une ligne ou une instruction, nombre total d’objets créés par cette ligne ou cette instruction.|
|**% d’allocations exclusives**|Pourcentage de tous les objets alloués dans le cadre de l’exécution du profilage qui étaient des allocations exclusives du module, de la fonction, de la ligne ou de l’instruction.|
|**Octets inclusifs**|-   Pour une fonction, nombre d’octets alloués par la fonction. Ce nombre inclut les octets alloués dans les fonctions appelées par cette fonction.<br />-   Pour un module, nombre d’octets alloués dans le cadre d’une exécution du profilage qui ont été alloués alors qu’au moins une fonction du module s’exécutait. Ce nombre inclut les objets créés dans toutes les fonctions appelées par les fonctions de module.<br />-   Pour une ligne ou une instruction, nombre total d’objets créés par la ligne ou l’instruction.|
|**% d’octets inclusifs**|Pourcentage de tous les octets alloués dans le cadre de l’exécution du profilage qui étaient des octets inclusifs du module, de la fonction, de la ligne ou de l’instruction.|
|**Octets exclusifs**|-   Pour une fonction, nombre total d’octets alloués par la fonction. Ce nombre n’inclut pas les octets alloués dans les fonctions appelées par cette fonction.<br />-   Pour un module, somme des octets exclusifs qui ont été alloués par les fonctions présentes dans le module.<br />-   Pour une ligne ou une instruction, nombre total d’objets alloués par cette ligne ou cette instruction.|
|**% d’octets exclusifs**|Pourcentage de tous les octets alloués dans le cadre de l’exécution du profilage qui étaient des octets exclusifs du module, de la fonction, de la ligne ou de l’instruction.|

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour personnaliser les colonnes de vue des rapports](../profiling/how-to-customize-report-view-columns.md)
- [Vue des modules - Instrumentation](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [Modules, mode](../profiling/modules-view-sampling-data.md)
- [Modules, mode](../profiling/modules-view-instrumentation-data.md)