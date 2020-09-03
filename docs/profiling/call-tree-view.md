---
title: Vue Arborescence des appels | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.calltree
helpviewer_keywords:
- Call Tree view
- profiling tools reports, Call Tree view
- performance reports, Call Tree view
- profiling tools, Call Tree view
ms.assetid: b2dbc033-bf95-4d10-8e51-f9462979133e
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0b932d5f9e4a178c94f3e490c66cec64648ce4f6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74773333"
---
# <a name="call-tree-view"></a>Mode Arborescence des appels
La vue Arborescence des appels affiche les chemins d’exécution de la fonction empruntés dans l’application profilée. La racine de l’arborescence correspond au point d’entrée de l’application ou du composant. Chaque nœud de fonction liste toutes les fonctions appelées par la fonction et les données de performances liées à ces appels de fonction.

 La vue Arborescence des appels peut également être développée et mettre en surbrillance le chemin d’exécution d’une fonction qui a exigé le plus de temps ou qui a fait l’objet du plus grand nombre d’échantillonnages. Pour faire apparaître le chemin le plus coûteux en matière de performances, cliquez avec le bouton droit sur la fonction, puis cliquez sur **Développer le chemin réactif**.

 Chaque processus de l’exécution du profilage s’affiche sous forme de nœud racine. Vous pouvez définir le nœud de départ de la vue Arborescence des appels en cliquant avec le bouton droit sur ce nœud, puis en sélectionnant **Définir la racine**.

 En définissant le nœud racine, vous supprimez toutes les autres entrées de l'affichage, à l'exception de la sous-arborescence du nœud sélectionné. Vous pouvez réinitialiser le nœud racine au nœud examiné à l’origine. Dans la fenêtre de la vue Arborescence des appels, cliquez avec le bouton droit, puis sélectionnez **Réinitialiser la racine**.

 La vue Arborescence des appels peut être personnalisée en ajoutant ou en supprimant des colonnes. Cliquez avec le bouton droit sur la **barre de titre des noms de colonne**, puis sélectionnez **Ajouter/Supprimer des colonnes**.

 Vous pouvez configurer une réduction du bruit pour la vue Arborescence des appels en limitant la quantité des données qui sont présentées. La réduction du bruit vous permet de repérer plus facilement les problèmes de performances dans la vue. Quand les problèmes de performances sont faciles à distinguer, l’analyse est plus facile. Pour plus d’informations, consultez [Guide pratique pour configurer la réduction du bruit dans les vues Rapports](../profiling/how-to-configure-noise-reduction-in-report-views.md).

> [!NOTE]
> Si la réduction du bruit est configurée pour afficher un avertissement quand elle est activée, une barre d’informations s’affiche dans le rapport.

 Pour plus d’informations sur les définitions des colonnes dans la vue Arborescence des appels, consultez les rubriques suivantes :

- [Vue arborescence des appels](../profiling/call-tree-view-sampling-data.md)

- [Vue arborescence des appels](../profiling/call-tree-view-instrumentation-data.md)

- [Vue arborescence des appels-échantillonnage](../profiling/call-tree-view-dotnet-memory-sampling-data.md)

- [Vue arborescence des appels](../profiling/call-tree-view-contention-data.md)

## <a name="see-also"></a>Voir aussi
- [Vues des rapports de performances](../profiling/performance-report-views.md)
- [Présentation des valeurs de données d’instrumentation](../profiling/understanding-instrumentation-data-values.md)
- [Présentation des valeurs de données d’échantillonnage](../profiling/understanding-sampling-data-values.md)
