---
title: "Collecte de statistiques de performance &#224; l’aide de l’&#233;chantillonnage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Outils de profilage, échantillonner"
  - "méthode de profilage par échantillonnage"
ms.assetid: 8e36361b-bb3d-40c6-b286-0e68c0ecb915
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# Collecte de statistiques de performance &#224; l’aide de l’&#233;chantillonnage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Par défaut, la méthode d'échantillonnage des outils de profilage [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] collecte les informations de profilage tous les 10 000 000 cycles de processeur \(soit environ tous les centièmes de seconde sur un ordinateur cadencé à 1 GHz\).  La méthode d'échantillonnage est utile pour détecter les problèmes d'utilisation du processeur et est suggérée pour commencer la plupart des examens de performances.  
  
 **Conditions requises**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
> [!NOTE]
>  Les fonctionnalités de sécurité renforcée dans Windows 8 et Windows Server 2012 nécessitaient d'importantes modifications de la manière dont le profileur Visual Studio collecte des données sur ces plateformes.  Les applications Windows Store requièrent également de nouvelles techniques de collecte.  Consultez [Profilage d'applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Vous pouvez spécifier la méthode d'échantillonnage à l'aide d'une des procédures suivantes :  
  
-   Sur la première page de l'Assistant de profilage, cliquez sur **Échantillonnage de l'UC \(recommandé\)**.  
  
-   Dans la barre d'outils **Explorateur de performances**, dans la liste **Méthode**, cliquez sur **Échantillonnage**.  
  
-   Sur la page **Général** de la boîte de dialogue des propriétés de la session de performance, cliquez sur **Échantillonnage**.  
  
## Tâches courantes  
 Spécifiez des options supplémentaires dans la boîte de dialogue **Pages de propriétés** de la *Performance Session*.  Pour ouvrir cette boîte de dialogue :  
  
-   Dans l'**Explorateur de performances**, cliquez avec le bouton droit sur le nom de la session de performance, puis cliquez sur **Propriétés**.  
  
 Les tâches du tableau suivant décrivent les options que vous pouvez spécifier dans la boîte de dialogue **Pages de propriétés** de *Performance Session* lorsque vous effectuez un profilage à l'aide de la méthode d'échantillonnage.  
  
|Tâche|Contenu associé|  
|-----------|---------------------|  
|Sur la page **Général**, ajoutez l'allocation de mémoire .NET et la collecte de données sur la durée de vie, puis spécifiez les détails d'attribution de nom du fichier de données de profilage \(.vsp\) généré.|-   [Collecte de données liées à l’allocation et à la durée de vie de la mémoire .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Comment : définir les options de nom de fichier de données de profilage](../profiling/how-to-set-performance-data-file-name-options.md)|  
|Sur la page **Échantillonnage**, modifiez le taux d'échantillonnage, modifiez l'événement d'échantillonnage pour utiliser un autre compteur de performance du processeur plutôt que les cycles d'horloge du processeur, ou modifiez les deux.|-   [Comment : choisir des événements d’échantillonnage](../Topic/How%20to:%20Choose%20Sampling%20Events.md)|  
|Sur la page **Lancer**, spécifiez l'application à démarrer et l'ordre de démarrage si votre solution de code comprend plusieurs projets .exe.|-   [Collecte de données d’interaction de couche](../profiling/collecting-tier-interaction-data.md)|  
|Sur la page **Interactions de couche**, ajoutez les informations d'appel ADO.NET aux données collectées lors de l'exécution du profilage.|-   [Collecte de données d’interaction de couche](../profiling/collecting-tier-interaction-data.md)|  
|Sur la page **Événements Windows**, spécifiez un ou plusieurs événements de Suivi d'événements pour Windows \(ETW\) à collecter avec les données d'échantillonnage.|-   [Comment : collecter les données de suivi d’événements pour Windows \(ETW\)](../Topic/How%20to:%20Collect%20Event%20Tracing%20for%20Windows%20\(ETW\)%20Data.md)|  
|Dans la page **Compteurs Windows**, spécifiez un ou plusieurs compteurs de performance de système d'exploitation à ajouter aux données de profilage en tant que marques.|-   [Comment : collecter les données des compteurs Windows](../profiling/how-to-collect-windows-counter-data.md)|  
|Sur la page **Avancé**, spécifiez la version du runtime .NET Framework à profiler si vos modules d'application utilisent plusieurs versions.  Par défaut, la première version chargée est profilée.|-   [Comment : spécifier le runtime .NET Framework à profiler dans les scénarios côte à côte](../Topic/How%20to:%20Specify%20the%20.NET%20Framework%20Runtime.md)|