---
title: "Mode R&#233;sum&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.summary"
helpviewer_keywords: 
  - "rapports de performances, mode Résumé"
  - "rapports d'outils de profilage, mode Résumé"
  - "outils de profilage, mode Résumé"
  - "mode Résumé"
ms.assetid: 98a1eb71-bbf5-4ce7-8559-cdc29f082c4b
caps.latest.revision: 37
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 37
---
# Mode R&#233;sum&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le mode Résumé affiche des informations sur les fonctions ou objets les plus performants dans une exécution de profilage.  Cette vue fournit un graphique de chronologie et au moins deux listes des fonctions ou objets les plus coûteux selon les mesures de performance de la méthode de profilage.  Les données dans cette vue dépendent de la méthode de profilage utilisée \(échantillonnage, instrumentation ou concurrence\) et si l'allocation de mémoire .NET a été collectée.  
  
 Pour toutes les vues Résumé excepté la vue Résumé des données d'accès concurrentiel, le graphique de chronologie dans la vue Résumé affiche l'utilisation du processeur \(UC\) de l'application profilée par rapport à l'heure à laquelle le profilage a eu lieu.  
  
-   Si vous spécifiez un segment de temps sur le graphique, vous pouvez analyser de nouveau les données pour ce segment ou zoomez sur l'affichage de chronologie du segment que vous avez spécifié.  Pour plus d'informations, consultez [Comment : filtrer les vues de rapport à partir de la chronologie Résumé](../Topic/How%20to:%20Filter%20Report%20Views%20from%20the%20Summary%20Timeline.md).  
  
-   Vous pouvez cliquer sur une fonction dans une liste du mode Résumé pour ouvrir la page Informations relatives à la fonction.  Vous pouvez également cliquer avec le bouton droit sur la fonction pour d'autres options d'affichage.  
  
-   Pour modifier le nombre des éléments qui s'affichent dans les listes du mode Résumé, ouvrez le menu **Outils**, pointez sur **Options**, puis cliquez sur **Outils d'analyse des performances**.  Sous **Paramètres généraux**, modifiez le paramètre **Nombre de fonctions en mode Résumé**.  
  
## Liens de notification  
 Vous pouvez cliquer sur les liens de la liste Notification pour définir des options d'affichage pour le rapport.  La liste est à droite du graphique de chronologie.  
  
|||  
|-|-|  
|**Afficher le Code non\-Utilisateur**<br /><br /> **Afficher Uniquement mon code**|Non disponible pour le code natif ou pour les données de profilage collectées à l'aide de la méthode d'instrumentation.  Bascule entre l'affichage des données de code utilisateur uniquement \(**Afficher Uniquement mon code**\) et l'affichage des données de l'ensemble du code, notamment le code système \(**Afficher tout le code**\).  Par défaut, les données sont limitées au code utilisateur.  Pour modifier le paramètre, consultez [Procédure : filtrer les vues de rapport de façon à afficher Uniquement mon code](../Topic/How%20to:%20Filter%20Profiling%20Tools%20Report%20Views%20to%20Display%20Just%20My%20Code.md).|  
|**Afficher l'aide**|Affiche des avertissements de règle de performance dans la fenêtre **Liste d'erreurs**.  Pour plus d'informations, consultez [Utilisation des règles de performance pour analyser des données](../profiling/using-performance-rules-to-analyze-data.md).|  
  
## Rapport  
 Vous pouvez cliquer sur les liens de la liste Rapport pour ouvrir des vues différentes et comparer, enregistrer ou filtrer le rapport.  La liste est à droite du graphique de chronologie.  
  
|||  
|-|-|  
|**Afficher une arborescence des appels tronquée**|Affiche les chemins d'exécution les plus coûteux dans la vue Arborescence des appels.  Pour plus d’informations, consultez [Mode Arborescence des appels](../profiling/call-tree-view.md).|  
|**Afficher les hotlines**|Non disponible pour les données de profilage collectées à l'aide de la méthode d'instrumentation.  Affiche les lignes de code source les plus coûteuses dans la vue Lines.  Pour plus d’informations, consultez [Vue Lignes](../profiling/lines-view.md).|  
|**Comparer des rapports**|Affiche la boîte de dialogue **Sélectionner les fichiers d'analyse à des fins de comparaison** où vous pouvez spécifier un autre fichier de données de profilage à comparer au fichier actif.  Pour plus d’informations, consultez [Comparaison des fichiers de données des outils de profilage](../profiling/comparing-performance-data-files.md).|  
|**Exporter les données de rapport**|Affiche la boîte de dialogue **Exporter le rapport** où vous pouvez spécifier un ou plusieurs modes Rapport à enregistrer en tant que valeur séparée par des virgules \(.csv\) ou fichiers .xml.  Pour plus d’informations, consultez [How to: Export Profiling Tools Reports](http://msdn.microsoft.com/fr-fr/174b5bd3-df9b-4fd4-88d4-76032ab90451).|  
|**Enregistrer le rapport analysé**|Enregistre le fichier de données de profilage actuel en tant qu'un fichier .vsps, qui s'ouvre plus rapidement dans l'interface pour [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Pour plus d’informations, consultez [How to: Save Analyzed Profiling Data Files](http://msdn.microsoft.com/fr-fr/0340ddde-caf4-48ac-8af3-d15dcdade556).|  
|**Filtrer les données du rapport**|Affiche le volet du filtre du rapport du profilage où vous pouvez spécifier des critères pour restreindre les données dans le mode Rapport.  Pour plus d'informations, consultez [Filtre de la vue de rapport des outils de profilage](../profiling/performance-report-view-filter.md).|  
|**Plein écran**|Bascule en plein écran pour le mode Rapport.|  
  
## Voir aussi  
 [Mode Résumé](../profiling/summary-view-sampling-data.md)   
 [Mode Résumé](../profiling/summary-view-instrumentation-data.md)   
 [Mode Résumé](../profiling/summary-view-dotnet-memory-data.md)