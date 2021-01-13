---
title: Vue Arborescence des appels - Données d’échantillonnage de la mémoire .NET | Microsoft Docs
description: Découvrez comment la vue arborescence des appels affiche les données d’échantillonnage de la mémoire .NET pour les chemins d’exécution des fonctions qui ont été parcourus dans l’application profilée.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: fbb6cb60-420b-4ca9-8306-2494f7d321fe
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: c1a36f4661abb5535c71fcebcf9e486408a56b22
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150806"
---
# <a name="call-tree-view---net-memory-sampling-data"></a>Vue Arborescence des appels - Données d’échantillonnage de la mémoire .NET
La vue Arborescence des appels affiche les chemins d’exécution de la fonction empruntés dans l’application profilée. La racine de l’arborescence correspond au point d’entrée de l’application ou du composant. Chaque nœud de fonction répertorie toutes les fonctions qu’elle a appelées et les données d’allocation mémoire liées à ces appels de fonction.

 Les valeurs qui s’affichent dans la vue Arborescence des appels sont celles des instances de fonction qui ont été appelées par la fonction parent dans l’arborescence des appels. Les valeurs en pourcentage sont calculées en comparant la valeur de l’instance de la fonction au nombre total ou à la taille totale des allocations dans l’exécution du profilage.

## <a name="highlight-the-execution-hot-path"></a>Mettre en surbrillance le chemin réactif d’exécution
 La vue Arborescence des appels peut être développée pour mettre en surbrillance le chemin d’exécution du processus ou de la fonction qui a créé les plus grands objets ou le plus d’objets en mémoire. Pour afficher le chemin le plus actif, cliquez avec le bouton droit sur le processus ou la fonction, puis cliquez sur **Développer le chemin réactif**.

## <a name="set-the-call-tree-root-node"></a>Définir le nœud racine de l’arborescence des appels
 Chaque processus de l’exécution du profilage s’affiche sous forme de nœud racine. Pour définir le nœud de départ de la vue Arborescence des appels sur un autre nœud, cliquez sur le nœud que vous voulez définir comme nœud de départ, puis sélectionnez **Définir la racine**.

 En définissant le nœud racine, vous supprimez toutes les autres entrées de l'affichage, à l'exception de la sous-arborescence du nœud sélectionné. Vous pouvez réinitialiser le nœud racine au nœud examiné à l’origine : cliquez avec le bouton droit dans la fenêtre Vue Arborescence des appels, puis sélectionnez **Réinitialiser la racine**.

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
|**Niveau**|Profondeur de la fonction dans l’arborescence des appels.|
|**Allocations inclusives**|Nombre d’objets alloués par les instances de cette fonction qui ont été appelées par la fonction parente dans l’arborescence des appels. Ce nombre comprend les allocations effectuées par des fonctions enfants.|
|**% d’allocations inclusives**|Pourcentage de tous les objets créés lors de l’exécution du profilage qui étaient des allocations inclusives de cette fonction.|
|**Allocations exclusives**|Nombre d’objets alloués par les instances de cette fonction qui ont été appelées par la fonction parente dans l’arborescence des appels. Ce nombre ne comprend pas les allocations effectuées par les fonctions enfants.|
|**% d’allocations exclusives**|Pourcentage de tous les objets créés au cours de l’exécution du profilage qui étaient des allocations exclusives des instances de cette fonction appelées par la fonction parente dans l’arborescence des appels.|
|**Octets inclusifs**|Nombre d’octets en mémoire alloués par les instances de cette fonction qui ont été appelées par la fonction parente dans l’arborescence des appels. Ce nombre comprend les allocations effectuées par des fonctions enfants.|
|**% d’octets inclusifs**|Pourcentage de tous les octets de mémoire alloués lors de l’exécution du profilage qui étaient des allocations inclusives de cette fonction.|
|**Octets exclusifs**|Nombre d’octets en mémoire alloués par les instances de cette fonction qui ont été appelées par la fonction parente dans l’arborescence des appels. Ce nombre ne comprend pas les allocations effectuées par les fonctions enfants.|
|**% d’octets exclusifs**|Pourcentage de tous les octets de mémoire alloués lors de l’exécution du profilage qui étaient des allocations exclusives de cette fonction.|

## <a name="see-also"></a>Voir aussi
- [Vue de l’arborescence des appels - Instrumentation](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)
- [Vue arborescence des appels](../profiling/call-tree-view-sampling-data.md)
- [Vue arborescence des appels](../profiling/call-tree-view-instrumentation-data.md)
