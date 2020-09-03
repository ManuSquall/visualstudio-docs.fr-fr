---
title: Analyser l’utilisation de la mémoire pour les objets .NET | Microsoft Docs
ms.date: 12/9/2019
ms.topic: how-to
helpviewer_keywords:
- memory allocation, memory usage
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 81c15753b083256b97c9f67219b64565a8db8736
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88247799"
---
# <a name="analyze-memory-usage-by-using-the-net-object-allocation-tool"></a>Analyser l’utilisation de la mémoire à l’aide de l’outil d’allocation d’objets .NET

Vous pouvez voir la quantité de mémoire utilisée par votre application et les chemins de code qui allouent le plus de mémoire à l’aide de l’outil d’allocation d’objets .NET.

Après avoir exécuté l’outil, vous pouvez voir les chemins d’exécution des fonctions où les objets sont alloués. Vous pouvez ensuite effectuer le suivi jusqu’à la racine de l’arborescence des appels qui occupe la plus grande partie de la mémoire.

## <a name="setup"></a>Installation

1. Appuyez sur **ALT + F2** pour ouvrir le profileur de performances dans Visual Studio.

1. Activez la case à cocher **suivi d’allocation d’objets .net** .

   ![L’outil de suivi d’allocation d’objets dotnet sélectionné](../profiling/media/dotnetalloctoolselected.png "L’outil de suivi d’allocation d’objets dotnet sélectionné")

1. Sélectionnez le bouton **Démarrer** pour exécuter l’outil.

1. Une fois l’exécution de l’outil terminée, parcourez le scénario que vous souhaitez profiler dans votre application. Sélectionnez ensuite **arrêter la collecte** ou fermez votre application pour afficher vos données.

   ![Fenêtre d’arrêt de la collecte](../profiling/media/stopcollectionlighttheme.png "Fenêtre d’arrêt de la collecte")

1. Sélectionnez l’onglet **allocation** . Le contenu de la fenêtre ressemble à la capture d’écran suivante.

   ![Onglet allocation](../profiling/media/allocationview.png "Onglet allocation")

Vous pouvez maintenant analyser l’allocation de mémoire des objets.

Pendant la collecte, l’outil de suivi peut ralentir l’application profilée. Si les performances de l’outil de suivi ou de l’application sont lentes et si vous n’avez pas besoin d’effectuer le suivi de chaque objet, vous pouvez ajuster le taux d’échantillonnage. Pour ce faire, sélectionnez le symbole d’engrenage en regard de l’outil de suivi dans la page Résumé du profileur.

![Paramètres de l’outil d’allocation dotnet](../profiling/media/dotnetallocsettings.png "Paramètres de l’outil d’allocation dotnet")

Ajustez le taux d’échantillonnage au taux de votre choix. Cette modification permet d’accélérer les performances de votre application pendant la collecte et l’analyse.

![Taux d’échantillonnage ajusté](../profiling/media/adjustedsamplingratedotnetalloctool.png "Taux d’échantillonnage ajusté")

Pour plus d’informations sur la façon de rendre l’outil plus efficace, consultez [optimisation des paramètres du profileur](../profiling/optimize-profiler-settings.md).

## <a name="understand-your-data"></a>Comprendre vos données

![Graphique pour l’outil d’allocation dotnet](../profiling/media/graphdotnetalloc.png "Graphique pour l’outil d’allocation dotnet")

Dans la vue graphique précédente, le graphique du haut affiche le nombre d’objets actifs dans votre application. Le graphique **Delta d’objet** inférieur affiche le pourcentage de modification des objets d’application. Les barres rouges indiquent quand garbage collection a eu lieu.

![Graphique filtré de la durée d’allocation dotnet](../profiling/media/graphdotnetalloctimefiltered.png "Graphique filtré de la durée d’allocation dotnet")

Vous pouvez filtrer les données tabulaires pour afficher l’activité uniquement pour une plage de temps spécifiée. Vous pouvez également effectuer un zoom avant ou arrière sur le graphique.

### <a name="allocation"></a>Allocation

![Affichage de l’allocation développé](../profiling/media/allocationexpandedlight.png "Affichage de l’allocation développé")

La vue **allocation** affiche l’emplacement des objets qui allouent de la mémoire et la quantité de mémoire allouée par ces objets.

- La **Type**   colonne de type est une liste de classes et de structures qui occupent de la mémoire. Double-cliquez sur un type pour afficher son suivi en tant qu’arborescence des appels inversée. Dans l’affichage **allocation** uniquement, vous pouvez voir les éléments de la catégorie sélectionnée qui occupent de la mémoire.

- La colonne **allocations**   affiche le nombre d’objets qui occupent de la mémoire dans une fonction ou un type d’allocation particulier. Cette colonne s’affiche uniquement dans les vues **allocation**, **arborescence des appels**et **fonctions**   .

- Les colonnes **octets**   et **taille moyenne (octets)**   n’apparaissent pas par défaut. Pour les afficher, cliquez avec le bouton droit sur la colonne **type**   ou **allocations**   , puis sélectionnez les options **octets**   et **taille moyenne (octets)**   pour les ajouter au graphique. 

   Les deux colonnes sont similaires au **total (allocations)** et **auto (allocations)**, sauf qu’elles indiquent la quantité de mémoire occupée au lieu du nombre d’objets qui occupent de la mémoire. Ces colonnes s’affichent uniquement dans la vue **allocation** .

