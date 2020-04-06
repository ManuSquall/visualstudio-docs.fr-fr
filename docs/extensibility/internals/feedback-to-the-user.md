---
title: Commentaires à l’utilisateur Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user model feedback
- environment, context
- IDE, context
- IDE, user feedback
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 46b9190b16b9aa444384847bf209ccca50c7f768
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708414"
---
# <a name="feedback-to-the-user"></a>Commentaires à l’utilisateur
Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE), la rétroaction visuelle concernant les fonctionnalités disponibles est basée sur la sélection actuelle de l’utilisateur et le contexte de sélection globale. Le tableau suivant répertorie les fonctionnalités disponibles dans différents contextes de sélection.

|Contexte de sélection|Fonctionnalité disponible|
|-----------------------|-----------------------------|
|IDE|Global|
|Ensemble de produits actuel|Produit spécifique|
|Hiérarchie active|Type de hiérarchie spécifique|
|Élément de hiérarchie actif|Type d’élément de hiérarchie spécifique|
|Document actif|Type de document spécifique|
|Fenêtre d’interface multi-documents topmost (MDI)|Type de fenêtre spécifique|
|Contexte de sélection actuel|Contexte de sélection spécifique|

 Si vous ne faites surface que les fonctionnalités dont les utilisateurs ont besoin et que vous fournissez continuellement une sélection cohérente et une rétroaction du contexte de l’environnement, vous réduisez la complexité de l’IDE. Les règles suivantes s’appliquent chaque fois qu’une fenêtre est ouverte dans l’IDE :

- Si la fenêtre modifie son contexte de sélection, la rétroaction de sélection est clairement indiquée dans la fenêtre, et la fenêtre **d’aide dynamique,** si elle est indiquée, est mise à jour pour refléter le contexte actuel.

- Si la fenêtre modifie le contexte de sélection globale, tous les menus spécifiques au contexte, la fenêtre de hiérarchie active et la barre de titre de l’application sont mis à jour pour refléter le contexte actuel.

- La fenêtre doit faire surface pour la sélection actuelle dans la fenêtre **Propriétés** et, si elle est indiquée, la boîte de dialogue **des Pages de propriété.**

- Si la fenêtre ne fait pas surface ou ne modifie pas le contexte de sélection globale, les commentaires de sélection ne doivent pas rester dans la fenêtre lorsqu’il n’est plus la fenêtre active de l’IDE.

- Toutes les fenêtres d’outils spécifiques aux documents doivent refléter continuellement le document actif.

- Les menus, les barres d’outils et la barre de titre de l’application doivent refléter la fenêtre client la plus haute interface multi-documents (MDI).

  Par exemple, lorsque la vue HTML d’un **formulaire Web** à l’intérieur `<td>` d’un projet d’application Web de base visuelle est ouverte et que l’utilisateur sélectionne une balise, la rétroaction est fournie de la manière suivante :

- La sélection est indiquée dans la fenêtre active et reflétée dans la fenêtre **propriétés.**

- La boîte à **outils** spécifique au document est mise à jour pour refléter le document actif.

- La barre d’outils **et** le menu de **la table** sont affichés et les mises à jour de la barre de titre reflètent la fenêtre Web Form.

- La fenêtre de hiérarchie active, qui est généralement **Solution Explorer**, et sa mise à jour de barre de titre pour refléter le contexte actuel et les commandes de menu **de projet** contextuelles s’appliquent maintenant au projet d’application Web active.

## <a name="see-also"></a>Voir aussi
- [Sélection et monnaie dans l’IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Objets contextuelles de sélection](../../extensibility/internals/selection-context-objects.md)
- [Hiérarchies et sélection](../../extensibility/internals/hierarchies-and-selection.md)
