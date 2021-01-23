---
title: Compteurs UC et Windows | Microsoft Docs
description: Les compteurs UC (matériel) et Windows (logiciels) fournissent des données de performances. Apprenez à les afficher et à collecter des données à partir de celles-ci.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.counters
helpviewer_keywords:
- Windows counters in Profiling Tools
- CPU counters in Profiling Tools
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2c3657f3558a688232424b868d0e93b8c056467c
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719160"
---
# <a name="cpu-and-windows-counters"></a>Compteurs UC et Windows

Le profileur Visual Studio permet de collecter les données de performances qui ont été générées par le système d’exploitation (compteurs Windows) et celles qui ont été générées par le processeur (compteurs UC).

> [!NOTE]
> Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications UWP nécessitent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="windows-counters"></a>Compteurs Windows

Les compteurs Windows font partie de l’infrastructure de diagnostics Windows qui fournit des informations sur les performances du système d’exploitation ou d’une application, d’un service ou d’un pilote. Les compteurs Windows dépendent de la configuration de l’ordinateur actuel et peuvent ne pas être disponibles sur d’autres ordinateurs. Les compteurs de performances Windows sont collectés dans les fichiers de données de profilage en tant que marques de profilage, qui peuvent ensuite servir à filtrer les vues et les rapports.

## <a name="cpu-counters"></a>Compteurs UC

Les compteurs UC sont une fonctionnalité du processeur de l’ordinateur qui stockent le nombre d’événements liés au matériel. Lorsque vous collectez des données de compteur UC à l’aide de la méthode de profilage par instrumentation, ces données sont ajoutées aux données concernant les fonctions et les modules. Vous pouvez collecter les données de plusieurs compteurs UC à l’aide de la méthode d’instrumentation. Avec la méthode d’échantillonnage, vous devez sélectionner le compteur à utiliser comme événement à échantillonner.

Les compteurs de performances sont spécifiques au processeur. Les différents modèles et versions d’un processeur peuvent avoir des paramètres de configuration très différents pour l’activation d’un même compteur de performances. Les événements portables du profileur [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] découplent certains compteurs de performances courants et certains processeurs, et permettent ainsi de collecter ou d’échantillonner des événements de performance génériques.

Si vous voulez comptabiliser un événement particulier lorsque vous utilisez le profileur (par exemple, les échecs du cache L2), vous pouvez créer une session de performance autour de cet émetteur d’événements. Vous pouvez procéder ainsi sur n’importe quel processeur disposant d’un cache L2. La session de performance peut être déplacée d’une plateforme à l’autre sans modification.

Le profileur Visual Studio continue de prendre en charge certains événements d’une plateforme spécifique. Par exemple, un développeur utilisant une plateforme Pentium 4 peut vouloir compter des événements qui sont spécifiques à l’architecture NetBurst. Cet événement n’est pas portable, mais reste disponible pour le développeur pour une session de performance spécifique sur une plateforme spécifique.

## <a name="portable-and-platform-events"></a>Événements portables et événements de plateforme

Les événements portables sont un groupe de compteurs UC qui ne sont pas spécifiques à un processeur. Tous les autres compteurs UC sont des événements de plateforme et peuvent ne pas être pris en charge sur toutes les plateformes.

 Les compteurs pour les événements portables et de plateforme sont définis dans. fichiers *XML* , où des valeurs spécifiques relatives aux compteurs sont fournies. Ces fichiers varient selon le processeur. En effet, les données des processeurs Intel et AMD, par exemple, ne sont pas les mêmes. Le profileur [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] utilise ces informations pour présenter des compteurs appropriés (à la fois pour les événements portables et les événements de plateforme) à l’utilisateur pour qu’il puisse mesurer les performances.

### <a name="portable-events"></a>Événements portables

Les événements portables contiennent les événements suivants :

**Événements généraux**

|Nom de l'événement|Description de l'événement|
|----------------|-----------------------|
|Instructions retirées|Indique le nombre d’instructions qui ont été exécutées avant la fin de l’événement.|
|Cycles hors interruption|Indique uniquement les cycles au cours desquels le processeur n’est pas arrêté, comme pour une attente d’E/S.|

**Événements frontaux**

|Nom de l'événement|Description de l'événement|
|----------------|-----------------------|
|Échecs dans ITLB|Indique le nombre de recherches dans le tampon de traduction ITLB qui ont échoué.|

**Événements de branche**

