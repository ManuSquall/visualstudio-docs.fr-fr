---
title: Vue d’ensemble des sessions de performances | Microsoft Docs
description: Découvrez comment utiliser les outils d’amélioration des performances pour gagner en productivité rapidement et augmenter les performances du code de configuration.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, performance session
- performance sessions
ms.assetid: 35752f95-a57a-4def-b64d-cf4899669e99
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1fcccf6a68afa26d8fe9ab5e5a4f40466822c689
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98723268"
---
# <a name="performance-session-overview"></a>Vue d’ensemble de la session de performance
Cette vue d’ensemble explique les principes de base du profilage. Les développeurs qui débutent dans le domaine des tâches liées aux performances vont découvrir comment les outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] peuvent leur permettre de devenir rapidement productifs et d’optimiser les performances de leur code. Quant aux développeurs expérimentés dans le profilage, ils peuvent obtenir une vue d’ensemble des fonctionnalités et des processus spécifiques des outils de profilage.

 Les outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] permettent d’identifier les problèmes de performance dans le code source et de comparer les performances des solutions potentielles. Les Assistants et les paramètres par défaut des outils de profilage peuvent vous fournir instantanément des renseignements sur de nombreux problèmes de performance. Les fonctionnalités et les options des outils de profilage contrôlent avec précision le processus de profilage. Elles permettent notamment de cibler des sections de code précises, de collecter des informations de durée de niveau bloc et d’inclure des données supplémentaires sur les performances du processeur et du système dans vos données.

 Les étapes suivantes constituent le processus de base de l’utilisation des outils de profilage :

1. Configurer la session de performance en spécifiant la méthode de collecte et les données à collecter.

2. Collecter les données de profilage en exécutant l’application dans la session de performance.

3. Analyser les données afin d’identifier le problème de performance.

4. Modifier le code dans l’environnement de développement intégré (IDE) de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] afin d’améliorer les performances d’application du code.

5. Collecter des données de profilage sur le code modifié et les comparer à celles des données d’origine.

6. Générer un rapport qui documente l’augmentation des performances.

   Pour utiliser les informations fournies par le profilage, vous devez disposer d’informations de symboles pour les fichiers binaires à profiler et pour les fichiers binaires du système d’exploitation Windows.

## <a name="configure-the-performance-session"></a>Configurer la session de performance
 Pour configurer une session de profilage, sélectionnez la méthode de profilage à utiliser et les données à collecter. L’**Assistant Performance** des outils de profilage peut vous guider tout au long de la configuration de base. Vous pouvez aussi ajouter des options à l’aide des pages de propriétés de la session de performance :

- Les méthodes de profilage incluent l’échantillonnage, le suivi et l’allocation de mémoire.

- Les valeurs de données incluent les compteurs de performance de temps, de processeur et de système d’exploitation, ainsi que des événements d’application tels que les erreurs de page et les transitions de noyau.

  Vous pouvez configurer une session de performance dans un projet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] au sein de la même solution ou profiler des fichiers binaires arbitrairement via l’IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Vous pouvez spécifier les propriétés de la session dans les pages de propriétés de la session de performance ou utiliser l’Assistant Profilage.

## <a name="collect-profiling-data"></a>Collecter les données de profilage
 Vous démarrez la collecte des données de profilage à partir de l’**Explorateur de performances**. Vous pouvez suspendre et reprendre le profilage afin de limiter le volume des données collectées. Vous pouvez également effectuer un attachement à un processus qui est déjà en cours d’exécution.

 Dès que l’application démarre, la fenêtre **Contrôle de collecte de données** s’affiche dans l’IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. **Cette fenêtre** permet de profiler des parties spécifiques de votre application en suspendant et en reprenant le processus de collecte. Grâce à la fenêtre **Contrôle de collecte de données**, vous pouvez également insérer des marques dans les données collectées. Les marques sont des points de données définis par l’utilisateur qui s’affichent dans les vues de profil et qui permettent de filtrer les données de profilage.

 Quand l’application cible s’arrête, les outils de profilage génèrent un fichier de données de profilage (*.vsp) et affichent la vue de rapport Résumé dans l’IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="analyze-the-data-and-identify-performance-issues"></a>Analyser les données et identifier les problèmes de performances
 Quand vous terminez une exécution de profilage, les données sont analysées et un résumé s’affiche dans les fenêtres des vues **Rapport de performances** des outils de profilage. Les données de profilage sont collectées pour la pile des appels et pour les fonctions individuelles de l’application cible. Les vues de rapport affichent l’analyse des performances pour des plages de données des processus, threads, modules, fonctions et lignes de code source de l’application. Les valeurs des données de profilage pour une fonction incluent les éléments suivants :

- Le temps total lié à la fonction et aux fonctions enfants appelées par la fonction (valeurs inclusives).

- Le temps passé à exécuter uniquement le code dans la fonction (valeurs exclusives).

  Vous pouvez analyser les données de profilage de manière optimale grâce à plus de douze vues différentes. Vous pouvez personnaliser les vues pour filtrer et trier les données afin de déterminer les fonctions qui risquent de provoquer des problèmes de performance. Le filtrage par chemin réactif met immédiatement en surbrillance les chemins les plus actifs dans les vues Arborescence des appels et Modules.

## <a name="modify-the-application-code"></a>Modifier le code de l’application
 Après avoir isolé un ou plusieurs problèmes de performance pertinents, vous pouvez modifier le code à l’aide de l’IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], puis collecter les données de profilage relatives aux modifications apportées.

## <a name="collect-profiling-data-again-and-compare-the-data-between-the-profiling-runs"></a>Collecter à nouveau les données de profilage et les comparer entre les exécutions de profilage
 La vue Rapport de comparaison des outils de profilage affiche les différences au niveau des performances des modules, des fonctions ou des lignes entre deux fichiers de données de profilage sélectionnés. Vous pouvez spécifier les valeurs de données de profilage à comparer et passer de la vue de comparaison aux vues des fichiers individuels.

## <a name="generate-a-report-of-the-results"></a>Générer un rapport des résultats
 Vous pouvez coller des lignes de vues de rapport de performances dans des e-mails et des feuilles de calcul. Il est également possible de générer des rapports qui contiennent les données d’une ou de plusieurs vues.

## <a name="see-also"></a>Voir aussi
- [Vues d'ensemble](../profiling/overviews-performance-tools.md)
- [Procédure pas à pas : identifier les problèmes de performances](beginners-guide-to-cpu-sampling.md)
