---
title: 'Comment : baliser et supprimer l’indicateur de threads | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: b6d6a49dd9b90172686a90d92e6b630dd70b5cf0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189441"
---
# <a name="how-to-flag-and-unflag-threads"></a>Comment : ajouter et supprimer les indicateurs des threads
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez marquer un thread auquel vous souhaitez accorder une attention particulière en le marquant avec une icône dans les fenêtres **Threads**, **Piles parallèles**, **Espion parallèle**et **Threads GPU** . Cette icône vous aide, ainsi que d'autres, à distinguer les threads avec indicateur des autres threads.  
  
 Les threads avec indicateur reçoivent également un traitement spécial dans la liste des **Threads** de la barre d’outils **emplacement de débogage** . Cette liste peut contenir tous les threads ou uniquement les threads avec indicateur. Quand vous marquez un thread, la liste des **Threads** bascule automatiquement pour afficher uniquement les threads avec indicateur, mais vous pouvez le basculer pour afficher tous les threads comme il convient.  
  
### <a name="to-flag-or-unflag-a-thread-by-using-the-threads-window"></a>Pour ajouter ou supprimer l'indicateur d'un thread à l'aide de la fenêtre Threads  
  
- Dans la fenêtre **Threads** , recherchez le thread qui vous intéresse, puis cliquez sur l’icône d’indicateur pour activer ou désactiver l’indicateur.  
  
### <a name="to-unflag-all-threads"></a>Pour supprimer tous les indicateurs de thread  
  
- Dans la fenêtre **Threads**, cliquez avec le bouton droit sur un thread, puis cliquez sur **Tous les threads sans indicateur**.  
  
### <a name="to-display-only-flagged-threads"></a>Pour afficher seulement les threads avec indicateur  
  
- Cliquez sur le bouton indicateur dans la fenêtre de débogage.  
  
### <a name="to-flag-just-my-code"></a>Pour signaler Uniquement mon code  
  
1. Dans la barre d’outils en haut de la fenêtre **Threads**, cliquez sur l’icône d’indicateur.  
  
2. Dans la liste déroulante, cliquez sur **Signaler uniquement mon code**.  
  
### <a name="to-flag-threads-that-are-associated-with-selected-modules"></a>Pour signaler des threads associés aux modules sélectionnés  
  
1. Dans la barre d’outils de la fenêtre **Threads**, cliquez sur l’icône d’indicateur.  
  
2. Dans la liste déroulante, cliquez sur **Signaler la sélection de modules personnalisés**.  
  
3. Dans la boîte de dialogue **Sélectionner les modules**, sélectionnez les modules souhaités.  
  
4. (Facultatif) Dans la zone **Rechercher**, saisissez une chaîne pour rechercher des modules spécifiques.  
  
5. Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Déboguer des applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Procédure pas à pas : débogage d’une application multithread](../debugger/walkthrough-debugging-a-multithreaded-application.md)