|Nom de l'événement|Description de l'événement|
|----------------|-----------------------|
|Branches retirées|Indique le nombre d’instructions de branche qui ont été exécutées avant la fin de l’événement.|
|Branches mal prédites|Indique les branches mal prédites qui sont dues à la mauvaise prédiction du chemin par le processeur. Les branches mal prédites affectent les performances, car le processeur doit abandonner tout le travail effectué et recommencer sur le bon chemin.|

**Événements mémoire**

|Nom de l'événement|Description de l'événement|
|----------------|-----------------------|
|Échecs de l'accès en lecture au cache L2|Indique le nombre d’échecs de lecture du cache de deuxième niveau (L2).|
|Références de lecture du cache L2|Indique le nombre de références de lecture du cache de deuxième niveau (L2). Cela comprend les échecs de chargement, ainsi que les échecs et les réussites RFO (Read For Ownership).|

## <a name="view-available-counters"></a>Voir les compteurs disponibles

Vous pouvez obtenir la liste des compteurs UC disponibles dans l’IDE de Visual Studio, à partir d’une fenêtre d’invite de commandes.

### <a name="visual-studio-ui"></a>Interface utilisateur de Visual Studio

Pour voir la liste des compteurs disponibles sur un ordinateur à partir de l’IDE de Visual Studio, vous devez avoir ouvert une session de performance de profileur dans l’Explorateur de performances.

#### <a name="to-view-a-list-of-a-list-of-all-cpu-counters-that-are-supported-on-the-current-platform"></a>Pour afficher la liste de tous les compteurs UC pris en charge sur la plateforme actuelle

1. Dans Explorateur de performances, cliquez avec le bouton droit sur la session de performance, puis cliquez sur **Propriétés**.

2. Effectuez l’une des actions suivantes :

   - Cliquez sur **Échantillonnage**, puis sélectionnez **Compteur de performances** dans la liste des événements **Échantillon**. Les compteurs UC sont répertoriés sous **Compteurs de performances disponibles**.

      **Remarque** Cliquez sur **Annuler** pour revenir à la configuration d’échantillonnage précédente.

     -ou-

   - Sélectionnez **Compteurs UC**, puis sélectionnez **Collecter les compteurs UC**. Les compteurs UC sont répertoriés sous **Compteurs disponibles**.

      **Remarque** Cliquez sur **Annuler** pour revenir à la configuration de la collection de compteurs précédente.

#### <a name="to-view-a-list-of-a-list-of-window-counters-that-are-supported-on-the-current-platform"></a>Pour afficher la liste des compteurs Windows pris en charge sur la plateforme actuelle

1. Dans Explorateur de performances, cliquez avec le bouton droit sur la session de performance, puis cliquez sur **Propriétés**.

2. Cliquez sur **Compteurs Windows**.

3. Sélectionnez **Collecter les compteurs Windows**.

4. Dans la liste **Catégorie de compteurs**, sélectionnez un groupe de compteurs. Le compteur Windows du groupe s’affiche dans la zone de liste.

     **Remarque** Cliquez sur **Annuler** pour revenir à la configuration de collecte de compteur précédente.

### <a name="command-line"></a>Ligne de commande

L’outil en ligne de commande [VSPerfCmd](../profiling/vsperfcmd.md) permet de répertorier les compteurs UC qui sont disponibles sur un ordinateur à partir de la ligne de commande.

#### <a name="to-list-of-cpu-counters-that-are-supported-on-the-current-platform"></a>Pour répertorier les compteurs UC pris en charge sur la plateforme actuelle

1. Ouvrir une fenêtre d’invite de commandes.

2. Type

     **\<Visual Studio Performance Tools Directory>\VSPerfCmd/QueryCounters**

     où *\<Visual Studio Performance Tools Directory>* est le chemin d’accès au répertoire des outils de performances de votre installation de Visual Studio. Pour obtenir le chemin d’accès des outils d’analyse des performances, voir [Spécifier le chemin d’accès des outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

## <a name="see-also"></a>Voir aussi

- [Vues d'ensemble](../profiling/overviews-performance-tools.md)
- [Comment : choisir des événements d’échantillonnage](../profiling/how-to-choose-sampling-events.md)
- [Procédure : collecter les données des compteurs UC](../profiling/how-to-collect-cpu-counter-data.md)
- [Comment : collecter les données des compteurs Windows](../profiling/how-to-collect-windows-counter-data.md)
