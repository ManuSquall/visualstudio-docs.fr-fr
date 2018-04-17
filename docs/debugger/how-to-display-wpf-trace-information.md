---
title: 'Comment : afficher des informations de Trace WPF | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: be3c6859-06e1-459e-9fd0-46375b5f55ef
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3584ae0d1dcd0e33bfa08954a2ad376485b6b71e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-display-wpf-trace-information"></a>Comment : afficher les informations de trace WPF
[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] peut recevoir des informations de trace de débogage à partir d’applications WPF et afficher ces informations dans le **sortie** fenêtre. Pour afficher les informations de trace de débogage, le traçage WPF doit être activé.  
  
 Vous pouvez activer le traçage WPF dans votre fichier App.Config ou par programmation en utilisant la classe <xref:System.Diagnostics.PresentationTraceSources>. Un moyen plus simple pour activer le traçage WPF est à l’aide de la **Options** fenêtre. Le traçage WPF pour les applications Web n'est pas pris en charge.  
  
### <a name="to-enable-or-customize-wpf-trace-information"></a>Pour activer ou personnaliser les informations de trace WPF  
  
1.  Dans le menu **Outils**, sélectionnez **Options**.  
  
2.  Dans le **Options** boîte de dialogue, dans la zone de gauche, ouvrez le **débogage** nœud.  
  
3.  Sous **débogage**, cliquez sur **fenêtre sortie**.  
  
4.  Sous **paramètres généraux de sortie**, sélectionnez **toute sortie du débogage**.  
  
5.  Dans la zone de droite, recherchez **paramètres de Trace WPF**.  
  
6.  Ouvrez le **paramètres de Trace WPF** nœud.  
  
7.  Sous **paramètres de Trace WPF**, cliquez sur la catégorie de paramètres que vous souhaitez activer (par exemple, **une liaison de données**).  
  
     Un contrôle de liste déroulante apparaît dans la colonne paramètres en regard **une liaison de données** ou de la catégorie que vous avez cliqué.  
  
8.  Cliquez sur la liste déroulante et sélectionnez le type d’informations de trace que vous souhaitez voir : **tous les**, **critique**, **erreur**, **avertissement**,  **Informations**, **Verbose**, ou **ActivityTracing**.  
  
     **Critique** Active le traçage des événements critiques uniquement.  
  
     **Erreur** Active le traçage des événements critiques et d’erreur.  
  
     **Avertissement** permet de tracer critique, erreur et d’événements d’avertissement.  
  
     **Informations** Active le traçage d’événements critique, erreur, avertissement et informations.  
  
     **Verbose** Active le traçage d’événements critique, erreur, avertissement, informations et commentaires.  
  
     **Suivi d’activités** Active le traçage d’événements arrêter, Démarrer, suspendre, transfert et reprendre.  
  
     Pour plus d'informations sur la signification de ces niveaux d'informations de trace, consultez <xref:System.Diagnostics.SourceLevels>.  
  
9. Cliquez sur **OK**.  
  
### <a name="to-disable-wpf-trace-information"></a>Pour désactiver les informations de trace WPF  
  
1.  Dans le menu **Outils**, sélectionnez **Options**.  
  
2.  Dans le **Options** boîte de dialogue, dans la zone de gauche, ouvrez le **débogage** nœud.  
  
3.  Sous **débogage**, cliquez sur **fenêtre sortie**.  
  
4.  Dans la zone de droite, recherchez **paramètres de Trace WPF**.  
  
5.  Ouvrez le **paramètres de Trace WPF** nœud.  
  
6.  Sous **paramètres de Trace WPF**, cliquez sur la catégorie de paramètres que vous souhaitez activer (par exemple, **une liaison de données**).  
  
     Un contrôle de liste déroulante apparaît dans la colonne paramètres en regard **une liaison de données** ou de la catégorie que vous avez cliqué.  
  
7.  Cliquez sur la liste déroulante et sélectionnez **hors**.  
  
8.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage de WPF](../debugger/debugging-wpf.md)