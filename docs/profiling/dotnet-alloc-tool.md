---
title: Analyser l’utilisation de la mémoire pour les objets .NET | Microsoft Docs
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
ms.sourcegitcommit: aa302af53de342e75793bd05b10325939dc69b53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75898468"
---
# <a name="analyze-memory-usage-using-the-net-object-allocation-tool"></a>Analyser l’utilisation de la mémoire à l’aide de l’outil d’allocation d’objets .NET

Vous pouvez voir la quantité de mémoire utilisée par votre application et les chemins de code qui allouent le plus de mémoire à l’aide de l’outil d’allocation d’objets .NET.

Après avoir exécuté l’outil, vous pouvez voir les chemins d’exécution des fonctions où les objets sont alloués afin que vous puissiez remonter jusqu’à la racine de l’arborescence des appels qui occupe la plus grande quantité de mémoire.

## <a name="setup"></a>Programme d'installation

1. Ouvrez le profileur de performances (**ALT + F2)** dans Visual Studio.
2.  Cochez la case suivi de l' **allocation d’objets .net** .

![Hub diag](../profiling/media/diaghub.png "Hub diag")

> [!NOTE]
> Le projet de démarrage est sélectionné comme **cible d’analyse** par défaut, mais vous pouvez le remplacer par le processus en cours d’exécution, les exécutables, les applications en cours d’exécution et les applications installées en ouvrant le menu déroulant **modifier la cible** , puis en sélectionnant parmi les options disponibles.

   L’outil d’allocation d’objets .NET ne prend pas actuellement en charge les exécutables via le menu déroulant. Vous devez passer par le système de projet exe pour utiliser l’outil. Pour ce faire, fermez votre solution actuelle (**fichier** -> **Fermer la solution**), puis appuyez sur **fichier** -> **ouvrir un projet ou une solution** -> sélectionnez votre fichier. exe.

![Cible de l’analyse](../profiling/media/analysistarget.png "Cible de l'analyse")

3. Cliquez sur le bouton **Démarrer** pour exécuter l’outil.

![Arrêter la collecte](../profiling/media/stopcollection.png "Arrêter la collection")

4. Une fois l’exécution de l’outil terminée, suivez le scénario souhaité dans votre application, puis appuyez sur **arrêter la collecte** ou fermez votre application pour afficher vos données.
5. Cliquez sur l’onglet **allocation** . vous devriez voir une image semblable à celle illustrée ci-dessous.

![Allocation](../profiling/media/allocation.png "Allocation")

Félicitations ! Vous pouvez maintenant analyser l’allocation de mémoire des objets.

## <a name="understand-your-data"></a>Comprendre vos données

### <a name="collection"></a>Collection

![Regroupement](../profiling/media/collection.png "Collection")

La vue de collection vous permet de connaître le nombre d’objets collectés pendant la garbage collection et le nombre de retenues. Cette vue fournit également quelques graphiques en secteurs pour visualiser les objets collectés et survivants par type.

- La colonne **collecté** affiche le nombre d’objets collectés par le garbage collector.
- La colonne **survécu** affiche le nombre d’objets qui ont survécu après l’exécution du garbage collector.

### <a name="allocation"></a>Allocation

![Étendue allouée](../profiling/media/allocationexpanded.png "Étendue allouée")

La vue allocation vous permet de voir l’emplacement des objets qui allouent de la mémoire et la quantité de mémoire allouée par ces objets.

- La colonne **Name** est une liste de diverses classes et structures qui occupent de la mémoire. Chaque élément de la colonne est un nœud qui peut être développé si des éléments de cette catégorie occupent de la mémoire. (Affichage**allocation** uniquement)
- La colonne **total (allocations)** indique le nombre d’objets dans un type d’allocation particulier qui occupent de la mémoire. (Vue**allocation**, **arborescence des appels**et **fonctions** )
- La colonne **Self (allocations)** affiche le nombre d’objets dans un élément individuel qui occupe de la mémoire. (Vue**allocation**, **arborescence des appels**et **fonctions** )
- Ces trois colonnes peuvent être triées. Dans le cas de la colonne **Name** , les éléments sont triés par ordre alphabétique (vers l’avant ou vers l’arrière). Pour les **opérations totales** et **automatiques (allocations)** , vous pouvez effectuer un tri numérique (de plus en plus ou moins complexe).
- Les colonnes **taille totale (octets)** et **taille automatique (octets)** ne sont pas activées par défaut. Pour les activer, cliquez avec le bouton droit sur les colonnes **nom**, **total** ou **auto (allocations)** , puis cliquez sur options **taille totale** et **taille automatique** pour les ajouter au graphique. Les deux colonnes sont similaires au **total (allocations)** et **auto (allocations)** , sauf qu’au lieu d’afficher le nombre d’objets qui occupent de la mémoire, ils affichent la quantité totale de mémoire en octets qu’occupent ces objets. [Allocation View Only]

### <a name="call-tree"></a>Arborescence des appels

![Arborescence des appels](../profiling/media/calltree.png "Arborescence des appels")

La vue **arborescence des appels** vous permet de voir les chemins d’exécution des fonctions qui contiennent des objets qui allouent beaucoup de mémoire.

- La colonne nom de la **fonction** affiche le processus ou le nom de la fonction contenant des objets qui allouent de la mémoire en fonction du niveau du nœud que vous Inspectez.
- Les colonnes **total** et **Self (allocations)** affichent les mêmes informations que la vue **allocation** .
- La colonne **nom du module** affiche le module qui contient la fonction ou le processus appelant.

![Chemin réactif](../profiling/media/hotpath.png "Chemin réactif")

- Le bouton **développer le chemin réactif** met en surbrillance une voie d’exécution de fonction qui contient un grand nombre d’objets qui allouent de la mémoire. L’algorithme commence à un nœud sélectionné par l’utilisateur et met en surbrillance le chemin d’accès de la plupart des allocations, en guidant un utilisateur dans son investigation.
- Le bouton **afficher le chemin réactif** active ou désactive les icônes de flamme qui indiquent quel nœud fait partie du **chemin réactif**.

### <a name="functions"></a>Fonctions

![Fonctions](../profiling/media/functions.png "Fonctions")

La vue **fonctions** affiche les processus, les modules et les fonctions qui allouent de la mémoire.

- La colonne **nom** affiche les processus en tant que nœuds de niveau supérieur. Sous, les processus sont des modules et les modules sont des fonctions.
- Les colonnes **total** et **Self (allocations)** affichent les mêmes informations que la vue **allocation** .

Les vues **allocations**, **arborescence des appels**et **fonctions** contiennent toutes les options **afficher le uniquement mon code**, afficher le **code natif**et **Rechercher** :

![Barre de filtre](../profiling/media/filterbar.png "Barre de filtre")

- **Affiche uniquement mon code** réduit les systèmes, les infrastructures et d’autres codes non-utilisateur et dans des frames **[code externe]** afin que le code utilisateur puisse se concentrer sur. Pour plus d’informations, consultez [déboguer le code utilisateur avec uniquement mon code](../debugger/just-my-code.md).
- **Afficher le code natif** affiche le code natif dans la cible d’analyse, y compris le code non-utilisateur, s’il est sélectionné.
- La **zone de filtre** vous permet de filtrer la colonne **nom** ou **nom de fonction** en fonction du paramètre que vous fournissez. Tapez simplement dans le champ et la table doit filtrer pour afficher uniquement les types qui contiennent la chaîne fournie.
