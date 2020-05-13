---
title: Analyser l’utilisation de la mémoire pour les objets .NET Microsoft Docs
ms.date: 12/9/2019
ms.topic: conceptual
helpviewer_keywords:
- memory allocation, memory usage
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 9518ffd618a6d82505feca33b37b5151a3a9f961
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75898468"
---
# <a name="analyze-memory-usage-using-the-net-object-allocation-tool"></a>Analyser l’utilisation de la mémoire à l’aide de l’outil .NET Object Allocation

Vous pouvez voir combien de mémoire votre application utilise et quels chemins de code allouent le plus de mémoire à l’aide de l’outil .NET Object Allocation.

Après avoir exécuté l’outil, vous pouvez voir les chemins d’exécution de fonction où les objets sont attribués de sorte que vous puissiez remonter à la racine de l’arbre d’appel qui prend la plus grande quantité de mémoire.

## <a name="setup"></a>Programme d’installation

1. Ouvrez le Profileer performance **(Alt et F2)** en Studio Visuel.
2.  Sélectionnez la case de **suivi de suivi de l’allocation d’objets .NET.**

![Diag Hub](../profiling/media/diaghub.png "Diag Hub")

> [!NOTE]
> Le projet de démarrage est sélectionné comme **cible d’analyse** par défaut, mais cela peut être modifié pour le processus d’exécution, les exécutables, les applications en cours d’exécution et les applications installées en ouvrant le menu de dropdown **Change Target,** puis en sélectionnant parmi les options disponibles.

   L’outil .NET Object Allocation ne prend actuellement pas en charge les exécutions via le menu dropdown. Vous devrez passer par le système de projet exe pour utiliser l’outil. Pour ce faire, fermez votre solution actuelle (**File** -> **Close Solution**) et frappez ensuite **File** -> Open un projet ou une**solution** -> sélectionnez votre fichier .exe.

![Cible de l'analyse](../profiling/media/analysistarget.png "Cible de l'analyse")

3. Cliquez sur le bouton **Démarrer** pour exécuter l’outil.

![Stop Collection](../profiling/media/stopcollection.png "Arrêter la collection")

4. Une fois que l’outil commence à fonctionner, passez par le scénario souhaité dans votre application, puis appuyez **sur Stop Collection** ou fermez votre application pour voir vos données.
5. Cliquez sur **l’onglet Allocation** et vous devriez voir une image similaire à celle indiquée ci-dessous.

![Allocation](../profiling/media/allocation.png "Allocation")

Félicitations ! Vous pouvez maintenant analyser l’allocation de mémoire des objets.

## <a name="understand-your-data"></a>Comprendre vos données

### <a name="collection"></a>Collection

![Collection](../profiling/media/collection.png "Collection")

La vue de collecte vous permet de voir combien d’objets ont été collectés lors de la collecte des ordures et combien ont été conservés. Cette vue fournit également quelques graphiques à secteurs pour visualiser les objets collectés et survécus par type.

- La colonne **Collectée** montre le nombre d’objets recueillis par le éboueur.
- La colonne **Survived** montre le nombre d’objets qui ont survécu après la course du collecteur d’ordures.

### <a name="allocation"></a>Allocation

![Répartition élargie](../profiling/media/allocationexpanded.png "Répartition élargie")

La vue d’allocation vous permet de voir l’emplacement des objets qui allouent de la mémoire et la quantité de mémoire que ces objets attribuent.

- La colonne **Nom** est une liste de différentes classes et structures qui prennent la mémoire. Chaque élément dans la colonne est un nœud qui peut être élargi s’il ya des éléments dans cette catégorie de prendre la mémoire. (**Vue d’allocation** seulement)
- La colonne **Total (Allocations)** affiche le nombre d’objets dans un type d’allocation particulier qui prennent la mémoire. (**Allocation**, **Arbre d’appel**, et Vue des **fonctions)**
- La colonne **Self (Allocations)** affiche le nombre d’objets dans un élément individuel qui prend la mémoire. (**Allocation**, **Arbre d’appel**, et Vue des **fonctions)**
- Ces trois colonnes sont triables. Dans le cas de la colonne **Nom,** les éléments sont triés par ordre alphabétique (vers l’avant ou vers l’arrière). Pour **Total** et **Auto (Allocations),** vous pouvez trier numériquement (de plus en plus ou de façon décroissante).
- Les colonnes **De taille totale (Octets)** et **de taille autonome (Octets)** ne sont pas allumées par défaut. Pour les activer, cliquez à droite sur les colonnes **Nom,** **Total** ou **Auto (Allocations),** puis cliquez sur les options **Taille totale** et **taille autonome** pour les ajouter au graphique. Les deux colonnes sont similaires à **Total (Allocations)** et **Self (Allocations)** sauf qu’au lieu de montrer le nombre d’objets prenant la mémoire, elles montrent la quantité totale de mémoire dans les octets que ces objets prennent. [Vue d’allocation seulement]

### <a name="call-tree"></a>Appelez l’arbre

![Appelez l’arbre](../profiling/media/calltree.png "Appelez l’arbre")

La vue **Call Tree** vous permet de voir les chemins d’exécution de fonction qui contiennent des objets allouant beaucoup de mémoire.

- La colonne **de nom de fonction** indique le processus ou le nom de la fonction contenant des objets allouant la mémoire en fonction du niveau du nœud que vous inspectez.
- Les colonnes **Total** et **Auto (Allocations)** affichent les mêmes informations que la vue **d’allocation.**
- La colonne **de nom du module** affiche le module qui contient la fonction ou le processus qui appelle.

![Chemin chaud](../profiling/media/hotpath.png "Chemin réactif")

- Le bouton **Expand Hot Path** met en évidence une voie d’exécution de fonction qui contient beaucoup d’objets qui allouent la mémoire. L’algorithme commence à un nœud d’intérêt sélectionné par l’utilisateur et met en évidence le chemin de la plupart des allocations, guidant un utilisateur dans leur enquête.
- Le bouton **Show Hot Path** bascule sur ou hors des icônes de flamme qui indiquent quel nœud font partie du Sentier **Chaud.**

### <a name="functions"></a>Fonctions

![Fonctions](../profiling/media/functions.png "Fonctions")

La vue **Fonctions** affiche les processus, les modules et les fonctions qui allouent la mémoire.

- La colonne **Nom** affiche les processus comme les nœuds de niveau le plus élevé. Sous les processus sont des modules, et sous les modules sont des fonctions.
- Les colonnes **Total** et **Auto (Allocations)** affichent les mêmes informations que la vue **d’allocation.**

Les **allocations**, **l’arbre d’appel**, et les vues **de fonctions** contiennent tous le **show Just My Code**, Afficher le code **autochtone**, et les options **de recherche** :

![Barre de filtre](../profiling/media/filterbar.png "Barre de filtre")

- **Afficher Just My Code** effondre les systèmes, les cadres et autres codes non utilisateurs et dans les images **[Code externe]** afin que le code utilisateur puisse être concentré sur. Pour plus d’informations, voir [Code utilisateur Debug avec Just My Code](../debugger/just-my-code.md).
- **Afficher le code autochtone** affiche le code natif dans la cible d’analyse, y compris le code non utilisateur s’il est sélectionné.
- La **boîte de filtre** vous permet de filtrer la colonne **nom** ou nom **de fonction** en fonction du paramètre que vous fournissez. Il suffit de taper dans le champ et la table doit filtrer vers le bas pour afficher uniquement les types qui contiennent la chaîne fournie.
