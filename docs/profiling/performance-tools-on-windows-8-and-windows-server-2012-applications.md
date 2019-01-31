---
title: Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012 | Microsoft Docs
ms.date: 06/19/2017
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e510705dc8aebad7cee6c8eea4e91c2522e4306
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54959708"
---
# <a name="performance-tools-on-windows-8-and-windows-server-2012-applications"></a>Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012

Les fonctionnalités de sécurité renforcées à compter de Windows 8 et Windows Server 2012 ont imposé des modifications importantes dans la façon dont les outils d’analyse des performances de Visual Studio collectent les données sur ces plateformes. Les applications UWP nécessitent aussi de nouvelles techniques de collecte. Cette rubrique décrit les modifications apportées aux outils d’analyse des performances à compter des plateformes Windows 8 et Windows Server 2012.

> [!NOTE]
> Les outils d’analyse des performances des autres versions prises en charge de Windows (Windows 7, Windows Server 2008 R2) n’ont pas changé.

## <a name="collect-data-on-uwp-apps-from-the-visual-studio-ide"></a>Collecter des données sur les applications UWP à partir de l’IDE Visual Studio

Quand vous profilez une application UWP écrite en JavaScript et HTML 5, vous collectez des données d’instrumentation pour le code JavaScript. Quand vous profilez une application UWP ou un composant écrit en Visual C++, Visual C# ou Visual Basic, vous collectez des données d’échantillonnage pour le code natif et managé. Vous pouvez profiler votre application localement ou sur un ordinateur distant.

Ces fonctionnalités et options de profilage ne sont pas prises en charge pour le profilage d’applications UWP :

- profilage d’applications JavaScript à l’aide de la méthode d’échantillonnage ;
- profilage de code managé et natif à l’aide de la méthode d’instrumentation ;
- profilage d’accès concurrentiel ;
- profilage de mémoire .NET ;
- profilage d’interaction de couche (TIP) ;
- options d’échantillonnage, telles que la définition de l’événement d’échantillonnage et l’intervalle de temporisation, ou la collecte de données de compteurs de performances supplémentaires ;
- options d’instrumentation, telles que la collecte de données de compteurs de performances et Windows, ou définition d’options de ligne de commande supplémentaires.

Pour plus d’informations sur le profilage d’applications UWP, consultez les articles suivants :

