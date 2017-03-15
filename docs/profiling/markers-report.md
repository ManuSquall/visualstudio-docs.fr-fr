---
title: "Rapport des marqueurs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.report.markers"
ms.assetid: 829ce099-172e-4c7e-bbd0-578b110c59bd
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Rapport des marqueurs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les Markers Report listent les marques dans le laps de temps affiché.  Le filtrage ou non du zoom, ou masquer des ruelles, peuvent faire apparaître des marques ou disparaître.  L'état contient les informations sur chaque jeton :  
  
-   Le moment où il a démarré, relatif au début de la trace.  
  
-   Sa durée.  La durée est zéro pour les balises et des messages car ils représentent un moment donné.  
  
-   L'ID du thread qui l'a créé.  
  
-   Le suivi d'événements pour le fournisseur windows \(ETW\) qui l'a créé.  
  
-   La série de jeton dont il a été écrit.  
  
-   La catégorie d'événements il appartient.  
  
-   Son niveau d'importance.  
  
-   Son type \(étendue, indicateur, ou message\).  
  
-   Une description globale de ce que il représente  
  
 Choisissez le bouton **Exporter** pour enregistrer le rapport sous la forme d'un fichier CSV.  Vous pouvez utiliser les données dans le fichier CSV avec d'autres applications ou outils.  
  
> [!NOTE]
>  L'état de balisage peut afficher 1 000 jetons.  Pour afficher tous les jetons, exportez le rapport circonstancié à un fichier CSV.