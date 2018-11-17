---
title: 'Comment : ajouter et supprimer les indicateurs des Threads | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- treads, switching [debugging]
ms.assetid: 952d579d-6911-413e-b3e5-54e7e797e70c
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5816007476da56321e58182e636b54a5a5697994
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817488"
---
# <a name="how-to-flag-and-unflag-threads"></a>Comment : ajouter et supprimer les indicateurs des threads
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez signaler un thread auquel vous souhaitez accorder une attention particulière en le marquant avec une icône dans le **Threads**, **piles parallèles**, **espion parallèle**, et **GPU Threads** windows. Cette icône vous aide, ainsi que d'autres, à distinguer les threads avec indicateur des autres threads.  
  
 Threads avec indicateur bénéficient d’un traitement spécial dans le **Thread** liste sur le **emplacement de débogage** barre d’outils. Cette liste peut contenir tous les threads ou uniquement les threads avec indicateur. Lorsque vous signalez un thread, le **Thread** liste affiche automatiquement pour afficher uniquement les threads avec indicateur, mais vous pouvez afficher tous les threads comme il convient.  
  
### <a name="to-flag-or-unflag-a-thread-by-using-the-threads-window"></a>Pour ajouter ou supprimer l'indicateur d'un thread à l'aide de la fenêtre Threads  
  
-   Dans le **Threads** fenêtre, recherchez le thread qui vous intéresse et cliquez sur l’icône d’indicateur pour activer ou désactiver l’indicateur.  
  
### <a name="to-unflag-all-threads"></a>Pour supprimer tous les indicateurs de thread  
  
-   Dans le **Threads** fenêtre, avec le bouton droit n’importe quel thread, puis cliquez sur **supprimer l’indicateur de tous les Threads**.  
  
### <a name="to-display-only-flagged-threads"></a>Pour afficher seulement les threads avec indicateur  
  
-   Cliquez sur le bouton indicateur dans la fenêtre de débogage.  
  
### <a name="to-flag-just-my-code"></a>Pour signaler Uniquement mon code  
  
1.  Dans la barre d’outils en haut de la **Threads** fenêtre, cliquez sur l’icône d’indicateur.  
  
2.  Dans la liste déroulante, cliquez sur **signaler uniquement mon Code**.  
  
### <a name="to-flag-threads-that-are-associated-with-selected-modules"></a>Pour signaler des threads associés aux modules sélectionnés  
  
1.  Dans la barre d’outils de la **Threads** fenêtre, cliquez sur l’icône d’indicateur.  
  
2.  Dans la liste déroulante, cliquez sur **signaler la sélection de Module personnalisé**.  
  
3.  Dans le **sélectionner les Modules** boîte de dialogue, sélectionnez les modules que vous souhaitez.  
  
4.  (Facultatif) Dans le **recherche** , tapez une chaîne à rechercher des modules spécifiques.  
  
5.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Déboguer les Applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Procédure pas à pas : débogage d’une application multithread](../debugger/walkthrough-debugging-a-multithreaded-application.md)



