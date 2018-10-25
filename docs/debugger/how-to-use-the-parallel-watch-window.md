---
title: Définir un espion sur les Variables dans des Threads parallèles | Microsoft Docs
ms.custom: ''
ms.date: 04/25/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelwatch
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel watch window
ms.assetid: 28004d9b-420c-48f7-b80e-ab1519802558
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e9381479fdfa3d64f3504e947f49411b99d53e2d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49857950"
---
# <a name="set-a-watch-on-variables-in-parallel-threads-in-visual-studio"></a>Définir un espion sur les Variables dans des Threads parallèles dans Visual Studio
Dans la fenêtre Espion parallèle, vous pouvez simultanément afficher les valeurs qu'une expression contient sur plusieurs threads. Chaque ligne représente un thread s'exécutant dans une application, mais un thread peut être représenté dans plusieurs lignes. Plus spécifiquement, chaque ligne représente un appel de fonction dont la signature de la fonction correspond à la fonctionnalité sur le frame de pile actuel. Vous pouvez trier, réorganiser, supprimer et regrouper les éléments qui figurent dans les colonnes. Vous pouvez marquer ou supprimer l'indicateur, figer et libérer (reprendre) les threads. Les colonnes suivantes sont affichées dans le **espion parallèle** fenêtre :  
  
- La colonne d'indicateur, où vous pouvez marquer un thread auquel vous souhaitez apporter une attention spéciale.  
  
- La colonne de thread actuelle, dans lequel une flèche jaune indique que le thread actuel (une flèche verte avec extrémité recourbée indique qu’un thread non actuel a le contexte du débogueur actuel).  
  
- Une colonne configurable qui peut afficher l’ordinateur, le processus, la mosaïque, la tâche et le thread.  
  
  > [!TIP]
  >  Aux informations de tâche modifiés dans le **espion parallèle** fenêtre, vous devez tout d’abord ouvrir le **tâche** fenêtre.  
  
- L’essai à blanc *ajouter un espion* colonnes, dans laquelle vous pouvez entrer des expressions à surveiller.  
  
  [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-display-the-parallel-watch-window"></a>Pour afficher la fenêtre Espion parallèle  
  
1.  Définissez un point d'arrêt dans le code.  
  
2.  Dans la barre de menus, choisissez **Débogage**, puis **Démarrer le débogage**. Attendez que l'application atteigne le point d'arrêt.  
  
3.  Dans la barre de menus, choisissez **déboguer**, **Windows**, **espion parallèle**, puis choisissez une fenêtre Espion. Vous pouvez ouvrir quatre fenêtres maximum.  
  
### <a name="to-add-a-watch-expression"></a>Pour ajouter une expression espionne  
  
-   Sélectionnez une de l’essai à blanc *ajouter un espion* colonnes, puis entrez une expression espionne.  
  
### <a name="to-flag-or-unflag-a-thread"></a>Pour marquer ou supprimer l'indicateur d'un thread  
  
-   Sélectionnez la colonne d’indicateur pour la ligne (première colonne), ou ouvrez le menu contextuel pour le thread et choisissez **indicateur** ou **supprimer l’indicateur**.  
  
### <a name="to-display-only-flagged-threads"></a>Pour afficher seulement les threads avec indicateur  
  
-   Choisissez le **afficher uniquement avec indicateur** situé dans l’angle supérieur gauche de la **espion parallèle** fenêtre.  
  
### <a name="to-switch-to-another-thread"></a>Pour basculer vers un autre thread  
  
-   Double-cliquez sur la colonne de thread actuelle (la deuxième colonne). (Raccourci : sélectionnez la ligne et appuyez sur Entrée.)  
  
### <a name="to-sort-a-column"></a>Pour trier une colonne  
  
-   Sélectionnez le titre de la colonne.  
  
### <a name="to-group-threads"></a>Pour regrouper des threads  
  
-   Ouvrez le menu contextuel de la fenêtre Espion parallèle, choisissez **Group By**, puis choisissez l’élément de sous-menu approprié.  
  
### <a name="to-freeze-or-thaw-threads"></a>Pour figer ou libérer les threads  
  
-   Ouvrez le menu contextuel pour la ligne et choisissez **Figer** ou **libérer**.  
  
### <a name="to-export-the-data-in-the-parallel-watch-window"></a>Pour exporter les données dans la fenêtre Espion parallèle  
  
-   Choisissez le **ouvrir dans Excel** bouton, puis choisissez **ouvrir dans Excel** ou **exporter au format CSV**.  
  
### <a name="to-filter-by-a-boolean-expression"></a>Pour filtrer en fonction d'une expression booléenne  
  
-   Entrez une expression booléenne dans la **filtrer par Expression booléenne** boîte. Le débogueur évalue l'expression de chaque contexte de thread. Seules les lignes avec la valeur `true` sont affichées.  
  
## <a name="see-also"></a>Voir aussi  
 [Déboguer les Applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Comment : utiliser la fenêtre Threads GPU](../debugger/how-to-use-the-gpu-threads-window.md)   
 [Procédure pas-à-pas : débogage d’une application C++ AMP](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)