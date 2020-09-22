---
title: Collecter des données d’échantillonnage au niveau de la ligne | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- performance tools, line-level sampling
ms.assetid: 44803aad-dd39-4c2e-9209-d35185d44983
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4653cf4b8c921a0c464dcb148963d3ab33506c25
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851253"
---
# <a name="how-to-collect-line-level-sampling-data"></a>Guide pratique pour collecter des données d’échantillonnage au niveau ligne
L’échantillonnage au niveau ligne permet au profileur de déterminer à quel endroit du code d’une fonction exigeant d’importantes ressources processeur (telle qu’une fonction avec de nombreux échantillons exclusifs) le processeur doit passer le plus de temps.

## <a name="overview"></a>Vue d’ensemble
 Pour l’échantillonnage au niveau ligne, le profileur parcourt la pile d’appels du programme à intervalles définis et regroupe les résultats. Ces résultats montrent quelles instructions étaient exécutées par le processeur lorsque les échantillons ont été prélevés. Les données collectées sur les échantillons exclusifs sont ensuite analysées afin d’identifier les lignes de code et le pointeur d’instruction (IP).

 L’échantillonnage au niveau ligne fonctionne aussi bien pour le code managé que pour le code natif. Les rapports de performances qui affichent ces données sont ceux de la vue Lignes et de la vue Modules.

 Les informations sur les caractères de début et de fin ne sont pas disponibles pour le code natif. Pour les instructions multilignes, les informations de début de ligne ne sont pas disponibles pour le code natif. Seules les informations de fin de ligne sont disponibles.

### <a name="available-data"></a>Données disponibles
 Les données d’échantillonnage au niveau ligne qui sont disponibles comprennent les informations suivantes :

- Le nom de la fonction

- L’adresse de la fonction

- Début de ligne : numéro de ligne du code échantillonné.

- Fin de ligne : numéro de la ligne source de fin. Il s’agit généralement des mêmes données que les données de début de ligne, sauf lorsqu’une instruction de programme s’étend sur plusieurs lignes de code source.

- Début de caractères : colonne de début de l’échantillon agrégé. Cette valeur est généralement égale à 0, sauf lorsqu’une ligne contient plusieurs instructions de programme.

- Fin de caractère : colonne de fin de l’échantillon agrégé.

- IP : adresse à laquelle l’échantillon agrégé a été prélevé (vue IP uniquement).

  Dans la vue **Modules**, si une fonction comporte des statistiques au niveau ligne, celles-ci sont imbriquées sous chaque fonction. Les statistiques de niveau IP qui sont imbriquées sous chaque ligne sont également affichées.

### <a name="turn-off-line-level-sampling-for-managed-code"></a>Désactiver l’échantillonnage au niveau ligne dans du code managé
 Par défaut, l’échantillonnage au niveau ligne est activé. Vous pouvez désactiver la collecte de données au niveau ligne pour du code managé à l’aide de l’une des commandes suivantes :

- Avant de commencer le profilage, tapez **VSPerfCLREnv /samplelineoff**. Cela affecte à la fois les applications et les services.

     — ou —

- Quand vous démarrez une application, tapez **VSPerfCmd \<other arguments> /LineOff **.

## <a name="see-also"></a>Voir aussi
- [Configurer des sessions de performance](../profiling/configuring-performance-sessions.md)
- [Analyser les données des outils d’analyse des performances](../profiling/analyzing-performance-tools-data.md)