- La colonne **nom du module**   affiche le module qui contient la fonction ou le processus appelant.

Toutes ces colonnes peuvent être triées. Pour les colonnes de **type** et de **nom de module** , vous pouvez trier les éléments par ordre alphabétique dans l’ordre croissant ou décroissant. Pour les **allocations**, les **octets**   et la **taille moyenne (octets)**, vous pouvez trier les éléments en accroissant ou en diminuant la valeur numérique.

#### <a name="symbols"></a>symboles

Les symboles suivants apparaissent dans les onglets **allocation**, **arborescence des appels**et **fonctions** :

- ![Le type valeur Symbol](../profiling/media/valuetypeicon.png "Symbole du type de valeur") -un type valeur comme Integer

- ![Symbole de collection de type valeur](../profiling/media/valuetypecollectionicon.png "Symbole de collection de type valeur") : une collection de type valeur comme un tableau d’entiers

- ![Symbole du type référence](../profiling/media/referencetypeicon.png "Symbole du type de référence") : un type référence comme String

- ![Symbole de collection de type référence](../profiling/media/referencetypecollectionicon.png "Symbole de collection de type référence") -une collection de type référence comme un tableau de chaînes

### <a name="call-tree"></a>Arborescence des appels

![La vue arborescence des appels](../profiling/media/calltreelight.png "La vue arborescence des appels")

La vue **arborescence des appels**   affiche les chemins d’exécution des fonctions qui contiennent des objets qui allouent de la mémoire.

- La colonne nom de la **fonction**   affiche le processus ou le nom de la fonction contenant des objets qui allouent de la mémoire. L’affichage est basé sur le niveau du nœud que vous Inspectez.
- Les colonnes **total (allocations)** et **taille totale (octets)**   affichent le nombre d’objets alloués et la quantité de mémoire utilisée par une fonction et toutes les autres fonctions qu’elle appelle.
- Les colonnes **auto (allocations)** et **auto-size (octets)** affichent le nombre d’objets alloués et la quantité de mémoire utilisée par une fonction ou un type d’allocation sélectionnés.
- La colonne **taille moyenne (octets)** affiche les mêmes informations que dans la vue **allocations** .
- La colonne **nom du module**   affiche le module qui contient la fonction ou le processus appelant.

   ![Un chemin réactif développé](../profiling/media/hotpathlight.png "Un chemin réactif développé")

- Le bouton **développer le chemin réactif** met en surbrillance une voie d’exécution de fonction qui contient de nombreux objets qui allouent de la mémoire. L’algorithme démarre sur un nœud que vous sélectionnez et met en surbrillance le chemin d’accès de la plupart des allocations, ce qui vous guide dans votre investigation.
- Le bouton **afficher le chemin réactif** affiche ou masque les symboles de flamme qui indiquent les nœuds faisant partie du chemin réactif.

### <a name="functions"></a>Fonctions

![Vue fonctions](../profiling/media/functionslight.png "Vue fonctions")

La vue **fonctions** affiche les processus, les modules et les fonctions qui allouent de la mémoire.

- La colonne **nom** affiche les processus en tant que nœuds de niveau supérieur. Sous, les processus sont des modules et les modules sous sont des fonctions.
- Ces colonnes affichent les mêmes informations que dans les vues **allocation** et **arborescence des appels** :

  - **Total (allocations)**
  - **Soi-même (allocations)**
  - **Taille totale (octets)**
  - **Taille automatique (octets)**
  - **Taille moyenne (octets)**

### <a name="collection"></a>Collection

![Vue de collection](../profiling/media/collectionlight.png "Vue de collection")

La vue **collection** indique le nombre d’objets qui ont été collectés ou conservés pendant la garbage collection. Cette vue affiche également les graphiques en secteurs pour visualiser les objets collectés et survivants par type.

- La colonne **collecté** affiche le nombre d’objets collectés par le garbage collector.
- La colonne **survécu** affiche le nombre d’objets qui ont survécu après l’exécution du garbage collector.

### <a name="filtering-tools"></a>Outils de filtrage

Les vues **allocations**, **arborescence des appels**et **fonctions** contiennent toutes les options afficher les **uniquement mon code** et **afficher le code natif** et filtre.

- **Affichez uniquement mon code** réduit les systèmes, les infrastructures et tout autre code utilisateur dans des frames **[code externe]** afin que vous puissiez vous concentrer uniquement sur votre code. Pour plus d’informations, consultez [déboguer le code utilisateur avec uniquement mon code](../debugger/just-my-code.md).
- **Afficher le code natif** affiche le code natif dans la cible d’analyse et peut inclure du code qui n’est pas un utilisateur.
- Avec la zone de filtre, vous pouvez filtrer la colonne **nom** ou **nom de fonction** en fonction de la valeur que vous fournissez. Entrez une valeur de chaîne dans la zone. La table affiche alors uniquement les types qui contiennent cette chaîne.
