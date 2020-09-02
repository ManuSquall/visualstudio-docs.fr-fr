---
title: Outils de profilage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.diagnosticshub.overview
ms.assetid: 0fb6cd5d-e16a-4526-84a5-19e63c625bc5
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bcb230532da4a0b84ea0102d86534c28afe35558
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686248"
---
# <a name="profiling-tools"></a>outils de profilage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les outils de profilage et de diagnostic vous aident à diagnostiquer l’utilisation de la mémoire et du processeur et d’autres problèmes au niveau de l’application. Grâce à ces outils, vous pouvez accumuler des données (par exemple, des valeurs de variables, des appels de fonctions et des événements) pendant que vous exécutez votre application dans le débogueur. Vous pouvez examiner l’état de votre application à différents stades au cours de l’exécution de votre code.  
  
 Vous trouverez au bas de l’article un résumé des outils disponibles pour le type de votre projet (par exemple, application de bureau, UWP, ASP.NET).  
  
 Vous pouvez accéder aux outils de profilage en sélectionnant **Déboguer / Windows / Afficher les outils de diagnostic** pour utiliser les outils durant votre session de débogage, ou en sélectionnant **Déboguer / Profileur de performances...** pour effectuer une analyse de performances ciblée.  Pour plus d’informations sur les différentes approches, consultez [Exécution des outils de profilage avec ou sans le débogueur](../profiling/running-profiling-tools-with-or-without-the-debugger.md) .  
  
 ![DebugDiagnosticsToolsMenu](../profiling/media/debugdiagnosticstoolsmenu.png "DebugDiagnosticsToolsMenu")  
  
 Pour en savoir plus sur les nouvelles fonctionnalités de cette version, consultez [Nouveautés des outils de profilage](../profiling/what-s-new-in-profiling-tools.md).  
  
 Les sections suivantes décrivent les différents outils d’analyse des performances disponibles dans Visual Studio.  
  
