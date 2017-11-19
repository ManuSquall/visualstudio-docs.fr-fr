---
title: "Vos commentaires à l’utilisateur | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user model feedback
- environment, context
- IDE, context
- IDE, user feedback
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ffc6ecc620f57f0cc1e4dd8baf02f1bd1b17d53b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="feedback-to-the-user"></a>Vos commentaires à l’utilisateur
Dans la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement de développement intégré (IDE), retour visuel concernant des fonctionnalités disponibles sont basée sur la sélection actuelle et le contexte de sélection globale de l’utilisateur. Le tableau suivant répertorie les fonctionnalités qui sont disponibles dans les contextes de sélection différente.  
  
|Contexte de sélection|Fonctionnalités disponibles|  
|-----------------------|-----------------------------|  
|IDE|Global|  
|Ensemble de produit actuel|Spécifique au produit|  
|Hiérarchie Active|Hiérarchie spécifique au type|  
|Élément de la hiérarchie Active|Hiérarchie spécifiques au type d’élément|  
|Document actif|Spécifique au type document|  
|Fenêtre de premier plan interface multidocument (MDI)|Fenêtre spécifique au type|  
|Contexte de sélection en cours|Contexte de sélection spécifique|  
  
 Si vous exposer uniquement les fonctionnalités utilisateurs avez besoin et offrir une sélection cohérente et les commentaires de contexte d’environnement, vous réduisez la complexité dans l’IDE. Les règles suivantes s’appliquent à chaque fois qu’une fenêtre s’ouvre dans l’IDE :  
  
-   Si la fenêtre change son contexte de sélection, les commentaires de sélection sont clairement indiquée dans la fenêtre et la fenêtre Aide dynamique, si indiqué, est mis à jour pour refléter le contexte actuel.  
  
-   Si la fenêtre change le contexte de sélection globale, tous les menus spécifiques au contexte, la fenêtre de la hiérarchie active et la barre de titre d’application sont mises à jour pour refléter le contexte actuel.  
  
-   La fenêtre doit exposer des propriétés pour la sélection actuelle dans le **propriétés** fenêtre et, éventuellement, si indiqué, le **Pages de propriétés** boîte de dialogue.  
  
-   Si la fenêtre ne pas exposer les propriétés ou modifier le contexte de sélection global, des commentaires de sélection doivent rester pas dans la fenêtre lorsqu’il n’est plus la fenêtre active dans l’IDE.  
  
-   Toutes les fenêtres Outil de document spécifique doivent refléter continuellement le document actif.  
  
-   Menus, barres d’outils et la barre de titre d’application doivent refléter la fenêtre du client au premier plan interface multidocument (MDI).  
  
 Par exemple, lorsque la vue HTML d’un formulaire Web à l’intérieur d’un projet d’Application Web de Visual Basic est ouvert et que l’utilisateur sélectionne un `<td>` balise, des commentaires sont fournis dans la manière suivante :  
  
-   La sélection est indiquée dans la fenêtre active et reflétée dans le **propriétés** fenêtre.  
  
-   Spécifique au document **boîte à outils** est mis à jour le document actif.  
  
-   Le **éditeur** barre d’outils et **Table** menu sont affichées et mises à jour de la barre de titre afin de refléter la fenêtre du formulaire Web.  
  
-   La fenêtre de la hiérarchie active, qui est généralement **l’Explorateur de solutions**et sa mise à jour de barre de titre afin de refléter le contexte actuel et la liste contextuelle **projet** commandes de menu appliqueront maintenant vers le site Web actif Projet d’application.  
  
## <a name="see-also"></a>Voir aussi  
 [Sélection et la devise dans l’IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Objets de contexte de sélection](../../extensibility/internals/selection-context-objects.md)   
 [Hiérarchies et sélection](../../extensibility/internals/hierarchies-and-selection.md)