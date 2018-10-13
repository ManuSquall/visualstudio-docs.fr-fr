---
title: Collecte des données liées à la durée de vie des objets et à l’allocation de mémoire .NET | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- .NET memory profiling method
- Profiling Tools,.NET memory method
ms.assetid: 62a6dd5f-db66-4456-9d57-f8913dbfe4d5
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 53443ed1681e5709edc0581fca8e2fd46a51834d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245555"
---
# <a name="collecting-net-memory-allocation-and-lifetime-data"></a>Collecte des données liées à la durée de vie des objets et à l’allocation de mémoire .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les outils de profilage [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prennent en charge la collecte des données d’allocation de mémoire .NET et de durée de vie des objets, ce qui permet de détecter les problèmes de performances liés à la mémoire de votre application.  
  
-   Les données concernant l’allocation de mémoire .NET incluent le nombre d’objets mémoire .NET Framework qui ont été alloués, ainsi que leur taille.  
  
-   Les données concernant la durée de vie des objets incluent le nombre d’objets mémoire .NET Framework qui ont été récupérés dans les trois générations de garbage collection, ainsi que la taille de ces objets.  
  
 **Spécifications**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
>  Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications Windows Store demandent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Vous pouvez collecter des données à l’aide de la méthode de profilage par échantillonnage ou par instrumentation.  
  
-   Lorsque vous utilisez la méthode d’échantillonnage, le profileur suit toutes les allocations de mémoire .NET et les objets qui sont générés par le processus qui a été démarré ou attaché.  
  
-   Lorsque vous utilisez la méthode d’instrumentation, le profileur suit uniquement les allocations de mémoire .NET et les objets qui sont générés par les modules instrumentés.  
  
> [!IMPORTANT]
>  Lorsque vous collectez des données de mémoire .NET (allocations, durées de vie d’objets, ou les deux) à l’aide de la méthode d’échantillonnage, tous les événements d’échantillonnage spécifiés par l’utilisateur sont ignorés, et les événements d’allocation de mémoire appropriés sont utilisés pour collecter des données.  
  
 Si vous activez le profilage de l’allocation de mémoire .NET, vous activez également le mode Allocation. Si vous activez le profilage des données de durée de vie .NET, vous activez également le mode Durée de vie des objets. Pour plus d’informations, consultez [Allocations, vue](../profiling/dotnet-memory-allocations-view.md) et [Durée de vie de l’objet, vue](../profiling/object-lifetime-view.md).  
  
 Pour plus d’informations sur la façon de collecter les données de mémoire .NET en utilisant les outils en ligne de commande des outils de profilage, consultez la section « Utilisation des méthodes de mémoire .NET pour collecter les données d’allocation de mémoire et de durée de vie des objets » dans [Utilisation des outils de profilage à partir de la ligne de commande](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md).  
  
### <a name="to-collect-net-memory-data"></a>Pour collecter des données de mémoire .NET  
  
1.  Dans l’ **Explorateur de performances**, cliquez avec le bouton droit sur la session de performance, puis cliquez sur **Propriétés**.  
  
2.  Dans la boîte de dialogue _Session de performance_**Pages de propriétés**, cliquez sur l’onglet **Général**, puis cochez la case **Collecter les informations d’allocation d’objets .NET**.  
  
3.  Pour collecter les données de durée de vie des objets .NET, cochez la case **Collecter aussi les informations de durée de vie des objets .NET**.  
  
## <a name="common-tasks"></a>Tâches courantes  
 Vous pouvez spécifier des options supplémentaires dans la boîte de dialogue des _pages de propriétés_**session de performance** . Pour ouvrir la boîte de dialogue :  
  
-   Dans l’ **Explorateur de performances**, cliquez avec le bouton droit sur le nom de la session de performance, puis cliquez sur **Propriétés**.  
  
 Les tâches du tableau suivant décrivent les options que vous pouvez spécifier dans la boîte de dialogue _Session de performance_**Pages de propriétés** quand vous collectez des données de mémoire .NET.  
  
