---
title: Afficher les informations de trace WPF | Microsoft Docs
description: Visual Studio peut recevoir des informations de trace de débogage à partir d’applications WPF et les afficher dans la fenêtre sortie. Apprenez à gérer et à personnaliser le traçage WPF.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e4800c2ca44c2c52b2059685d9c5bc4fe38ed08
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903972"
---
# <a name="how-to-display-wpf-trace-information"></a>Comment : afficher les informations de trace WPF
[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] peut recevoir des informations de trace de débogage envoyées par des applications WPF et afficher ces informations dans la fenêtre **Sortie**. Pour afficher les informations de trace de débogage, le traçage WPF doit être activé.

 Vous pouvez activer le traçage WPF dans votre fichier App.Config ou par programmation en utilisant la classe <xref:System.Diagnostics.PresentationTraceSources>. La fenêtre **Options** est le moyen le plus simple d’activer le traçage WPF. Le traçage WPF pour les applications Web n'est pas pris en charge.

### <a name="to-enable-or-customize-wpf-trace-information"></a>Pour activer ou personnaliser les informations de trace WPF

1. Dans le menu **Tools** (Outils), sélectionnez **Options**.

2. Dans la boîte de dialogue **Options**, ouvrez le nœud **Débogage** dans la zone située à gauche.

3. Sous **Débogage**, cliquez sur **Fenêtre Sortie**.

4. Sous **Paramètres généraux de sortie**, sélectionnez **Toute sortie du débogage**.

5. Dans la zone à droite, recherchez **Paramètres de trace WPF**.

6. Ouvrez le nœud **Paramètres de trace WPF**.

7. Sous **Paramètres de trace WPF**, cliquez sur la catégorie de paramètres que vous voulez activer (par exemple **Liaison de données**).

     Un contrôle de liste déroulante s’affiche dans la colonne Paramètres en regard de **Liaison de données** ou de la catégorie sur laquelle vous avez cliqué.

8. Cliquez sur la liste déroulante et sélectionnez le type d’informations de trace que vous voulez voir : **Tous**, **Critique**, **Erreur**, **Avertissement**, **Informations**, **Commentaires** ou **Activité**.

     **Critique** permet de tracer uniquement les événements « Critique ».

     **Erreur** permet de tracer les événements « Critique » et « Erreur ».

     **Avertissement** permet de tracer les événements « Critique », « Erreur » et « Avertissement ».

     **Informations** permet de tracer les événements « Critique », « Erreur », « Avertissement » et « Informations ».

     **Commentaires** permet de tracer les événements « Critique », « Erreur », « Avertissement », « Informations » et « Commentaires ».

     **Activité** permet de tracer les événements « Arrêter », « Démarrer », « Interrompre », « Transférer » et « Reprendre ».

     Pour plus d'informations sur la signification de ces niveaux d'informations de trace, consultez <xref:System.Diagnostics.SourceLevels>.

9. Cliquez sur **OK**.

### <a name="to-disable-wpf-trace-information"></a>Pour désactiver les informations de trace WPF

1. Dans le menu **Tools** (Outils), sélectionnez **Options**.

2. Dans la boîte de dialogue **Options**, ouvrez le nœud **Débogage** dans la zone située à gauche.

3. Sous **Débogage**, cliquez sur **Fenêtre Sortie**.

4. Dans la zone à droite, recherchez **Paramètres de trace WPF**.

5. Ouvrez le nœud **Paramètres de trace WPF**.

6. Sous **Paramètres de trace WPF**, cliquez sur la catégorie de paramètres que vous voulez activer (par exemple **Liaison de données**).

     Un contrôle de liste déroulante s’affiche dans la colonne Paramètres en regard de **Liaison de données** ou de la catégorie sur laquelle vous avez cliqué.

7. Cliquez sur la liste déroulante et sélectionnez **Inactif**.

8. Cliquez sur **OK**.

## <a name="see-also"></a>Voir aussi
- [Débogage WPF](../debugger/debugging-wpf.md)