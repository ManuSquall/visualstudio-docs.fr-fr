---
title: "Vos commentaires &#224; l&#39;utilisateur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "commentaires de modèle utilisateur"
  - "environnement, contexte"
  - "IDE, contexte"
  - "IDE, les commentaires des utilisateurs"
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Vos commentaires &#224; l&#39;utilisateur
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Dans l'IDE de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(IDE\), la rétroaction visuelle concernant la fonctionnalité disponible est basée sur la sélection actuelle de l'utilisateur et le contexte global de sélection.  Le tableau suivant répertorie les fonctionnalités disponibles dans différents contextes de sélection.  
  
|contexte de sélection|Fonctionnalités disponibles|  
|---------------------------|---------------------------------|  
|IDE|Global|  
|ensemble actuel de produit|détail de produit|  
|hiérarchie active|Détail de type de la hiérarchie|  
|Élément actif de la hiérarchie|Détail de type d'élément de la hiérarchie|  
|document actif|détail de type de document|  
|fenêtre le plus élevé \(MDI\) d'interface multidocument|détail de type de fenêtre|  
|contexte actuel de sélection|détail de contexte de sélection|  
  
 Si vous ne surface les utilisateurs tirent de fonctionnalité et fournissez continuellement la sélection cohérente et commentaires de contexte d'environnement, vous réduisez la complexité de l'IDE.  Les règles suivantes s'appliquent lorsqu'une fenêtre est ouverte dans l'IDE :  
  
-   Si la fenêtre change son contexte de sélection, les commentaires de sélection est clairement indiquée dans la fenêtre, et la fenêtre d'Aide dynamique, si est affichée, est mise à jour pour refléter le contexte actuel.  
  
-   Si la fenêtre change de contexte global de sélection, tous les menus de spécifique au contexte, la fenêtre active de hiérarchie, et la barre de titre d'application sont mis à jour pour refléter le contexte actuel.  
  
-   La fenêtre doit apprêter des propriétés pour la sélection actuelle dans la fenêtre de **Propriétés** et éventuellement, si affichée, la boîte de dialogue **Pages de propriétés** .  
  
-   Si la fenêtre ne considère pas les propriétés ou ne modifie pas le contexte global de sélection, les commentaires de sélection ne doit pas rester dans la fenêtre lorsque ce n'est plus la fenêtre active dans l'IDE.  
  
-   Toutes les fenêtres Outil de document\-détail doivent continuellement refléter le document actif.  
  
-   Les menus, les barres d'outils et la barre de titre d'application doivent refléter la fenêtre le plus \(MDI\) élevé de client d'interface multidocument.  
  
 Par exemple, le mode HTML d'un formulaire web au sein d'un projet d'application Web Visual Basic est ouvert et l'utilisateur sélectionne une balise d' `<td>` , la est tenu de la manière suivante :  
  
-   La sélection est indiquée dans la fenêtre active et répercutées dans la fenêtre de **Propriétés** .  
  
-   le document\-détail **boîte à outils** est mis à jour pour refléter le document actif.  
  
-   la barre d'outils d' **Éditeur** et le menu de **Tableau** sont affichés et les mises à jour de barre de titre pour refléter la fenêtre de formulaire web.  
  
-   La fenêtre active de hiérarchie, qui est généralement **Explorateur de solutions**, et sa mise à jour de barre de titre pour refléter le contexte actuel et les commandes de menu contextuelles de **Projet** s'appliquent à présent au projet d'application Web actif.  
  
## Voir aussi  
 [Sélection et la devise dans l’IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Objets de contexte de sélection](../../extensibility/internals/selection-context-objects.md)   
 [Hiérarchies et la sélection](../../extensibility/internals/hierarchies-and-selection.md)