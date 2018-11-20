---
title: 'Comment : afficher les informations de Trace WPF | Microsoft Docs'
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
- WPF, debugging
- debugging, WPF
ms.assetid: be3c6859-06e1-459e-9fd0-46375b5f55ef
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a91d9f1f58a6905d50e14351bbbaf6fe732c60f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51771247"
---
# <a name="how-to-display-wpf-trace-information"></a>Comment : afficher les informations de trace WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] peut recevoir des informations de trace de débogage à partir d’applications WPF et afficher ces informations dans le **sortie** fenêtre. Pour afficher les informations de trace de débogage, le traçage WPF doit être activé.  
  
 Vous pouvez activer le traçage WPF dans votre fichier App.Config ou par programmation en utilisant la classe <xref:System.Diagnostics.PresentationTraceSources>. Un moyen plus simple pour activer le traçage WPF est à l’aide de la **Options** fenêtre. Le traçage WPF pour les applications Web n'est pas pris en charge.  
  
### <a name="to-enable-or-customize-wpf-trace-information"></a>Pour activer ou personnaliser les informations de trace WPF  
  
1.  Dans le menu **Outils**, sélectionnez **Options**.  
  
2.  Dans le **Options** boîte de dialogue, dans la zone située à gauche, ouvrez le **débogage** nœud.  
  
3.  Sous **débogage**, cliquez sur **fenêtre sortie**.  
  
4.  Sous **paramètres généraux de sortie**, sélectionnez **toute sortie du débogage**.  
  
5.  Dans la zone de droite, recherchez **paramètres de Trace WPF**.  
  
6.  Ouvrez le **paramètres de Trace WPF** nœud.  
  
7.  Sous **paramètres de Trace WPF**, cliquez sur la catégorie de paramètres que vous souhaitez activer (par exemple, **une liaison de données**).  
  
     Un contrôle de liste déroulante s’affiche à côté dans la colonne paramètres **une liaison de données** ou la catégorie que vous avez cliqué.  
  
8.  Cliquez sur la liste déroulante et sélectionnez le type d’informations de trace que vous souhaitez voir : **tous les**, **critique**, **erreur**, **avertissement**,  **Informations**, **Verbose**, ou **ActivityTracing**.  
  
     **Critique** Active le traçage des événements critiques uniquement.  
  
     **Erreur** Active le traçage des événements critiques et d’erreur.  
  
     **Avertissement** permet de tracer critique, erreur et d’événements d’avertissement.  
  
     **Informations** Active le traçage d’événements critique, erreur, avertissement et informations.  
  
     **Verbose** Active le traçage d’événements critique, erreur, avertissement, Information et Verbose.  
  
     **Suivi d’activités** Active le traçage d’événements arrêter, Démarrer, suspendre, transfert et reprendre.  
  
     Pour plus d'informations sur la signification de ces niveaux d'informations de trace, consultez <xref:System.Diagnostics.SourceLevels>.  
  
9. Cliquez sur **OK**.  
  
### <a name="to-disable-wpf-trace-information"></a>Pour désactiver les informations de trace WPF  
  
1.  Dans le menu **Outils**, sélectionnez **Options**.  
  
2.  Dans le **Options** boîte de dialogue, dans la zone située à gauche, ouvrez le **débogage** nœud.  
  
3.  Sous **débogage**, cliquez sur **fenêtre sortie**.  
  
4.  Dans la zone de droite, recherchez **paramètres de Trace WPF**.  
  
5.  Ouvrez le **paramètres de Trace WPF** nœud.  
  
6.  Sous **paramètres de Trace WPF**, cliquez sur la catégorie de paramètres que vous souhaitez activer (par exemple, **une liaison de données**).  
  
     Un contrôle de liste déroulante s’affiche à côté dans la colonne paramètres **une liaison de données** ou la catégorie que vous avez cliqué.  
  
7.  Cliquez sur la liste déroulante et sélectionnez **hors**.  
  
8.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage de WPF](../debugger/debugging-wpf.md)