## <a name="memory-usage"></a>Utilisation de la mémoire  
 ![DiagMemorySmall](../profiling/media/diagmemorysmall.png "DiagMemorySmall")  
  
 Recherchez les fuites de mémoire et la mémoire inefficace pendant le débogage avec l’outil utilisation de la **mémoire** . L’outil vous permet de prendre des captures instantanées du tas de mémoire managé et natif. Vous pouvez utiliser cet outil avec les applications de bureau, les applications universelles Windows et les applications ASP.NET. L’outil **utilisation** de la mémoire peut être exécuté à partir de la fenêtre **outils de diagnostic** pendant le débogage (déboguer **/Windows/afficher outils de diagnostic**) ou en dehors du débogueur (**Déboguer/profileur de performances...**). Pour plus d’informations, consultez  [utilisation](../profiling/memory-usage.md) de la mémoire et utilisation de la [mémoire sans débogage](https://msdn.microsoft.com/library/8883bc5f-df86-4f84-aa2b-a21150f499b0) .  
  
## <a name="cpu-usage"></a>Utilisation de l'UC  
 ![DiagCPUSmall](../profiling/media/diagcpusmall.png "DiagCPUSmall")  
  
 L'outil **Utilisation du processeur** vous montre où le processeur consacre son temps à exécuter le code C++, C#/VB et JavaScript.  Vous pouvez utiliser cet outil avec les applications de bureau et les applications universelles Windows, mais aussi avec les applications Azure App Services. L’outil **utilisation** de l’UC peut être exécuté à partir de la fenêtre **outils de diagnostic** pendant le débogage (déboguer **/Windows/afficher outils de diagnostic**) ou en dehors du débogueur (**Déboguer/profileur de performances...**). Pour plus d’informations, consultez [utilisation de l’UC](../profiling/cpu-usage.md) .  
  
## <a name="performance-explorer"></a>Explorateur de performances  
 ![PerfTools](../profiling/media/perftools.png "PerfTools")  
  
 L’ **Explorateur de performances** (**Déboguer / Profileur / Explorateur de performances**) vous permet d’utiliser différents outils, dont **Échantillonnage de l’UC**,  **Instrumentation**, **Allocation de mémoire .NET**et **Conflit de ressources**. Vous pouvez utiliser les outils Explorateur de performances avec les applications de bureau et les applications ASP.NET, mais pas avec les applications universelles Windows. Pour plus d’informations, consultez [Explorateur de performances](../profiling/performance-explorer.md).  
  
## <a name="gpu-usage"></a>Utilisation du GPU  
 ![DiagGPUUsage](../profiling/media/diaggpuusage.png "DiagGPUUsage")  
  
 Utilisez l’outil [GPU Usage](../debugger/gpu-usage.md) pour mieux comprendre l’utilisation générale du matériel par votre application Direct3D. Vous pouvez utiliser cet outil avec les applications de bureau et les applications universelles Windows, mais pas avec les applications ASP.NET. L’outil **Utilisation de l’UC** peut être exécuté à partir de la fenêtre **Outils de diagnostic** pendant le débogage (**Déboguer / Afficher les outils de diagnostic**) ou en dehors du débogueur (**Déboguer / Profileur de performances...**).  
  
## <a name="application-timeline"></a>Chronologie de l'application  
 ![DiagAppTimeline](../profiling/media/diagapptimeline.png "DiagAppTimeline")  
  
 L’outil [Application Timeline](../profiling/application-timeline.md) vous aide à améliorer les performances des applications XAML en offrant une vue détaillée de leur consommation de ressources. Vous pouvez utiliser **Chronologie de l’application** avec les applications de bureau et les applications universelles Windows, mais pas avec les applications ASP.NET. L’outil **Chronologie de l’application** peut être exécuté à partir de la fenêtre **Outils de diagnostic** (**Déboguer / Profileur de performances...**).  
  
## <a name="perftips"></a>Conseils sur les performances  
 ![DiagPerfTips](../profiling/media/diagperftips.png "DiagPerfTips")  
  
 Quand le débogueur arrête l'exécution à un point d'arrêt ou lors de l'exécution pas à pas, le temps qui s'écoule entre l'arrêt et le point d'arrêt précédent apparaît sous la forme d'un conseil dans la fenêtre de l'éditeur. Ces [PerfTips](../profiling/perftips.md) vous permettent de surveiller et d’analyser les performances de votre application pendant le débogage. Vous pouvez afficher les **Conseils sur les performances** dans les applications de bureau, les applications universelles Windows et les applications ASP.NET.  
  
## <a name="javascript-memory"></a>Mémoire JavaScript  
 ![Diagnostics](../profiling/media/diagjsmemory.png "Diagnostics")  
  
 L’outil [JavaScript Memory](../profiling/javascript-memory.md) vous permet de mesurer, d’évaluer et de cibler les problèmes liés aux performances dans votre code en recueillant des informations de minutage à l’entrée et à la sortie de chaque fonction de votre application. Vous pouvez utiliser cet outil avec les applications HTML universelles Windows. L’outil **Minutage de fonction JavaScript** peut être exécuté à partir de la fenêtre **Outils de diagnostic** (**Déboguer / Profileur de performances...**).  
  
## <a name="html-ui-responsiveness"></a>Réactivité de l'interface utilisateur HTML  
 ![Réactivité](../profiling/media/diaghtmlresp.png "Réactivité")  
  
 L’outil [Réactivité de l’interface utilisateur HTML](../profiling/html-ui-responsiveness.md) vous aide à isoler les problèmes de performances dans vos applications, comme le manque de réactivité, les lenteurs de chargement et les mises à jour visuelles qui sont moins fréquentes que prévu. Vous pouvez utiliser cet outil avec les applications HTML universelles Windows. L’outil **Réactivité de l’interface utilisateur HTML** peut être exécuté à partir de la fenêtre **Outils de diagnostic** (**Déboguer / Profileur de performances...**).  
  
## <a name="intellitrace"></a>IntelliTrace  
 ![DiagIntelliTrace](../profiling/media/diagintellitrace.png "DiagIntelliTrace")  
  
 [IntelliTrace](../debugger/intellitrace.md) vous permet d’inscrire des événements spécifiques, d’examiner les données dans la fenêtre **Variables locales** pendant les événements de débogueur et les appels de fonctions, ainsi que les erreurs de débogage difficiles à reproduire.  IntelliTrace est avant tout un outil de débogage, mais il procure aussi des informations qui peuvent être exploitées pour effectuer des recherches sur les performances. Vous pouvez utiliser cet outil dans Visual Studio Enterprise uniquement, avec les applications de bureau, les applications universelles Windows et les applications C# ASP.NET. Vous pouvez trouver IntelliTrace dans la fenêtre **Outils de diagnostic** pendant le débogage (**Déboguer / Windows / Afficher les outils de diagnostic**).  
  
## <a name="profiling-in-production"></a>Profilage en production  
 La méthode recommandée en matière de profilage en production consiste à profiler à partir de la [ligne de commande en utilisant vsperf.exe](../profiling/using-the-profiling-tools-from-the-command-line.md) pour collecter un profil d’UC. Pour bénéficier d’une prise en charge du profilage à distance dans Azure App Service, vous pouvez profiler via l’ [Explorateur de serveurs ou le portail Kudu](https://azure.microsoft.com/blog/remote-profiling-support-in-azure-app-service/).  
  
## <a name="which-tool-should-i-use"></a>Quel outil utiliser ?  
 Voici un tableau qui recense les différents outils proposés par Visual Studio, ainsi que les différents types de projet avec lesquels vous pouvez les utiliser :  
  
|Outil d’analyse des performances|Ordinateurs Windows|Universel Windows/Store|ASP.NET|  
|----------------------|---------------------|------------------------------|-------------|  
|[Utilisation de la mémoire](../profiling/memory-usage.md)|Oui|Oui|Non|  
|[Utilisation du processeur](../profiling/cpu-usage.md)|Oui|Oui|Azure App Service uniquement|  
|[Utilisation du GPU](../debugger/gpu-usage.md)|Oui|Oui|Non|  
|[Chronologie de l'application](../profiling/application-timeline.md)|Oui|Oui|Non|  
|[Conseils sur les performances](../profiling/perftips.md)|Oui|oui pour XAML, non pour HTML|Non|  
|[Explorateur de performances](../profiling/performance-explorer.md)|Oui|Non|Oui|  
|[IntelliTrace](../debugger/intellitrace.md)|.NET Enterprise uniquement|.NET Enterprise uniquement|.NET Enterprise uniquement|  
|[Réactivité de l’interface utilisateur HTML](../profiling/html-ui-responsiveness.md)|Non|oui pour HTML, non pour XAML|Non|  
|[Mémoire JavaScript](../profiling/javascript-memory.md)|Non|oui pour HTML, non pour XAML|Non|  
  
## <a name="see-also"></a>Voir aussi  
 [IDE Visual Studio](../ide/visual-studio-ide.md)
