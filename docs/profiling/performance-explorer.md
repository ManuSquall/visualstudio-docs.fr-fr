---
title: Explorateur de performances | Microsoft Docs
ms.date: 06/19/2017
ms.topic: conceptual
f1_keywords:
- vs.performance
- vs.performance.wizard.website
helpviewer_keywords:
- performance tools [Visual Studio ALM]
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0a248821639a2263f5695d64030d932b2b6a05fe
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53933912"
---
# <a name="performance-explorer"></a>Explorateur de performances

Grâce aux outils de profilage de Visual Studio, les développeurs peuvent mesurer, évaluer et cibler les problèmes de performances de leur code. Ces outils sont totalement intégrés à l'environnement de développement intégré (IDE) pour fournir une expérience utilisateur conviviale et accessible.

Le profilage d'une application est simple. Vous commencez par créer une session de performance. Dans l'édition Visual Studio Team System Development, vous pouvez utiliser l'Assistant Création d'une nouvelle session de performance pour créer une session de performance. À la fin de la session de performance, les données rassemblées lors du profilage sont enregistrées dans un fichier .*vsp*. Vous pouvez visualiser le fichier .*vsp* dans l’IDE. Plusieurs vues de rapport sont disponibles pour vous aider à visualiser et à détecter les problèmes de performances provenant des données collectées.

Les outils de profilage peuvent également être utilisés à partir de la ligne de commande. Cela offre aux utilisateurs la souplesse nécessaire pour exécuter ces outils à partir de la ligne de commande ou pour les utiliser pour automatiser les tâches qui utilisent des scripts.

Pour plus d'informations sur les rubriques actuelles et avancées relatives aux performances et au profilage, effectuez une recherche sur MSDN (Microsoft Developer Network) et dans les blogs Microsoft. Utilisez les mots clés Enterprise, Performance, Outils, Team.

## <a name="common-tasks"></a>Tâches courantes

|Tâche|Contenu associé|
|----------|---------------------|
|**Techniques pour Windows 8 et ultérieur**|[Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)|
|**Comprendre les concepts de profilage :** découvrez les concepts et les termes que vous allez utiliser lors de la collecte, de l’affichage et de l’analyse des performances de code à l’aide des outils de profilage.|[Vues d’ensemble](../profiling/overviews-performance-tools.md)|
|**Se lancer et le faire :** découvrez les procédures de base que vous allez utiliser lors de la collecte, de l’affichage et de l’analyse des performances de code à l’aide des outils de profilage. Essayez par vous-même en suivant une procédure pas à pas.|[Prise en main](../profiling/getting-started-with-performance-tools.md)|
|**Configurer une session de profilage :** découvrez des méthodes avancées permettant de spécifier les projets ou les fichiers binaires à profiler, de sélectionner une méthode de profilage, de choisir les données de performance à collecter, et de définir d’autres options de la session de profilage.|[Configurer des sessions de performances](../profiling/configuring-performance-sessions.md)|
|**Contrôler les données collectées par le profileur :** découvrez comment utiliser les propriétés d’une session de performance et les procédures interactives permettant de démarrer et d’arrêter le profilage, ainsi qu’à limiter les données de performance collectées aux informations souhaitées.|[Contrôler la collecte des données](../profiling/controlling-data-collection.md)|
|**Identifier les problèmes de performances :** découvrez comment afficher et analyser les données de performances collectées dans la fenêtre d’affichage Rapport des outils de profilage.|[Analyser les données des outils d’analyse des performances](../profiling/analyzing-performance-tools-data.md)|
|**Analyser les modifications de performance :** découvrez comment comparer deux fichiers de données du profileur pour analyser l’évolution des performances.|[Comparer des fichiers de données de performances](../profiling/comparing-performance-data-files.md)|
|**Enregistrer et partager vos résultats :** découvrez comment enregistrer les données de profilage pour l’archivage ou le partage.|[Enregistrer et exporter les données des outils d’analyse des performances](../profiling/saving-and-exporting-performance-tools-data.md)|
|**Automatiser le profilage :** découvrez comment utiliser les outils de profilage à partir de l’invite de commandes.|[Profiler à partir de la ligne de commande](../profiling/using-the-profiling-tools-from-the-command-line.md)|
|**Contrôler le profilage par programmation :** découvrez comment utiliser les API managées et natives des outils de profilage pour contrôler la collecte de données directement à partir du code source.|[API des outils de profilage](../profiling/profiling-tools-apis.md)|
|**Résoudre les problèmes de profilage**|[Résoudre les problèmes liés aux outils d’analyse des performances](../profiling/troubleshooting-performance-tools-issues.md)|

## <a name="see-also"></a>Voir aussi

[Découvrir les outils de profilage](../profiling/profiling-feature-tour.md)