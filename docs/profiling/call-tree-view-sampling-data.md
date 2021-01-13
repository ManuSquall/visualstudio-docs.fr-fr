---
title: Vue Arborescence des appels - Données d’échantillonnage | Microsoft Docs
description: Lisez comment la vue arborescence des appels affiche les données d’échantillonnage pour les chemins d’exécution des fonctions qui ont été parcourus dans l’application profilée dans Explorateur de performances.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Call Tree view
- Call Tree view
ms.assetid: 5c4e8ec3-d0d3-485a-93bd-9060df4eb739
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1fc7493d20d09ebd606e3a6ec8e5271981fb6f62
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150520"
---
# <a name="call-tree-view---sampling-data"></a>Vue Arborescence des appels - Données d’échantillonnage
La vue Arborescence des appels affiche les chemins d’exécution de la fonction empruntés dans l’application profilée.

> [!NOTE]
> Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications UWP nécessitent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

 La racine de l’arborescence correspond au point d’entrée de l’application ou du composant. Chaque nœud de fonction répertorie toutes les fonctions appelées et les données de performance liées à ces appels de fonction.

 Les valeurs qui s’affichent dans la vue Arborescence des appels sont celles des instances de fonction qui ont été appelées par la fonction parent dans l’arborescence des appels. Les valeurs en pourcentage sont calculées en comparant la valeur des instances de fonctions au nombre total d’échantillons de l’exécution du profilage.

## <a name="highlight-the-execution-hot-path"></a>Mettre en surbrillance le chemin réactif d’exécution
 La vue Arborescence des appels peut être développée pour mettre en surbrillance le chemin d’exécution du processus ou de la fonction ayant fait l’objet du plus grand nombre d’échantillonnages. Pour afficher le chemin le plus actif, cliquez avec le bouton droit sur le processus ou la fonction, puis cliquez sur **développer le chemin réactif**.

## <a name="set-the-call-tree-root-node"></a>Définir le nœud racine de l’arborescence des appels
 Chaque processus de l’exécution du profilage s’affiche sous forme de nœud racine. Pour définir le nœud de départ de la vue Arborescence des appels, cliquez sur le nœud que vous souhaitez définir comme nœud de départ, puis sélectionnez **Définir la racine**.

 En définissant le nœud racine, vous supprimez toutes les autres entrées de l'affichage, à l'exception de la sous-arborescence du nœud sélectionné. Pour réinitialiser le nœud racine vers le nœud d’origine, cliquez avec le bouton droit dans la fenêtre Vue Arborescence des appels, puis sélectionnez **Réinitialiser la racine**.

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
|**Niveau**|Niveau d’imbrication de cette fonction dans l’arborescence des appels. Uniquement dans les rapports en ligne de commande [VSPerfReport](../profiling/vsperfreport.md).|
|**Échantillons exclusifs**|Nombre d’échantillons collectés dans cette fonction quand celle-ci a été appelée par la fonction parent dans l’arborescence des appels. Ce nombre n’inclut pas les échantillons collectés dans les fonctions appelées par cette fonction.|
|**% d’échantillons exclusifs**|Pourcentage de tous les échantillons de l’exécution du profilage qui étaient des échantillons exclusifs de cette fonction lorsque celle-ci a été appelée par la fonction parent dans l’arborescence des appels.|
|**Échantillons inclusifs**|Nombre d’échantillons collectés dans cette fonction quand celle-ci a été appelée par la fonction parent dans l’arborescence des appels. Ce nombre inclut les échantillons collectés dans les fonctions appelées par la fonction.|
|**% des échantillons inclusifs**|Pourcentage de tous les échantillons de l’exécution du profilage qui étaient des échantillons inclusifs de cette fonction lorsque celle-ci a été appelée par la fonction parent dans l’arborescence des appels.|

## <a name="see-also"></a>Voir aussi
- [Comment : personnaliser les colonnes de la vue rapport](../profiling/how-to-customize-report-view-columns.md)
- [Vue de l’arborescence des appels - Données d’échantillonnage du profileur](../profiling/call-Tree-view-sampling-data.md)
- [Vue arborescence des appels-échantillonnage](../profiling/call-tree-view-dotnet-memory-sampling-data.md)
- [Vue de l’arborescence des appels - Instrumentation](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)
- [Vue arborescence des appels](../profiling/call-tree-view-instrumentation-data.md)