|Tâche|Contenu associé|  
|----------|---------------------|  
|Dans la page **Général**, spécifiez les détails d’affectation de noms pour le fichier de données de profilage (.vsp) généré.|-   [Collecte des données liées à la durée de vie des objets et à l’allocation de mémoire .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Guide pratique pour définir les options de nom de fichier de données de profilage](../profiling/how-to-set-performance-data-file-name-options.md)|  
|Si votre solution de code contient plusieurs projets .exe, dans la page **Lancer**, spécifiez l’application à démarrer.|-   [Collecte de données d’interaction de couche](../profiling/collecting-tier-interaction-data.md)|  
|Dans la page **Interaction de couche** , ajoutez les données d’appel ADO.NET à l’exécution du profilage.|-   [Collecte de données d’interaction de couche](../profiling/collecting-tier-interaction-data.md)|  
|Dans la page **Événements Windows**, spécifiez un ou plusieurs événements de suivi d’événements pour Windows (ETW) à collecter avec les données d’échantillonnage.|-   [Guide pratique pour collecter les données de suivi d’événements pour Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|  
|Dans la page **Compteurs Windows** , spécifiez un ou plusieurs compteurs de performance de système d’exploitation à ajouter aux données de profilage en tant que marques.|-   [Guide pratique pour collecter les données des compteurs Windows](../profiling/how-to-collect-windows-counter-data.md)|  
|Dans la page **Avancé**, spécifiez la version du runtime .NET Framework à profiler si vos modules d’application utilisent plusieurs versions. Par défaut, la première version chargée est profilée.|-   [Guide pratique pour spécifier le runtime .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|  
  
## <a name="instrumentation-tasks"></a>Tâches d’instrumentation  
 Les tâches du tableau suivant correspondent aux options de la boîte de dialogue **Pages de propriétés** qui sont spécifiques au profilage à l’aide de la méthode d’instrumentation.  
  
|Tâche|Contenu associé|  
|----------|---------------------|  
|Dans la page **Fichiers binaires** , spécifiez un emplacement pour les copies instrumentées des modules. Par défaut, les fichiers binaires d’origine sont déplacés vers un dossier de sauvegarde.|-   [Guide pratique pour déplacer des binaires instrumentés](../profiling/how-to-relocate-instrumented-binaries.md)|  
|Dans la page **Instrumentation** , excluez les petites fonctions du profilage pour réduire les surcharges de profilage, profilez le code JavaScript dans des pages web ASP.NET et spécifiez les commandes à exécuter dans une invite de commandes avant et après le processus d’instrumentation.|-   [Guide pratique pour exclure ou inclure les fonctions courtes dans l’instrumentation](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />-   [Guide pratique pour profiler du code JavaScript dans des pages web](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Guide pratique pour spécifier des commandes de pré-instrumentation et de post-instrumentation](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|  
|Dans la page **Compteurs UC** , spécifiez un ou plusieurs compteurs de performance du processeur à ajouter aux données de profilage.|-   [Guide pratique pour collecter les données des compteurs UC](../profiling/how-to-collect-cpu-counter-data.md)|  
|Dans la page **Avancé**, spécifiez les options VSInstr.exe supplémentaires de votre choix, telles que celles permettant d’inclure ou d’exclure des fonctions spécifiques. Pour plus d’informations sur les options de VSInstr, consultez [VSInstr](../profiling/vsinstr.md).|-   [Guide pratique pour spécifier des options d’instrumentation supplémentaires](../profiling/how-to-specify-additional-instrumentation-options.md)<br />-   [Guide pratique pour limiter l’instrumentation à des fonctions spécifiques](../profiling/how-to-limit-instrumentation-to-specific-functions.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de sessions de performance](../profiling/configuring-performance-sessions.md)   
 [Guide pratique pour choisir une méthode de collecte](../profiling/how-to-choose-collection-methods.md)   
 [Propriétés d’une session de performance](../profiling/performance-session-properties.md)



