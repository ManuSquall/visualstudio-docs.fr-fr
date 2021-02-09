---
title: Utiliser des méthodes de profilage de ligne de commande pour obtenir des données de performances
description: Découvrez comment le choix des outils et options de ligne de commande de Visual Studio Outils de profilage dépend de facteurs tels que le type d’application que vous profilez.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5613fafc-f298-4e7a-9a2d-a853b61cdf9c
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ebcd3fdbc09029309d1b06efc75417add223ce04
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917589"
---
# <a name="use-profiling-methods-to-collect-performance-data-from-the-command-line"></a>Utiliser des méthodes de profilage pour collecter des données de performances à partir de la ligne de commande
Votre choix d’outils et d’options de ligne de commande des outils de profilage de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dépend de facteurs comme le type d’application que vous profilez, la méthode de profilage que vous voulez utiliser, et de ce que l’application cible est écrite en code natif ou en code .NET Framework.

 Cette rubrique classe les rubriques des procédures pour la ligne de commande en fonction de la méthode de profilage que vous choisissez.

## <a name="use-the-sampling-method-to-collect-performance-statistics"></a>Utiliser la méthode d’échantillonnage pour collecter les statistiques de performances
 La méthode d’échantillonnage des outils de profilage collecte les données de performances à des intervalles spécifiés dans une exécution du profilage. L’échantillonnage des données peut fournir des insights sur les problèmes de performances liées à l’UC, et il peut être un bon moyen de commencer à explorer les performances d’une application.

 Vous pouvez démarrer le profileur et l’application en même temps, ou vous pouvez attacher le profileur à une instance d’une application en cours d’exécution.

|Tâche|Type d’application cible|
|----------|-----------------------------|
|**Lancer une application**|-   [Applications autonomes](../profiling/how-to-launch-a-stand-alone-app-and-collect-application-statistics.md)|
|**Attacher à un processus en cours d’exécution**|-   [.NET Framework des applications autonomes](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-application-statistics.md)<br />-   [Applications autonomes natives](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-application-statistics.md)<br />-   [Applications Web ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Services .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Services natifs](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="use-the-instrumentation-method-to-collect-detailed-timing-data"></a>Utiliser la méthode d’instrumentation pour collecter les données de minutage détaillées
 La méthode d’instrumentation des outils de profilage collecte des données de performances à partir de copies de fichiers binaires de l’application qui contiennent des sondes logicielles pour enregistrer des informations sur les performances. Les données d’instrumentation sont collectées au début et à la fin de chaque fonction instrumentée et à chaque appel à d’autres fonctions depuis la fonction instrumentée. La méthode d’instrumentation est utile pour détecter les problèmes de performances avec les E/S, comme l’utilisation des disques.

 Vous créez le fichier binaire instrumenté avec l’outil [VInstr.exe](../profiling/vsinstr.md). Une fois le profileur initialisé, les données sont collectées automatiquement à partir des fichiers binaires instrumentés quand vous exécutez l’application cible.

 **Type d’application cible**

- [.NET Framework composants autonomes](../profiling/how-to-instrument-a-dotnet-framework-component-and-collect-timing-data.md)

- [Composants autonomes natifs](../profiling/how-to-instrument-a-native-component-and-collect-timing-data.md)

- [Applications Web ASP.NET compilées statiquement](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)

- [Applications Web ASP.NET compilées dynamiquement](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)

- [Services .NET](../profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)

- [Services natifs](../profiling/how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)

## <a name="use-net-memory-methods-to-collect-memory-allocation-and-object-lifetime-data"></a>Utiliser des méthodes de mémoire .NET pour collecter les données d’allocation de mémoire et de durée de vie des objets
 La méthode de mémoire .NET des outils de profilage vous permet de collecter des données d’allocation de mémoire du .NET Framework et des informations sur la durée de vie des objets dans le .NET Framework.

 Vous pouvez démarrer l’application cible à l’aide du profileur, vous pouvez attacher le profileur à une instance en cours d’exécution d’une application ou vous pouvez créer des versions instrumentées de l’application pour collecter des informations de minutage détaillées avec les données de mémoire du .NET Framework.

|Tâche|Type d’application cible|
|----------|-----------------------------|
|**Lancer une application**|-   [Applications de .NET Framework autonomes](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-memory-data.md)|
|**Attacher à un processus en cours d’exécution**|-   [.NET Framework des applications autonomes](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-app-to-collect-memory-data.md)<br />-   [Applications Web ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [Services .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-memory-data-by-using-the-command-line.md)|
|**Instrumenter des modules**|-   [.NET Framework composants autonomes](../profiling/how-to-instrument-a-dotnet-framework-component-and-collect-memory-data.md)<br />-   [Applications Web ASP.NET compilées statiquement](../profiling/how-to-instrument-a-statically-compiled-aspnet-app-and-collect-memory-data.md)<br />-   [Applications Web ASP.NET compilées dynamiquement](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)<br />-   [Services .NET](../profiling/how-to-instrument-a-dotnet-framework-service-and-collect-memory-data-by-using-the-profiler-command-line.md)|

## <a name="use-the-concurrency-method-to-collect-resource-contention-and-thread-activity-data"></a>Utiliser la méthode de concurrence pour collecter les données de conflit de ressources et d’activité du thread
 La méthode de concurrence des outils de profilage vous permet de collecter des données sur les conflits de ressources et sur l’activité des threads et des processus à partir d’applications multithreads.

 Vous pouvez démarrer l’application à l’aide du profileur, ou vous pouvez attacher le profileur à une instance d’une application en cours d’exécution.

|Tâche|Type d’application cible|
|----------|-----------------------------|
|**Lancer une application**|-   [Application .NET Framework autonome](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)<br />-   [Application native autonome](../profiling/how-to-launch-a-stand-alone-native-application-to-collect-concurrency-data.md)|
|**Attacher à un processus en cours d’exécution**|-   [Application .NET Framework autonome](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)<br />-   [Application autonome native](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data.md)<br />-   [Application Web ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Service .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Service natif](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|

## <a name="add-tier-interaction-data-to-a-profiling-run"></a>Ajouter des données d’interaction de couche à une exécution du profilage
 L’ajout de données d’interaction de couche à une exécution de profilage nécessite des procédures spécifiques avec les outils de profilage en ligne de commande. Consultez [collecter les données d’interaction de couche](../profiling/adding-tier-interaction-data-from-the-command-line.md)

## <a name="see-also"></a>Voir aussi
- [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profiler des applications Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profiler des services](../profiling/command-line-profiling-of-services.md)
