---
title: "Comment&#160;: utiliser la fen&#234;tre Espion parall&#232;le | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.parallelwatch"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "débogueur, Espion parallèle (fenêtre)"
ms.assetid: 28004d9b-420c-48f7-b80e-ab1519802558
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Comment&#160;: utiliser la fen&#234;tre Espion parall&#232;le
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dans la fenêtre Espion parallèle, vous pouvez simultanément afficher les valeurs qu'une expression contient sur plusieurs threads.  Chaque ligne représente un thread s'exécutant dans une application, mais un thread peut être représenté dans plusieurs lignes.  Plus spécifiquement, chaque ligne représente un appel de fonction dont la signature de la fonction correspond à la fonctionnalité sur le frame de pile actuel.  Vous pouvez trier, réorganiser, supprimer et regrouper les éléments qui figurent dans les colonnes.  Vous pouvez marquer ou supprimer l'indicateur, figer et libérer \(reprendre\) les threads.  Les colonnes suivantes sont affichées dans la fenêtre **Espion parallèle** :  
  
-   La colonne d'indicateur, où vous pouvez marquer un thread auquel vous souhaitez apporter une attention spéciale.  
  
-   La colonne de frame, dans laquelle une flèche indique le frame sélectionné.  
  
-   Une colonne configurable qui peut afficher l'ordinateur, le processus, la mosaïque, la tâche et le thread.  
  
    > [!TIP]
    >  Vous devez ouvrir la fenêtre **Tâche parallèle** pour afficher les informations de tâche dans la fenêtre **Espion parallèle**.  
  
-   La colonne **\<Ajouter un espion\>**, dans laquelle vous pouvez écrire des expressions à surveiller.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### Pour afficher la fenêtre Espion parallèle  
  
1.  Définissez un point d'arrêt dans le code.  
  
2.  Dans la barre de menus, sélectionnez **Débogage**, puis **Démarrer le débogage**.  Attendez que l'application atteigne le point d'arrêt.  
  
3.  Dans la barre de menus, sélectionnez **Déboguer**, **Fenêtres**, **Espion parallèle**, puis sélectionnez une fenêtre Espion.  Vous pouvez ouvrir quatre fenêtres maximum.  
  
### Pour ajouter une expression espionne  
  
-   Sélectionnez **\<Ajouter un espion\>**, puis spécifiez une expression espionne.  
  
### Pour marquer ou supprimer l'indicateur d'un thread  
  
-   Sélectionnez la colonne d'indicateur de la ligne, ou ouvrez le menu contextuel du thread et choisissez **Marquer** ou **Supprimer l'indicateur**.  
  
### Pour afficher seulement les threads avec indicateur  
  
-   Sélectionnez le bouton Afficher uniquement éléments avec indicateur dans l'angle supérieur gauche de la fenêtre **Espion parallèle**.  
  
### Pour basculer vers les frames  
  
-   Double\-cliquez sur la colonne de frame. \(Raccourci : sélectionnez la ligne et appuyez sur Entrée.\)  
  
### Pour trier une colonne  
  
-   Sélectionnez le titre de la colonne.  
  
### Pour regrouper des threads  
  
-   Ouvrez le menu contextuel de la fenêtre Espion parallèle, choisissez **Grouper par**, puis choisissez l'élément de sous\-menu approprié.  
  
### Pour figer ou libérer les threads  
  
-   Ouvrez le menu contextuel de la ligne par défaut et choisissez **Figer** ou **Libérer**.  
  
### Pour exporter les données dans la fenêtre Espion parallèle  
  
-   Cliquez sur le bouton **Ouvrir dans Excel**, puis sélectionnez **Ouvrir dans Excel** ou **Exporter au format CSV**.  
  
### Pour filtrer en fonction d'une expression booléenne  
  
-   Entrez une expression booléenne dans la zone **Filtrer par expression booléenne**.  Le débogueur évalue l'expression de chaque contexte de thread.  Seules les lignes avec la valeur `true` sont affichées.  
  
## Voir aussi  
 [Déboguer les applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Comment : utiliser la fenêtre Threads GPU](../Topic/How%20to:%20Use%20the%20GPU%20Threads%20Window.md)   
 [Procédure pas\-à\-pas : débogage d’une application C\+\+ AMP](../Topic/Walkthrough:%20Debugging%20a%20C++%20AMP%20Application.md)