---
title: Collecter les données d’allocation de mémoire .NET & de durée de vie
description: Pour aider à détecter les problèmes de performances liés à la mémoire dans votre application .NET, utilisez Outils de profilage pour collecter les données d’allocation de mémoire et de durée de vie des objets.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- .NET memory profiling method
- Profiling Tools,.NET memory method
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: a9321ce83f65d5a7cac95d793d5f635651bef0e7
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533795"
---
# <a name="collect-net-framework-memory-allocation-and-lifetime-data"></a>Collecter les données d’allocation de mémoire et de durée de vie .NET Framework

Visual Studio Outils de profilage prennent en charge la collection de .NET Framework les données d’allocation de mémoire et de durée de vie des objets, ce qui vous permet de détecter les problèmes de performances liés à la mémoire dans votre application.

- Les données concernant l’allocation de mémoire .NET incluent le nombre d’objets mémoire .NET Framework qui ont été alloués, ainsi que leur taille.

- Les données concernant la durée de vie des objets incluent le nombre d’objets mémoire .NET Framework qui ont été récupérés dans les trois générations de garbage collection, ainsi que la taille de ces objets.

> [!NOTE]
> Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications UWP nécessitent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

Vous pouvez collecter des données à l’aide de la méthode de profilage par échantillonnage ou par instrumentation.

- Lorsque vous utilisez la méthode d’échantillonnage, le profileur suit toutes les allocations de mémoire .NET et les objets qui sont générés par le processus qui a été démarré ou attaché.

- Lorsque vous utilisez la méthode d’instrumentation, le profileur suit uniquement les allocations de mémoire .NET et les objets qui sont générés par les modules instrumentés.

> [!IMPORTANT]
> Lorsque vous collectez des données de mémoire .NET (allocations, durées de vie d’objets, ou les deux) à l’aide de la méthode d’échantillonnage, tous les événements d’échantillonnage spécifiés par l’utilisateur sont ignorés, et les événements d’allocation de mémoire appropriés sont utilisés pour collecter des données.

Si vous activez le profilage de l’allocation de mémoire .NET, vous activez également le mode Allocation. Si vous activez le profilage des données de durée de vie .NET, vous activez également le mode Durée de vie des objets. Pour plus d’informations, consultez [Allocations, vue](../profiling/dotnet-memory-allocations-view.md) et [Durée de vie de l’objet, vue](../profiling/object-lifetime-view.md).

Pour plus d’informations sur la façon de collecter les données de mémoire .NET en utilisant les outils en ligne de commande des outils de profilage, consultez la section « Utilisation des méthodes de mémoire .NET pour collecter les données d’allocation de mémoire et de durée de vie des objets » dans [Utilisation des outils de profilage à partir de la ligne de commande](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md).

## <a name="to-collect-net-memory-data"></a>Pour collecter des données de mémoire .NET

1. Dans l’ **Explorateur de performances**, cliquez avec le bouton droit sur la session de performance, puis cliquez sur **Propriétés**.

2. Dans la boîte de dialogue *Session de performance* **Pages de propriétés**, cliquez sur l’onglet **Général**, puis cochez la case **Collecter les informations d’allocation d’objets .NET**.

3. Pour collecter les données de durée de vie des objets .NET, cochez la case **Collecter aussi les informations de durée de vie des objets .NET**.

## <a name="common-tasks"></a>Tâches courantes

Vous pouvez spécifier des options supplémentaires dans la boîte de dialogue des _pages de propriétés_**session de performance** . Pour ouvrir la boîte de dialogue :

- Dans **Explorateur de performances**, cliquez avec le bouton droit sur le nom de la session de performance, puis cliquez sur **Propriétés**.

Les tâches du tableau suivant décrivent les options que vous pouvez spécifier dans la boîte de dialogue _Session de performance_**Pages de propriétés** quand vous collectez des données de mémoire .NET.

|Tâche|Contenu associé|
|----------|---------------------|
|Dans la page **Général**, spécifiez les détails d’affectation de noms pour le fichier de données de profilage (.vsp) généré.|- [Collecter les données d’allocation et de durée de vie de la mémoire .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />- [Procédure : définir les options de nom de fichier de données de performances](../profiling/how-to-set-performance-data-file-name-options.md)|
|Si votre solution de code contient plusieurs projets .exe, dans la page **Lancer**, spécifiez l’application à démarrer.|- [Collecter les données d’interaction de couche](../profiling/collecting-tier-interaction-data.md)|
|Dans la page **Interaction de couche** , ajoutez les données d’appel ADO.NET à l’exécution du profilage.|- [Collecter les données d’interaction de couche](../profiling/collecting-tier-interaction-data.md)|
|Dans la page **Événements Windows**, spécifiez un ou plusieurs événements de suivi d’événements pour Windows (ETW) à collecter avec les données d’échantillonnage.|- [Comment : collecter des données Suivi d’v nements pour Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|Dans la page **Compteurs Windows** , spécifiez un ou plusieurs compteurs de performance de système d’exploitation à ajouter aux données de profilage en tant que marques.|- [Comment : collecter les données des compteurs Windows](../profiling/how-to-collect-windows-counter-data.md)|
|Dans la page **Avancé**, spécifiez la version du runtime .NET Framework à profiler si vos modules d’application utilisent plusieurs versions. Par défaut, la première version chargée est profilée.|- [Comment : spécifier le Runtime .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|

## <a name="instrumentation-tasks"></a>Tâches d’instrumentation

Les tâches du tableau suivant correspondent aux options de la boîte de dialogue **Pages de propriétés** qui sont spécifiques au profilage à l’aide de la méthode d’instrumentation.

|Tâche|Contenu associé|
|----------|---------------------|
|Dans la page **Fichiers binaires** , spécifiez un emplacement pour les copies instrumentées des modules. Par défaut, les fichiers binaires d’origine sont déplacés vers un dossier de sauvegarde.|- [Comment : déplacer des binaires instrumentés](../profiling/how-to-relocate-instrumented-binaries.md)|
|Dans la page **Instrumentation** , excluez les petites fonctions du profilage pour réduire les surcharges de profilage, profilez le code JavaScript dans des pages web ASP.NET et spécifiez les commandes à exécuter dans une invite de commandes avant et après le processus d’instrumentation.|- [Comment : exclure ou inclure les fonctions courtes de l’instrumentation](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />- [Comment : profiler du code JavaScript dans des pages Web](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />- [Comment : spécifier des commandes de pré-instrumentation et de publication](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|
|Dans la page **Compteurs UC** , spécifiez un ou plusieurs compteurs de performance du processeur à ajouter aux données de profilage.|- [Procédure : collecter les données des compteurs UC](../profiling/how-to-collect-cpu-counter-data.md)|
|Dans la page **Avancé**, spécifiez les options VSInstr.exe supplémentaires de votre choix, telles que celles permettant d’inclure ou d’exclure des fonctions spécifiques. Pour plus d’informations sur les options de VSInstr, consultez [VSInstr](../profiling/vsinstr.md).|- [Guide pratique pour spécifier des options d’instrumentation supplémentaires](../profiling/how-to-specify-additional-instrumentation-options.md)<br />- [Comment : limiter l’instrumentation à des fonctions spécifiques](../profiling/how-to-limit-instrumentation-to-specific-functions.md)|

## <a name="see-also"></a>Voir aussi

[Configurer des sessions](../profiling/configuring-performance-sessions.md) 
 de performance [Comment : choisir des méthodes](../profiling/how-to-choose-collection-methods.md) 
 de collection [Propriétés](../profiling/performance-session-properties.md) de la session de performance
