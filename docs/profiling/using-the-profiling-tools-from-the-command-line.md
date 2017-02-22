---
title: "Utilisation des outils de profilage &#224; partir de la ligne de commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ligne de commande, outils d’analyse des performances"
  - "outils en ligne de commande, outils d’analyse des performances"
  - "outils de profilage, ligne de commande"
  - "outils, ligne de commande"
  - "ligne de commande, outils"
ms.assetid: 6593fa82-181e-4009-a0ed-02aa24c2c063
caps.latest.revision: 35
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 35
---
# Utilisation des outils de profilage &#224; partir de la ligne de commande
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez utiliser les outils en ligne de commande des outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour profiler des applications depuis l'invite de commandes et automatiser le profilage à l'aide de fichiers de commandes et de scripts.  Vous pouvez également générer des fichiers de rapport depuis une invite de commandes.  Vous pouvez utiliser le profileur autonome léger pour collecter des données sur des ordinateurs où [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] n'est pas installé.  
  
> [!NOTE]
>  Les fonctionnalités de sécurité renforcée dans windows 8 et Windows Server 2012 requises des modifications significatives de la manière que le profileur Visual Studio collecte des données sur ces plateformes.  Les applications de mémoire de fenêtres requièrent également de nouvelles techniques de collection.  Consultez [Profilage d'applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## Tâches courantes  
  
|Tâche|Contenu associé|  
|-----------|---------------------|  
|**Définir l'emplacement de symboles :** pour afficher les noms de fonctions et les paramètres, le profileur doit avoir accès aux fichiers de symboles \(.pdb\) des binaires profilés.  Ces fichiers doivent inclure les fichiers de symboles pour le système d'exploitation Microsoft et les applications que vous souhaitez intégrer à votre analyse.  Vous pouvez utiliser le serveur de symboles public Microsoft pour vous assurer que vous disposez des fichiers .pdb corrects pour les binaires Microsoft.|-   [Comment : spécifier les emplacements du fichier de symboles à partir de la ligne de commande](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md)|  
|**Profiler votre application :**  les outils en ligne de commande et les options que vous utilisez pour profiler une application cible dépendent du type de l'application, de la méthode de profilage et du type de la cible \(application managée ou native\).|-   [Utilisation de méthodes de profilage à partir de la ligne de commande](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)<br />-   [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)<br />-   [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)<br />-   [Profilage de services](../profiling/command-line-profiling-of-services.md)|  
|**Créer des rapports .xml et .csv :** un profilage depuis l'invite de commandes crée des fichiers de données que vous pouvez afficher dans l'interface de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Vous pouvez également générer des fichiers .xml ou .csv des données à l'aide de l'outil en ligne de commande VSPerfReport.|-   [Création de rapports de profileur à partir de la ligne de commande](../profiling/creating-profiler-reports-from-the-command-line.md)<br />-   [VSPerfReport](../profiling/vsperfreport.md)|  
|**Profiler le code sur des ordinateurs sans Visual Studio :** vous pouvez utiliser le profileur autonome des outils de profilage afin de collecter des données pour les applications sur des ordinateurs où [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] n'est pas installé.|-   [Comment : installer le profileur autonome](../profiling/how-to-install-the-stand-alone-profiler.md)|  
  
## Référence  
 [Référence d'outils de profilage de ligne de commande](../profiling/command-line-profiling-tools-reference.md)  
  
## Voir aussi  
 [Utilisation des outils de profilage](../profiling/performance-explorer.md)