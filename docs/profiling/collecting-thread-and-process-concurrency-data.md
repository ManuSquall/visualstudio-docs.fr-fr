---
title: "Collecte de donn&#233;es de concurrence de threads et de processus | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "méthode de profilage d’accès concurrentiel"
  - "outils de profilage, méthode de concurrence"
ms.assetid: fa03d381-a9ee-408c-876d-05111e29225b
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Collecte de donn&#233;es de concurrence de threads et de processus
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La méthode de profilage d'accès concurrentiel des outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vous permet de collecter les données de conflit de ressources qui incluent des informations sur chaque événement de synchronisation qui provoque qu'une fonction dans l'application profilée attende l'accès à une ressource.  
  
 **Conditions requises**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Vous pouvez spécifier la méthode de profilage de concurrence à l'aide de l'une des procédures suivantes :  
  
-   Sur la première page de l'Assistant de Profilage, cliquer sur **Concurrence**  
  
-   Sur la page **Général** de la boîte de dialogue des propriétés de la session de performance, cliquer sur **Concurrence**.  
  
-   Dans la barre d'outils **Explorateur de performances**, dans la liste **Méthode**, cliquez sur **Concurrence**.  
  
## Tâches courantes  
 Spécifiez des options supplémentaires dans la boîte de dialogue **Pages de propriétés** de la *Performance Session*.  Pour ouvrir cette boîte de dialogue :  
  
-   Dans l'**Explorateur de performances**, cliquez avec le bouton droit sur le nom de la session de performance, puis cliquez sur **Propriétés**.  
  
 Les tâches du tableau suivant décrivent les options que vous pouvez spécifier dans la boîte de dialogue **Property Pages** de *Performance Session* lorsque vous effectuez un profilage à l'aide de la méthode de concurrence.  
  
|Tâche|Contenu associé|  
|-----------|---------------------|  
|Sur la page **Général**, spécifiez les détails d'attribution de nom pour le fichier de données de profilage généré \(.vsp\).|-   [Comment : définir les options de nom de fichier de données de profilage](../profiling/how-to-set-performance-data-file-name-options.md)|  
|Sur la page **Lancement**, spécifiez l'application à démarrer si votre solution de code comporte plusieurs projets .exe.|-   [Comment : spécifier le binaire à démarrer](../profiling/how-to-specify-the-binary-to-start.md)|  
|Dans la page **Interactions de couche**, ajoutez les données d'appel ADO.NET à l'exécution du profilage.|-   [Collecte de données d’interaction de couche](../profiling/collecting-tier-interaction-data.md)|  
|Dans la page **Compteurs Windows**, spécifiez un ou plusieurs compteurs de performance de système d'exploitation à ajouter aux données de profilage en tant que marques.|-   [Comment : collecter les données des compteurs Windows](../profiling/how-to-collect-windows-counter-data.md)|  
|Sur la page **Avancé**, spécifiez la version du runtime .NET Framework à profiler si vos modules d'application utilisent plusieurs versions.  Par défaut, la première version chargée est profilée.|-   [Comment : spécifier le runtime .NET Framework à profiler dans les scénarios côte à côte](../Topic/How%20to:%20Specify%20the%20.NET%20Framework%20Runtime.md)|