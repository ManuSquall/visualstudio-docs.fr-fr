---
title: "Marques, vue | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.marks"
helpviewer_keywords: 
  - "rapports d'outils de profilage, affichage Marques"
  - "outils de profilage, affichage Marques"
ms.assetid: b2773344-8081-4116-85a1-58f770448f6a
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Marques, vue
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vue Marques affiche l'échantillonnage et les événements ETW qui ont été insérés dans l'application.  
  
 Les marques par défaut qui sont pré\-remplies dans le rapport signalent le démarrage et la fin du programme.  
  
 Les données de compteurs Windows issues des marques générées automatiquement sont également présentées dans cet affichage.  Pour plus d'informations, consultez [Comment : collecter les données des compteurs Windows](../profiling/how-to-collect-windows-counter-data.md).  
  
 Pour créer un filtre entre deux marques, sélectionnez les marques, cliquez avec le bouton droit sur **Ajouter un filtre aux marques** ou **Ajouter un filtre par horodatage**.  
  
 Le tableau suivant fournit les définitions de colonnes disponibles dans la vue Marques.  
  
 **ID de marque**  
 Identificateur unique de la marque de profilage.  
  
 **Nom de la marque**  
 Nom de l’événement.  
  
 **Horodateur**  
 Durée écoulée entre le début du profilage et le moment où l'évènement est enregistré.  
  
 Données du compteur de performance Windows  
 Lorsque les données du compteur de performance Windows sont collectées, les valeurs sont affichées dans une colonne portant le nom du compteur.  
  
## Voir aussi  
 [Vue d’ensemble des rapports d’outils de profilage](../profiling/performance-report-overview.md)   
 [\<PAVE\_OVER\> Comment : configurer des marques de profilage](../Topic/%3CPAVE_OVER%3E%20How%20to:%20Configure%20Profiling%20Marks.md)   
 [\<PAVE\_OVER\> Comment : insérer des marques dans un fichier de données du profileur](../Topic/%3CPAVE_OVER%3E%20How%20to:%20Insert%20Marks%20in%20a%20Profiler%20Data%20File.md)   
 [Comment : collecter les données des compteurs Windows](../profiling/how-to-collect-windows-counter-data.md)   
 [&#91;NIB&#93; Data Collection Control Window](http://msdn.microsoft.com/fr-fr/98d740d8-459f-4605-bf04-fb17aafaaa8f)