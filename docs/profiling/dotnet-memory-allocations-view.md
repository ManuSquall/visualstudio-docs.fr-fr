---
title: Vue Allocations de mémoire .NET | Microsoft Docs
description: En savoir plus sur la vue allocations de mémoire .NET, qui répertorie les types créés au cours de l’exécution du profilage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.allocation
helpviewer_keywords:
- performance reports, allocation view
- Allocations view
- profiling tools, Allocation view
- profiling tools reports, Allocation view
ms.assetid: 01eb876e-c413-4516-977b-4f896929e8a6
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f52a30eef50c783ea96d403c25837f9bf2515a52
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801282"
---
# <a name="net-memory-allocations-view"></a>Mode Allocations de mémoire .NET
La vue Allocations liste les types qui ont été créés au cours de l’exécution du profilage. Chaque type est le nœud racine d’une arborescence des appels qui affiche les chemins d’exécution des fonctions qui ont entraîné les allocations du type.

 Les données d’une ligne de type montrent le nombre total d’objets du type qui ont été créés au cours de l’exécution du profilage, et le nombre total d’octets alloués pour les objets de ce type. Les valeurs inclusives et exclusives d’un type sont toujours les mêmes.

- Les valeurs inclusives correspondent aux objets créés dans les instances de la fonction et de ses fonctions enfants qui ont été appelées par la fonction parente dans l’arborescence des appels.

- Les valeurs exclusives correspondent aux objets qui ont été créés directement par la fonction quand ils ont été appelés par la fonction parente. Les objets créés dans des fonctions enfants ne sont pas inclus.

  Les données d’une fonction montrent le nombre d’objets créés et le nombre d’octets alloués pour les objets du type parent.

## <a name="highlight-the-execution-hot-path"></a>Mettre en surbrillance le chemin réactif d’exécution
 Vous pouvez trouver le chemin d’exécution de l’arborescence des appels qui a créé le plus d’objets du type parent.

- Pour afficher le chemin le plus actif, cliquez avec le bouton droit sur le type ou la fonction, puis cliquez sur **Développer le chemin réactif**.

|Colonne|Description|
|------------|-----------------|
|**Nom**|Nom du type alloué ou de la fonction allouée.|
|**ID de processus**|ID du processus (PID) de l'exécution du profilage.|
|**Nom du processus**|Nom du processus.|
|**Nom du module**|Nom du module qui contient le type ou la fonction.|
|**Chemin du module**|Chemin du module qui contient le type ou la fonction.|
|**Source File**|Fichier source contenant la définition pour le type ou la fonction.|
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette définition de type ou de cette fonction dans le fichier source.|
|**Niveau**|Indique si les données concernent un type ou une fonction.|
|**Allocations inclusives**|-   Pour une fonction, nombre total d’objets du type parent créés par la fonction. Ce nombre inclut les objets créés dans les fonctions enfants.<br />-   Pour un type, nombre total d’instances de ce type qui ont été créées.|
|**% d’allocations inclusives**|-   Pour une fonction, pourcentage de tous les objets créés lors de l’exécution du profilage qui étaient des allocations inclusives de ce type parent par la fonction.<br />-   Pour un type, pourcentage du nombre total d’objets créés lors de l’exécution du profilage et qui étaient des instances du type.|
|**Allocations exclusives**|-   Pour une fonction, nombre d’objets créés quand la fonction s’exécutait directement en haut de la pile des appels. Ce nombre n’inclut pas les objets créés dans les fonctions enfants.<br />-   Pour un type, nombre total d’instances de ce type qui ont été créées.|
|**% d’allocations exclusives**|-   Pour une fonction, pourcentage de tous les objets créés lors de l’exécution du profilage qui étaient des allocations exclusives de ce type parent par la fonction.<br />-   Pour un type, pourcentage du nombre total d’objets créés lors de l’exécution du profilage et qui étaient des instances du type.|
|**Octets inclusifs**|-   Pour une fonction, nombre d’octets de mémoire alloués par la fonction pour des objets du type parent. Ce nombre inclut la mémoire allouée par ses fonctions enfants.<br />-   Pour un type, nombre total d’octets qui ont été alloués lors de l’exécution du profilage pour les instances du type.|
|**% d’octets inclusifs**|-   Pour une fonction, pourcentage de toute la mémoire allouée lors de l’exécution du profilage qui était constitué d’allocations inclusives du type parent par la fonction.<br />-   Pour un type, pourcentage de toute la mémoire allouée lors de l’exécution du profilage qui a été alloué pour des instances du type.|
|**Octets exclusifs**|-   Pour une fonction, nombre d’octets de mémoire alloués par la fonction pour des objets du type parent. Ce nombre n’inclut pas la mémoire allouée par ses fonctions enfants.<br />-   Pour un type, nombre total d’octets qui ont été alloués lors de l’exécution du profilage pour les instances du type.|
|**% d’octets exclusifs**|-   Pour une fonction, pourcentage de toute la mémoire allouée lors de l’exécution du profilage qui était constitué d’allocations exclusives du type parent par la fonction.<br />-   Pour un type, pourcentage de toute la mémoire allouée lors de l’exécution du profilage qui a été alloué pour des instances du type.|
