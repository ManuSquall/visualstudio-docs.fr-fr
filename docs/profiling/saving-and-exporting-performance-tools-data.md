---
title: "Enregistrement et exportation de donn&#233;es des outils d’analyse des performances | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "outils d’analyse des performances, enregistrement et exportation de rapports"
ms.assetid: 2e9b28fe-3ed2-4e1d-b9cb-0a5e384380b0
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Enregistrement et exportation de donn&#233;es des outils d’analyse des performances
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette rubrique décrit comment enregistrer et exporter des fichiers de données de performances.  
  
##  <a name="BKMK_Save_Profiler_Data_Files_As_Analyzed_Report_Files"></a> Comment : enregistrer des fichiers de données de performances en tant que fichiers de rapports analysés  
 Vous pouvez enregistrer des vues filtrées ou non filtrées de fichiers de données de profilage \(.vsp\) en tant que fichiers de rapports analysés \(.vsps\). Un fichier de rapport analysé peut être visualisé dans la fenêtre d’affichage des rapports et est considérablement plus petit que le fichier .vsp d’origine. Toutefois, vous ne pouvez pas appliquer de filtre aux données d’un fichier .vsps. Vous pouvez créer un fichier de rapport analysé à partir de l’Explorateur de performances sans ouvrir le fichier dans l’environnement de développement intégré \(IDE\), ou vous pouvez ouvrir et filtrer le fichier .vsp puis enregistrer les résultats.  
  
#### Pour enregistrer un rapport de performances analysé à partir de l’Explorateur de performances  
  
1.  Sous **rapports**, cliquez avec le bouton droit sur le fichier de données de profilage que vous souhaitez analyser, puis cliquez sur **Enregistrer l’analyse**.  
  
2.  Dans la boîte de dialogue **Enregistrer les données analysées**, spécifiez le répertoire et tapez le nom de fichier.  
  
3.  Cliquez sur **Enregistrer**.  
  
#### Pour enregistrer un rapport de performances analysé à partir de la fenêtre d’affichage des rapports  
  
1.  Ouvrez le fichier de données de profilage \(.vsp\) dans la fenêtre d’affichage des rapports.  
  
2.  \(Facultatif\) Appliquez un filtre aux données. Pour plus d'informations, consultez [Filtre de la vue de rapport des outils de profilage](../profiling/performance-report-view-filter.md).  
  
3.  Cliquez sur **Enregistrer l’analyse** dans la barre d’outils de la fenêtre d’affichage des rapports.  
  
4.  Dans la boîte de dialogue **Enregistrer les données analysées**, spécifiez le répertoire et tapez le nom de fichier.  
  
5.  Cliquez sur **Enregistrer**.  
  
## Comment : exporter des rapports d’outils de profilage pour un fichier .xml ou .csv  
 Vous pouvez exporter une ou plusieurs vues de rapports à partir d’un fichier .vsp ou d’un fichier de données de profilage .vsps sous forme de fichier délimité par des virgules ou de fichier XML. Vous pouvez filtrer les données de la fenêtre d’affichage des rapports avant d’exporter, ou exporter des vues de rapport du fichier de données entier à partir de la fenêtre **Explorateur de performances**.  
  
> [!NOTE]
>  Vous pouvez également copier et coller des lignes sélectionnées à partir de la fenêtre d’affichage des rapports en tant que valeurs séparées par des tabulations.  
  
#### Pour exporter des rapports de performances à partir de la fenêtre Explorateur de performances  
  
1.  Dans l’**Explorateur de performances**, sélectionnez le rapport, cliquez avec le bouton droit et sélectionnez **Exporter**.  
  
     La boîte de dialogue **Exporter le rapport** s’affiche.  
  
2.  Sélectionnez les vues de rapport à exporter.  
  
3.  Sous **Préfixer les rapports avec**, spécifiez le préfixe que vous souhaitez ajouter au nom du rapport.  
  
4.  Sous **Emplacement du rapport exporté**, spécifiez le répertoire.  
  
5.  Sous **Format du rapport exporté**, sélectionnez \(délimité par des virgules\) \(\*.csv\) ou Données XML \(\*.xml\).  
  
6.  Cliquez sur **Exporter**.  
  
     Chaque vue de rapport est enregistrée dans un fichier distinct nommé \<préfixe\>\_\<nom\_vue\_rapport\>.\<csv&#124;xml\>  
  
#### Pour exporter des rapports de performances à partir de la fenêtre d’affichage des rapports  
  
1.  Ouvrez le fichier .vsp dans la fenêtre d’affichage des rapports.  
  
2.  \(Facultatif\) Appliquez un filtre aux données. Pour plus d'informations, consultez [Filtre de la vue de rapport des outils de profilage](../profiling/performance-report-view-filter.md).  
  
3.  Cliquez sur **Exporter le rapport** dans la barre d’outils de la fenêtre d’affichage des rapports.  
  
4.  Sélectionnez les vues de rapport à exporter.  
  
5.  Sous **Préfixer les rapports avec**, spécifiez le préfixe que vous souhaitez ajouter au nom du rapport.  
  
6.  Sous **Emplacement du rapport exporté**, spécifiez le répertoire.  
  
7.  Sous **Format du rapport exporté**, sélectionnez \(délimité par des virgules\) \(\*.csv\) ou Données XML \(\*.xml\).  
  
8.  Cliquez sur **Exporter**.  
  
     Chaque vue de rapport est enregistrée dans un fichier distinct nommé \<préfixe\>\_\<nom\_vue\_rapport\>.\<csv&#124;xml\>  
  
## Voir aussi  
 [Utilisation des outils de profilage](../profiling/performance-explorer.md)   
 [Analyse des données des outils de profilage](../profiling/analyzing-performance-tools-data.md)   
 [Comparaison des fichiers de données des outils de profilage](../profiling/comparing-performance-data-files.md)   
 [VSPerfReport](../profiling/vsperfreport.md)