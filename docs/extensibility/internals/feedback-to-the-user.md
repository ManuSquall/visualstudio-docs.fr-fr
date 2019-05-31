---
title: Vos commentaires à l’utilisateur | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user model feedback
- environment, context
- IDE, context
- IDE, user feedback
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e2255a972dd7a889713e77fa686b348500c03ea7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328980"
---
# <a name="feedback-to-the-user"></a>Vos commentaires à l’utilisateur
Dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement de développement intégré (IDE), des commentaires visuels concernant des fonctionnalités disponibles sont basée sur la sélection actuelle et le contexte de la sélection globale de l’utilisateur. Le tableau suivant répertorie les fonctionnalités qui sont disponibles dans les contextes d’autre sélection.

|Contexte de sélection|Fonctionnalités disponibles|
|-----------------------|-----------------------------|
|IDE|Global|
|Ensemble de produit actuel|Spécifique au produit|
|Hiérarchie Active|Hiérarchie spécifique au type|
|Élément de la hiérarchie Active|Hiérarchie spécifique au type élément|
|Document actif|Spécifique au type document|
|Fenêtre de premier plan interface multidocument (MDI)|Fenêtre spécifique au type|
|Contexte de sélection actuel|Contexte de sélection spécifique|

 Si vous n'apparaître que la fonctionnalité utilisateurs avez besoin et fournissent en permanence une sélection cohérente et commentaires de contexte d’environnement, vous réduisez la complexité dans l’IDE. Les règles suivantes s’appliquent à chaque fois qu’une fenêtre est ouverte dans l’IDE :

- Si la fenêtre change son contexte de sélection, des commentaires de sélection sont clairement indiquée dans la fenêtre et le **aide dynamique** fenêtre, si indiqué, est mis à jour pour refléter le contexte actuel.

- Si la fenêtre change le contexte de la sélection globale, tous les menus spécifiques au contexte, la fenêtre de la hiérarchie active et la barre de titre d’application sont mis à jour pour refléter le contexte actuel.

- La fenêtre doit faire apparaître les propriétés pour la sélection actuelle dans le **propriétés** fenêtre et, éventuellement, si indiqué, le **Pages de propriétés** boîte de dialogue.

- Si la fenêtre ne pas exposer des propriétés ou modifier le contexte de sélection global, des commentaires de sélection ne doivent pas rester dans la fenêtre lorsqu’il n’est plus la fenêtre active dans l’IDE.

- Toutes les fenêtres Outil de document spécifique doivent refléter en permanence le document actif.

- Menus, barres d’outils et la barre de titre d’application doivent refléter la fenêtre du client au premier plan interface multidocument (MDI).

  Par exemple, lorsque le code HTML affichez d’un **Web Form** à l’intérieur d’une Application Web de Visual Basic le projet est ouvert et que l’utilisateur sélectionne un `<td>` balise, est tenu de la manière suivante :

- Sélection est indiquée dans la fenêtre active et reflétée dans le **propriétés** fenêtre.

- Spécifique au document **boîte à outils** est mis à jour le document actif.

- Le **éditeur** barre d’outils et **Table** menu sont affichées et mises à jour de la barre de titre afin de refléter la fenêtre du formulaire Web.

- La fenêtre hiérarchie active, qui est généralement **l’Explorateur de solutions**et sa mise à jour de barre de titre afin de refléter le contexte actuel et le contextuelle **projet** maintenant appliqueront des commandes de menu pour le site Web actif Projet d’application.

## <a name="see-also"></a>Voir aussi
- [Sélection et la devise dans l’IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Objets de contexte de sélection](../../extensibility/internals/selection-context-objects.md)
- [Hiérarchies et sélection](../../extensibility/internals/hierarchies-and-selection.md)