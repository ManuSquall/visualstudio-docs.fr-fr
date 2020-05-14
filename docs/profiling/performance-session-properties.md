---
title: Propriétés d’une session de performance | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,properties
- property pages,Profiling Tools
- performance tools, performance session properties
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1b3bafa976c8e57f468a3f3f59a3b6b19308fd1b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772200"
---
# <a name="performance-session-properties"></a>Propriétés d’une session de performance

Une **session de performance** vous permet de configurer les paramètres qui déterminent le profilage de l’application. Elle stocke également les rapports générés pour la session de profilage.

Pour créer une **session de performance**, exécutez l’**Assistant Performance** ou créez une session manuellement. Une fois la **session de performance** créée, **session de performance** s’affiche dans l’**Explorateur de performances**.

Pour afficher les propriétés d’une **session de performance**, sélectionnez son nom dans l’**Explorateur de performances**, cliquez dessus avec le bouton droit, puis sélectionnez **Propriétés**.

La session de performance présente les pages de propriétés suivantes :

## <a name="general"></a>Général

Ces paramètres vous permettent de sélectionner la méthode de profilage, d’ajouter la collection d’objets .NET et les données de durée de vie, ainsi que de spécifier l’emplacement des rapports par défaut et les conventions d’affectation de noms.

Pour plus d'informations, consultez les pages suivantes :

[Comment : Choisissez des méthodes de collecte](../profiling/how-to-choose-collection-methods.md)

[Collecter les données liées à l’allocation et à la durée de vie de la mémoire .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)

- [Guide pratique pour définir les options de nom de fichier des données de performance](../profiling/how-to-set-performance-data-file-name-options.md)

## <a name="launch"></a>Launch

Ces paramètres vous permettent de sélectionner des fichiers binaires dans une liste et de spécifier l’ordre de démarrage des fichiers binaires.

Pour plus d’informations, voir [Comment : Spécifier le binaire pour commencer](../profiling/how-to-specify-the-binary-to-start.md)

## <a name="sampling"></a>échantillonnage

Ces paramètres vous permettent de sélectionner l’événement d’échantillon et l’intervalle d’échantillonnage en cas d’utilisation de l’échantillonnage comme méthode de profilage. Un événement d’échantillon est utilisé pour collecter les données de profilage à l’intervalle spécifié. Par exemple, pour l’événement d’échantillon Cycles d’horloge, si l’intervalle d’échantillonnage a la valeur 10 000 000, les données de profilage sont collectées chaque fois que 10 millions de cycles d’horloge sont effectués. Les quatre types d’événements d’échantillons suivants sont disponibles :

- Cycles d’horloge : pour les problèmes liés à l’unité centrale
- Erreurs de page : pour les problèmes liés à la mémoire
- Appels système : pour les problèmes liés à l’E/S
- Compteurs de performance : pour les problèmes de performances de bas niveau
- Il est possible de spécifier des événements d’échantillon supplémentaires sur la base des compteurs de performance disponibles.

Pour plus d’informations, voir [Comment : Choisissez des événements d’échantillonnage](../profiling/how-to-choose-sampling-events.md)

## <a name="binary"></a>Binary
Ces paramètres vous permettent de spécifier si vous souhaitez déplacer le fichier binaire instrumenté vers un autre emplacement. Par exemple, si vous dressez le profil *My.DLL* et choisissez de ne pas déplacer le binaire instrumenté, une copie de sauvegarde de *My.DLL* nommée *My.Orig.DLL* est créée. Par la suite, *My.DLL* est modifié en insérant des sondes pour collecter des données. Si vous déplacez le fichier binaire instrumenté, le fichier binaire d’origine n’est pas renommé et le fichier binaire instrumenté est copié dans l’emplacement spécifié pour être utilisé pendant l’instrumentation.

Pour plus d’informations, voir [Comment : Spécifier le binaire pour commencer](../profiling/how-to-specify-the-binary-to-start.md)

## <a name="tier-interactions"></a>Interactions de couche

Pour plus d’informations, consultez [Collecte de données d’interaction de couche](../profiling/collecting-tier-interaction-data.md).

## <a name="instrumentation"></a>Instrumentation

Ces paramètres vous permettent de collecter les données de performance pour le code JScript dans les pages web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] et de spécifier les événements de **pré-instrumentation** et de **post-instrumentation** devant se produire avant ou après le processus d’instrumentation.

Pour plus d'informations, consultez les pages suivantes :

[Comment : Profil du code JavaScript dans les pages Web](../profiling/how-to-profile-javascript-code-in-web-pages.md)

[Guide pratique pour spécifier des commandes de pré-instrumentation et de post-instrumentation](../profiling/how-to-specify-pre-and-post-instrument-commands.md)

## <a name="cpu-counters"></a>Compteurs UC

Ces paramètres vous permettent de collecter des données à propos des compteurs de performance de l’UC quand vous utilisez l’instrumentation comme méthode de profilage. Les compteurs de performance portables sont disponibles indépendamment de la conception ou du fabricant de l’UC. Les événements de plateforme sont spécifiques à la conception et au fabricant de l’UC. Pour plus d’informations sur les compteurs de performance de processeur, consultez la documentation spécifique au processeur.

Pour plus d’informations, voir [Comment : Collecter des données de compteur CPU](../profiling/how-to-collect-cpu-counter-data.md)

## <a name="windows-events"></a>Événements Windows

Pendant le profilage, vous pouvez collecter des données à partir de fournisseurs de suivi d’événements. Vous pouvez afficher les données en utilisant l’option d’outil `/calltrace` de ligne de commande *VSPerfReport.exe.* Pour plus d’informations sur le suivi d’événements pour Windows (ETW), consultez [À propos du suivi d’événements](/windows/win32/etw/about-event-tracing).

Pour plus d'informations, consultez les pages suivantes :

[Comment : Recueillir le traçage des événements pour les données Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)

[VSPerfReport](../profiling/vsperfreport.md).

## <a name="windows-counters"></a>Compteurs Windows

Cette option vous permet de collecter les données des compteurs de l’Analyseur de performances Windows. Pour collecter ces données, cochez la case **Collecter les compteurs de performance Windows**. L’intervalle de collecte peut être défini dans la zone **Intervalle de collecte**. Les options **Catégorie de compteurs** et **Instance** peuvent également être disponibles. Certains compteurs de l’Analyseur de performances Windows par défaut sont disponibles.

 Pour plus d’informations, voir [Comment : Collecter des données de compteur Windows](../profiling/how-to-collect-windows-counter-data.md).

## <a name="advanced"></a>Avancé

Ces paramètres vous permettent d’ajouter des options au processus d’instrumentation en spécifiant une ou plusieurs options de l’outil de profilage en ligne de commande [VSInstr](../profiling/vsinstr.md). Vous pouvez également spécifier la version du Common Runtime à profiler quand l’application utilise plusieurs versions.

Pour plus d'informations, consultez les pages suivantes :

[Guide pratique pour spécifier le runtime .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)

[Guide pratique pour spécifier des options d’instrumentation supplémentaires](../profiling/how-to-specify-additional-instrumentation-options.md)

## <a name="see-also"></a>Voir aussi

[Aperçus](../profiling/overviews-performance-tools.md)
[Configurer les sessions de](../profiling/configuring-performance-sessions.md)
performance[Contrôlez la collecte de données](../profiling/controlling-data-collection.md)
