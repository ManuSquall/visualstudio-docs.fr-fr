---
title: Bien démarrer avec les outils d’analyse des performances | Microsoft Docs
description: Découvrez les différentes façons dont Visual Studio permet de collecter, d’afficher et d’analyser les données de performances du code.
ms.custom: SEO-VS-2020
ms.date: 11/04/2018
ms.topic: conceptual
helpviewer_keywords:
- getting started, performance
- getting started, profiling tools
ms.assetid: 02085214-a8e4-40fd-9b26-32391a7a7082
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4f168c4c88ba12ff1f1c9bd0543e9d2b74ae095c
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801508"
---
# <a name="getting-started-with-performance-tools"></a>Bien démarrer avec les outils d’analyse des performances

Visual Studio propose plusieurs façons de collecter, afficher et analyser les données de performances du code. Dans de nombreux cas, le meilleur moyen de bien démarrer avec les outils de performances consiste à utiliser les paramètres par défaut de l’**Assistant Performance**. L’Assistant collecte des statistiques d’application qui peuvent pointer vers les problèmes de performances de votre code.

- Des avertissements de performances qui vous informent des problèmes de codage courants s’affichent dans la fenêtre **Liste d’erreurs** de Visual Studio. Les avertissements vous permettent d’accéder à votre code source ainsi qu’à des rubriques d’aide détaillées qui vous aideront à écrire du code plus efficace.

- Des rapports de performances offrent des vues des différents niveaux de votre structure d’application, des lignes de code source et des processus. Des rapports de performances affichent les données d’exécution d’application, des fonctions appelantes et appelées d’une fonction spécifique jusqu’à l’arborescence des appels de l’application entière.

Pour profiler rapidement un projet, une application ou un site Web ASP.net, sélectionnez **Déboguer** le  >  **profileur de performances** et sélectionnez **Assistant Performance**. Pour obtenir des instructions détaillées, consultez [Guide du débutant en profilage des performances](../profiling/beginners-guide-to-cpu-sampling.md) et [Guide pratique pour collecter les données de performances d’un site web](../profiling/how-to-collect-performance-data-for-a-web-site.md).

Pour spécifier et configurer manuellement une session de profilage des performances, sélectionnez **Déboguer** le  >  **profileur**  >  **Explorateur de performances**. Utilisez le dossier **Cibles** et les pages de **Propriétés** dans l’**Explorateur de performances** pour configurer des sessions. Pour obtenir des instructions, consultez [Guide pratique pour créer manuellement des sessions de performance](../profiling/how-to-manually-create-performance-sessions.md).

**Voir aussi :**

- [Présentations des outils d’analyse des performances](../profiling/overviews-performance-tools.md)
- [Analyse des données des outils d’analyse des performances](../profiling/analyzing-performance-tools-data.md)
- [Utilisation des règles de performances pour analyser des données](../profiling/using-performance-rules-to-analyze-data.md)
- [Configuration de sessions de performance](../profiling/configuring-performance-sessions.md)
