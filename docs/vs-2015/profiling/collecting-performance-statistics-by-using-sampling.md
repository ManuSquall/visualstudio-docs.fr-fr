---
title: Collecte de statistiques de performance à l’aide de l’échantillonnage | Microsoft Docs
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
- Profiling Tools,sampling
- sampling profiling method
ms.assetid: 8e36361b-bb3d-40c6-b286-0e68c0ecb915
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a67c6542c2b838de7e80ee23588847cc15c15292
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755273"
---
# <a name="collecting-performance-statistics-by-using-sampling"></a>Collecte de statistiques de performance à l’aide de l’échantillonnage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Par défaut, la méthode d’échantillonnage des outils de profilage de [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] collecte les informations de profilage tous les 10 000 000 cycles de processeur (soit environ tous les centièmes de seconde sur un ordinateur de 1 GHz). La méthode d’échantillonnage est utile pour détecter les problèmes d’utilisation du processeur. De plus, elle est conseillée pour commencer la plupart des examens de performances.  
  
 **Spécifications**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
>  Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications Windows Store demandent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Vous pouvez spécifier la méthode d’échantillonnage à l’aide de l’une des procédures suivantes :  
  
-   Dans la première page de l’Assistant Profilage, cliquez sur **Échantillonnage de l’UC (recommandé)**.  
  
-   Dans la barre d’outils de **l’Explorateur de performances**, dans la liste **Méthode**, cliquez sur **Échantillonnage**.  
  
-   Dans la page **Général** de la boîte de dialogue Propriétés de la session de performance, cliquez sur **Échantillonnage**.  
  
## <a name="common-tasks"></a>Tâches courantes  
 Vous pouvez spécifier des options supplémentaires dans la boîte de dialogue des _pages de propriétés_**session de performance** . Pour ouvrir la boîte de dialogue :  
  
- Dans l’ **Explorateur de performances**, cliquez avec le bouton droit sur le nom de la session de performance, puis cliquez sur **Propriétés**.  
  
  Les tâches du tableau suivant décrivent les options que vous pouvez spécifier dans la boîte de dialogue _Session de performance_**Pages de propriétés** quand vous effectuez un profilage à l’aide de la méthode d’échantillonnage.  
  
|Tâche|Contenu associé|  
|----------|---------------------|  
|Dans la page **Général**, ajoutez l’allocation de mémoire .NET et la collecte de données de durée de vie, puis spécifiez les détails d’affectation de noms pour le fichier de données de profilage (.vsp) généré.|-   [Collecte de données liées à l’allocation et à la durée de vie de la mémoire .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Guide pratique pour définir les options de nom de fichier de données de profilage](../profiling/how-to-set-performance-data-file-name-options.md)|  
|Dans la page **Échantillonnage**, modifiez le taux d’échantillonnage, remplacez l’événement d’échantillonnage de cycle d’horloge du processeur par un événement de compteur de performances du processeur, ou modifiez les deux.|-   [Guide pratique pour choisir des événements d’échantillonnage](../profiling/how-to-choose-sampling-events.md)|  
|Si votre solution de code contient plusieurs projets .exe, dans la page **Lancer**, spécifiez l’application à démarrer, ainsi que l’ordre de démarrage.|-   [Collecte de données d’interaction de couche](../profiling/collecting-tier-interaction-data.md)|  
|Dans la page **Interaction de couche**, ajoutez les informations d’appel ADO.NET aux données collectées lors de l’exécution du profilage.|-   [Collecte de données d’interaction de couche](../profiling/collecting-tier-interaction-data.md)|  
|Dans la page **Événements Windows**, spécifiez un ou plusieurs événements de suivi d’événements pour Windows (ETW) à collecter avec les données d’échantillonnage.|-   [Guide pratique pour collecter les données de suivi d’événements pour Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|  
|Dans la page **Compteurs Windows** , spécifiez un ou plusieurs compteurs de performance de système d’exploitation à ajouter aux données de profilage en tant que marques.|-   [Guide pratique pour collecter les données des compteurs Windows](../profiling/how-to-collect-windows-counter-data.md)|  
|Dans la page **Avancé**, spécifiez la version du runtime .NET Framework à profiler si vos modules d’application utilisent plusieurs versions. Par défaut, la première version chargée est profilée.|-   [Guide pratique pour spécifier le runtime .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|



