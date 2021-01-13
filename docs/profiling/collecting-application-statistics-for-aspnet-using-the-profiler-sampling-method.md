---
title: Collecter des statistiques pour des applications web ASP.NET
description: Passez en revue les procédures et les options de collecte des statistiques de performances pour les applications Web ASP.NET à l’aide de l’outil VSPerfASPNETCmd et VSPerfCmd et de la méthode de profilage par échantillonnage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profiling tools, sampling method
- sampling profling method
ms.assetid: f8383ab1-eb49-4d3f-8608-d8b4d51a81be
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: ef1f4ef1c50db1234425ab164f377dab5ff12ea6
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149532"
---
# <a name="collect-statistics-for-aspnet-web-apps"></a>Collecter des statistiques pour des applications web ASP.NET

Cette section décrit les procédures et les options de collecte des statistiques de performances pour une application web ASP.NET à l’aide des outils en ligne de commande **VSPerfASPNETCmd** et **VSPerfCmd**, et de la méthode de profilage par échantillonnage.

> [!NOTE]
> Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications UWP nécessitent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

> [!NOTE]
> Même si l’outil **VSPerfCmd** vous permet d’accéder à l’intégralité des fonctionnalités des outils de profilage, y compris la suspension et la reprise du profilage, ainsi que la collecte de données supplémentaires à partir du processeur et des compteurs de performances Windows, vous devez utiliser l’outil en ligne de commande **VSPerfASPNETCmd** si vous n’avez pas besoin de ces fonctionnalités. L’outil en ligne de commande **VSPerfASPNETCmd** est recommandé quand vous profilez des sites web ASP.NET à l’aide du profileur autonome. Par rapport à l’outil en ligne de commande [VSPerfCmd](../profiling/vsperfcmd.md), cet outil ne nécessite ni configuration de variables d’environnement, ni redémarrage de l’ordinateur. Pour plus d’informations, consultez [profilage de site Web rapide avec VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).

## <a name="common-tasks"></a>Tâches courantes

|Tâche|Contenu associé|
|----------|---------------------|
|**Attacher le profileur à une application ASP.NET**|-   [Comment : attacher le profileur à une application Web ASP.NET pour collecter des statistiques d’applications](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="related-tasks"></a>Tâches associées

### <a name="profile-aspnet-web-applications"></a>Profiler des applications web ASP.NET

|Tâche|Contenu associé|
|----------|---------------------|
|**Profiler à l’aide de la méthode d’instrumentation**|-   [Collecter les données temporelles détaillées à l’aide de l’instrumentation](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md)|
|**Profiler l’allocation de mémoire et le garbage collection**|-   [Collecter des données de mémoire](../profiling/collecting-memory-data-from-an-aspnet-web-application.md)|
|**Profiler le conflit des ressources et l’activité des threads**|-   [Collecter les données d’accès concurrentiel](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="sample-method"></a>Méthode d’échantillonnage

|Tâche|Contenu associé|
|----------|---------------------|
|**Profiler des applications autonomes (clientes)**|-   [Collecter des statistiques d’applications en utilisant l’échantillonnage](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|-   **Services de profil**|-   [Collecter des statistiques d’applications en utilisant l’échantillonnage](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|

### <a name="analyze-sampling-data-views-and-reports"></a>Analyser des vues et des rapports de données d’échantillonnage
- [Vues de données de la méthode d’échantillonnage](../profiling/profiler-sampling-method-data-views.md)
