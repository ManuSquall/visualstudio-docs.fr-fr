---
title: Commentaires à l’utilisateur | Microsoft Docs
description: Découvrez comment fournir des commentaires visuels à l’utilisateur sur les fonctionnalités disponibles dans l’environnement de développement intégré (IDE) de Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: d8f3f79a61729a641ee7c046ddd196a648469fb3
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480523"
---
# <a name="feedback-to-the-user"></a>Commentaires à l’utilisateur
Dans l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement de développement intégré (IDE), les commentaires visuels concernant les fonctionnalités disponibles sont basés sur la sélection actuelle de l’utilisateur et le contexte de sélection globale. Le tableau suivant répertorie les fonctionnalités disponibles dans différents contextes de sélection.

|Contexte de sélection|Fonctionnalités disponibles|
|-----------------------|-----------------------------|
|IDE|Global|
|Ensemble de produits actuel|Spécifique au produit|
|Hiérarchie Active|Spécifique au type de hiérarchie|
|Élément de la hiérarchie Active|Spécifique au type d’élément de hiérarchie|
|Document actif|Spécifique au type de document|
|Fenêtre MDI (multiple-document interface)|Spécifique au type de fenêtre|
|Contexte de sélection actuel|Contexte de sélection spécifique|

 Si vous surveillez uniquement les fonctionnalités dont les utilisateurs ont besoin et que vous fournissez continuellement une sélection cohérente et des commentaires de contexte d’environnement, vous réduisez la complexité de l’IDE. Les règles suivantes s’appliquent à chaque ouverture d’une fenêtre dans l’IDE :

- Si la fenêtre modifie son contexte de sélection, les commentaires de sélection sont clairement indiqués dans la fenêtre, et la fenêtre **d’aide dynamique** , si elle est affichée, est mise à jour pour refléter le contexte actuel.

- Si la fenêtre change le contexte de sélection global, tous les menus spécifiques au contexte, à la fenêtre de la hiérarchie active et à la barre de titre de l’application sont mis à jour pour refléter le contexte actuel.

- La fenêtre doit surfacer les propriétés de la sélection actuelle dans la fenêtre **Propriétés** et éventuellement, si elle est affichée, la boîte de dialogue **pages de propriétés** .

- Si la fenêtre ne contient pas de propriétés de surface ou modifie le contexte de sélection globale, les commentaires de sélection ne doivent pas rester dans la fenêtre lorsqu’il ne s’agit plus de la fenêtre active dans l’IDE.

- Toutes les fenêtres outil spécifiques à un document doivent refléter continuellement le document actif.

- Les menus, les barres d’outils et la barre de titre de l’application doivent refléter la fenêtre cliente de l’interface MDI (multiple-document interface) la plus haute.

  Par exemple, quand la vue HTML d’un **formulaire Web** dans un projet d’Application Web Visual Basic est ouverte et que l’utilisateur sélectionne une `<td>` balise, les commentaires sont fournis de la manière suivante :

- La sélection est indiquée dans la fenêtre active et est reflétée dans la fenêtre **Propriétés** .

- La **boîte à outils** spécifique au document est mise à jour pour refléter le document actif.

- La barre d’outils de l' **éditeur** et le menu **table** sont affichés et la barre de titre est mise à jour pour refléter la fenêtre de formulaire Web.

- La fenêtre hiérarchie Active, qui est généralement **Explorateur de solutions**, et sa barre de titre sont mises à jour pour refléter le contexte actuel et les commandes de menu de **projet** contextuelles s’appliquent désormais au projet d’application Web actif.

## <a name="see-also"></a>Voir aussi
- [Sélection et devise dans l’IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Objets de contexte de sélection](../../extensibility/internals/selection-context-objects.md)
- [Hiérarchies et sélection](../../extensibility/internals/hierarchies-and-selection.md)