- [Exécuter des applications UWP sur l’ordinateur local](/visualstudio/debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml)
- [Exécuter des applications UWP sur un ordinateur distant](../debugger/run-windows-store-apps-on-a-remote-machine.md)
- [Découvrir les outils de profilage](profiling-feature-tour.md)
- [Mémoire JavaScript](../profiling/javascript-memory.md)
- [Profiler du code Visual C++, Visual C# et Visual Basic dans des applications UWP sur un ordinateur local](https://msdn.microsoft.com/2d0c939e-0bac-48c5-b727-46f6c6113060)
- [Profiler du code Visual C++, Visual C# et Visual Basic dans des applications UWP sur un appareil distant](https://msdn.microsoft.com/b932a2be-11b0-40fd-b996-75c6b6a79d22)
- [Analyser les données de performances du code Visual C++, Visual C# et Visual Basic dans des applications UWP](https://msdn.microsoft.com/5de4a413-d924-425f-afc4-e1ecfb0fca18)

## <a name="collect-data-on-apps-running-on-the-windows-8-desktop-or-on-windows-server-2012-from-the-visual-studio-ide"></a>Collecter des données sur des applications qui s’exécutent sur un poste de travail Windows 8 ou sur Windows Server 2012 à partir de l’IDE Visual Studio

Le profilage à l’aide de la méthode d’instrumentation n’a pas évolué pour Windows 8.

Le profilage d’interaction de couche (TIP) n’est pas pris en charge en utilisant la méthode d’échantillonnage.

## <a name="collect-data-on-apps-running-on-the-windows-8-desktop-or-on-windows-server-2012-by-using-sampling-from-the-visual-studio-ide"></a>Collecter des données sur des applications qui s’exécutent sur un poste de travail Windows 8 ou sur Windows Server 2012 en utilisant l’échantillonnage de l’IDE Visual Studio

Ces fonctionnalités et options de profilage ne sont pas prises en charge quand il s’agit de profiler des applications de bureau Windows 8 ou des applications Windows Server 2012 à l’aide de la méthode d’échantillonnage :

- Profilage d’interaction de couche (TIP). La collecte de données de TIP est prise en charge en utilisant l’instrumentation.

- Options d’échantillonnage, telles que la définition de l’événement d’échantillonnage et l’intervalle de temporisation, ou la collecte de données de compteurs de performances supplémentaires.

## <a name="profile-from-the-command-line"></a>Profiler à partir de la ligne de commande

Pour collecter les données de profilage sur les appareils Windows 8 et Windows Server 2012, y compris les appareils qui n’ont pas d’installation de Visual Studio, vous pouvez utiliser deux outils de ligne de commande :

|Nom de l’outil|Description|
|---------------|-----------------|
|[VSPerf](../profiling/vsperf.md)|Collecte les données de profilage à partir d’applications UWP, et collecte les données de profilage par échantillonnage à partir d’applications pour poste de travail Windows 8 et d’applications Windows Server 2012.|
|[VSPerfCmd](../profiling/vsperfcmd.md)|Collecte les données de profilage d’instrumentation, d’accès concurrentiel et d’interaction de couche à partir d’applications qui s’exécutent sur le bureau Windows 8 ou Windows Server 2012. Collecte tous les types de données de profilage à partir des versions précédentes de Windows.|

Les deux outils sont installés avec Visual Studio pour être utilisés sur l’ordinateur local.

Pour profiler des applications sur les appareils dépourvus de Visual Studio, procédez de l’une des façons suivantes :

- Téléchargez les outils dans le cadre des Outils de contrôle à distance pour Visual Studio à partir du [site web MSDN](http://go.microsoft.com/fwlink/?LinkID=219549).

- Copiez et exécutez le programme d’installation des outils de profilage autonomes à partir de votre ordinateur Visual Studio. Pour obtenir le chemin des outils de profilage, consultez [Spécifier le chemin des outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Choisissez le programme d’installation correspondant au système d’exploitation (x86/x64) de l’ordinateur distant.

> [!NOTE]
> Pour collecter les données de profilage TIP, vous devez installer le profileur autonome de votre ordinateur Visual Studio sur l’ordinateur distant.

Ces fonctionnalités et options de profilage ne sont pas prises en charge quand il s’agit de profiler des applications Windows 8 et Windows Server 2012 à partir de la ligne de commande :

- Collecte de données à partir d’applications web Windows 8 et Windows Server 2012 en utilisant le mode d’échantillonnage avec [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md).

- Collecte des données d’échantillonnage à l’aide de VsPerfCmd.exe.

- Options d’échantillonnage, telles que la définition de l’événement d’échantillonnage et l’intervalle de temporisation, ou la collecte de données de compteurs de performances supplémentaires.

## <a name="collect-tier-interaction-tip-data"></a>Collecter des données d’interaction entre niveaux

Le profilage d’interaction de couche fournit des informations supplémentaires sur les temps d’exécution des fonctions d’applications multicouches qui communiquent avec des bases de données via les services ADO.NET. Les données sont collectées uniquement pour les appels de fonctions synchrones.

**Éditions Visual Studio**

Pour collecter des données de profilage d’interaction de couche, vous pouvez utiliser n’importe quelle édition de Visual Studio. Cependant, ces données ne sont consultables que dans Visual Studio Enterprise.

**Windows 8 et Windows Server 2012**

1. Pour collecter des données d’interaction de couche à partir d’applications qui s’exécutent sur le bureau Windows 8 ou Windows Server 2012, vous devez utiliser la méthode d’instrumentation.

2. Vous ne pouvez pas collecter de données d’interaction de couche pour les applications UWP.

3. Vous pouvez inclure des données d’interaction de couche dans toutes les méthodes de profilage sur les autres versions prises en charge de Windows.

**Assistant Performance et Explorateur de performances**

Vous devez ajouter l’option de collecte de données d’interaction de couche à une exécution du profilage à partir de l’Explorateur de performances. Vous devez aussi ajouter le projet, l’exécutable ou le site web au nœud cible de l’Explorateur de performances. Consultez [Collecter les données d’interaction de couche](../profiling/collecting-tier-interaction-data.md).

**Collecte de données TIP sur un ordinateur distant**

Pour collecter des données d’interaction entre niveaux sur un ordinateur distant, vous devez copier le fichier **vs\_profiler\_**_\<Plateforme>_**\_**_\<Langage>_**.exe** depuis le dossier *%VSInstallDir%\Team Tools\Performance Tools\Setups* d’un ordinateur Visual Studio vers l’ordinateur distant, puis lancer l’installation. Vous ne pouvez pas utiliser les outils de profilage contenus dans le package de téléchargement [Débogage à distance](../debugger/remote-debugging.md).

Vous pouvez utiliser [VSPerfCmd](../profiling/vsperfcmd.md) ou [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) pour collecter les données de profilage.

**Rapports TIP**

Les données d’interaction de couche ne sont consultables que dans Visual Studio Enterprise. Les rapports d’interaction de couche basés sur des fichiers générés à l’aide de [VSPerfReport](../profiling/vsperfreport.md) ne sont pas disponibles.

## <a name="see-also"></a>Voir aussi

[Explorateur de performances](../profiling/performance-explorer.md)
[Configurer les sessions de performances](../profiling/configuring-performance-sessions.md)
[Profiler à partir de la ligne de commande](../profiling/using-the-profiling-tools-from-the-command-line.md)