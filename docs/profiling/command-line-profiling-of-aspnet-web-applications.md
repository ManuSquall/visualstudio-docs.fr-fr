---
title: "Profilage d’applications web ASP.NET &#224; partir de la ligne de commande | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "profiler des applications ASP.NET"
  - "outils de profilage, applications ASP.NET"
ms.assetid: 897c00d5-5767-433b-a960-4a29c6023ede
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Profilage d’applications web ASP.NET &#224; partir de la ligne de commande
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette section décrit les procédures et les options pour la collecte des données de performances pour les applications Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] en utilisant les outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] à partir de la ligne de commande.  
  
> [!NOTE]
>  Les fonctionnalités de sécurité renforcée dans windows 8 et Windows Server 2012 requises des modifications significatives de la manière que le profileur Visual Studio collecte des données sur ces plateformes.  Les applications de mémoire de fenêtres requièrent également de nouvelles techniques de collection.  Consultez [Profilage d'applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## Tâches courantes  
  
|Tâche|Contenu associé|  
|-----------|---------------------|  
|**Collecter facilement des données de profilage ASP.NET de base :** utilisez l'outil **VSPerfASPNETCmd** pour collecter des données d'échantillonnage, d'instrumentation, de mémoire .NET, de conflit ou sur l'interaction entre les couches sans la configuration requise et les redémarrages des services IIS \(Internet Information Services\) nécessaires pour **VSPerfCmd**.  **VSPerfASPNETCmd** ne vous permet pas de collecter des données supplémentaires ou de contrôler la collecte des données. **Note:**  **VSPerfASPNETCmd** est l'outil par défaut à utiliser pour que le profileur autonome profile des sites Web ASP.NET.|-   [Profilage de site Web rapide avec VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)|  
|**Collecter des statistiques de l'application :** utilisez la méthode d'échantillonnage pour collecter des statistiques de performance.  Les données d'échantillonnage sont utiles pour analyser les problèmes d'utilisation de l'UC et pour comprendre les caractéristiques de performance générales d'une application.|-   [Collecte de statistiques d’applications en utilisant l’échantillonnage](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Collecter des données de minutage détaillées :** utilisez la méthode d'instrumentation pour collecter des informations de minutage détaillées.  Les données d'instrumentation sont utiles pour analyser les problèmes d'E\/S et pour l'analyse affinée des scénarios d'application.|-   [Collecte de données de temporisation détaillées à l'aide de l'instrumentation](../profiling/collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line.md)|  
|**Collecter des données de la mémoire .NET :** utilisez l'échantillonnage ou l'instrumentation pour collecter des données d'allocation de mémoire .NET qui indiquent la taille et le nombre d'objets alloués.  Vous pouvez également collecter des données de durée de vie d'objet qui indiquent la taille et le nombre d'objets qui sont récupérés dans chaque génération de garbage collection.|-   [Collecte des données de mémoire](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**Collecter des données de concurrence :** utilisez la méthode de concurrence pour collecter des données de conflit de ressources. **Note:**  La collecte de données d'activité de thread et de données de visualisation n'est pas prise en charge pour les applications Web.|-   [Collecte de données concurrentielles](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
|**Ajouter des données sur l'interaction entre les couches :** vous pouvez ajouter des données de performances sur les appels [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] synchrones que l'application Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] passe à une base de données Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)].|-   [Collecte de données d’interaction de couche](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## Tâches connexes  
  
|Tâche|Contenu associé|  
|-----------|---------------------|  
|**Profiler les applications autonomes \(clientes\)**|-   [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**Profiler des services**|-   [Profilage de services](../profiling/command-line-profiling-of-services.md)|