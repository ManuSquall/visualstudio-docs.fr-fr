---
title: 'Comment : utiliser la fenêtre Espion parallèle | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.parallelwatch
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, parallel watch window
ms.assetid: 28004d9b-420c-48f7-b80e-ab1519802558
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 88c4efe15e2afd3f4158b93cf8701109cd3902b8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504272"
---
# <a name="how-to-use-the-parallel-watch-window"></a>Comment : utiliser la fenêtre Espion parallèle
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [définissant un espion sur les Variables dans des Threads parallèles](https://docs.microsoft.com/visualstudio/debugger/how-to-use-the-parallel-watch-window).  
  
Dans la fenêtre Espion parallèle, vous pouvez simultanément afficher les valeurs qu'une expression contient sur plusieurs threads. Chaque ligne représente un thread s'exécutant dans une application, mais un thread peut être représenté dans plusieurs lignes. Plus spécifiquement, chaque ligne représente un appel de fonction dont la signature de la fonction correspond à la fonctionnalité sur le frame de pile actuel. Vous pouvez trier, réorganiser, supprimer et regrouper les éléments qui figurent dans les colonnes. Vous pouvez marquer ou supprimer l'indicateur, figer et libérer (reprendre) les threads. Les colonnes suivantes sont affichées dans le **espion parallèle** fenêtre :  
  
-   La colonne d'indicateur, où vous pouvez marquer un thread auquel vous souhaitez apporter une attention spéciale.  
  
-   La colonne de frame, dans laquelle une flèche indique le frame sélectionné.  
  
-   Une colonne configurable qui peut afficher l’ordinateur, le processus, la mosaïque, la tâche et le thread.  
  
    > [!TIP]
    >  Vous devez ouvrir le **tâches parallèles** fenêtre pour afficher les informations de tâche dans le **espion parallèle** fenêtre.  
  
-   Le  **\<ajouter un espion >** colonne, dans laquelle vous pouvez entrer des expressions à surveiller.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-display-the-parallel-watch-window"></a>Pour afficher la fenêtre Espion parallèle  
  
1.  Définissez un point d'arrêt dans le code.  
  
2.  Dans la barre de menus, choisissez **Débogage**, puis **Démarrer le débogage**. Attendez que l'application atteigne le point d'arrêt.  
  
3.  Dans la barre de menus, choisissez **déboguer**, **Windows**, **espion parallèle**, puis choisissez une fenêtre Espion. Vous pouvez ouvrir quatre fenêtres maximum.  
  
### <a name="to-add-a-watch-expression"></a>Pour ajouter une expression espionne  
  
-   Sélectionnez  **\<ajouter un espion >** , puis spécifiez une expression espionne.  
  
### <a name="to-flag-or-unflag-a-thread"></a>Pour marquer ou supprimer l'indicateur d'un thread  
  
-   Sélectionnez la colonne d’indicateur pour la ligne, ou ouvrez le menu contextuel pour le thread et choisissez **indicateur** ou **supprimer l’indicateur**.  
  
### <a name="to-display-only-flagged-threads"></a>Pour afficher seulement les threads avec indicateur  
  
-   Cliquez sur le bouton Afficher uniquement éléments avec indicateur dans le coin supérieur gauche de la **espion parallèle** fenêtre.  
  
### <a name="to-switch-frames"></a>Pour basculer vers les frames  
  
-   Double-cliquez sur la colonne de frame. (Raccourci : sélectionnez la ligne et appuyez sur Entrée.)  
  
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
 [Procédure pas-à-pas : débogage d’une application C++ AMP](http://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5)



