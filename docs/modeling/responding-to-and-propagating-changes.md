---
title: "Propagation et r&#233;ponse aux modifications en attente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "langage spécifique à un domaine, événements"
ms.assetid: fc2e9ac5-7a84-44ed-9945-94e45f89c227
caps.latest.revision: 24
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 24
---
# Propagation et r&#233;ponse aux modifications en attente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lorsqu'un élément est créé, supprimé ou mis à jour, vous pouvez écrire du code qui propage la modification à d'autres parties du modèle, ou à des ressources externes telles que les fichiers, les bases de données, ou d'autres composants.  
  
## Dans cette section  
 comme indication, considérez ces techniques dans l'ordre suivant :  
  
|Technique|Scénarios|Pour plus d'informations|  
|---------------|---------------|------------------------------|  
|définissez une propriété de domaine calculée.|une propriété de domaine dont la valeur est calculée d'autres propriétés dans le modèle.  par exemple, un prix qui est la somme de prix des éléments associés.|[Propriétés de stockage calculées et personnalisées](../modeling/calculated-and-custom-storage-properties.md)|  
|définissez une propriété de domaine personnalisée de stockage.|Une propriété de domaine stockée dans d'autres parties du modèle ou de l'extérieur.  Par exemple, vous pouvez analyser une chaîne d'expression en une arborescence dans le modèle.|[Propriétés de stockage calculées et personnalisées](../modeling/calculated-and-custom-storage-properties.md)|  
|Substituez les gestionnaires de modification par exemple OnValueChanging et OnDeleting|Conservez les différents éléments de la synchronisation, et conserver des valeurs externes synchronisé avec le le modèle.<br /><br /> Contraignez des valeurs aux plages définies.<br /><br /> Appelé juste avant et après la valeur de propriété et d'autres modifications.  vous pouvez terminer la modification en levant une exception.|[Gestionnaire de modification de la valeur de propriété du domaine](../modeling/domain-property-value-change-handlers.md)|  
|Règles|Vous pouvez définir des règles qui sont mises en file d'attente de l'exécution juste avant la fin d'une transaction pendant laquelle la modification s'est produite.  Elles ne sont pas exécutées sur l'annulation ou la de rétablissement.  Employez\-les pour conserver une partie du magasin dans la synchronisation avec les autres.|[Règles de propagent les modifications dans le modèle](../modeling/rules-propagate-changes-within-the-model.md)|  
|Événements du magasin|Le magasin de modélisation fournit des notifications d'événements tels que l'ajout ou la suppression d'un élément ou un lien, ou modifier la valeur d'une propriété.  L'événement est exécuté sur une annulation et la de rétablissement.  Utilisez les événements du magasin pour mettre à jour les valeurs qui ne sont pas dans le magasin.|[Propagation de modifications en dehors du modèle par des gestionnaires d'événements](../modeling/event-handlers-propagate-changes-outside-the-model.md)|  
|événements.NET|les formes ont des gestionnaires d'événements qui répondent aux clics de souris et à d'autres entrées tactiles.  Vous devez vous inscrire à ces événements pour chaque objet.  L'inscription est généralement fait dans une substitution d'InitializeInstanceResources, et doit être effectuée pour chaque élément.<br /><br /> Ces événements se produisent habituellement en dehors d'une transaction.|[Comment : intercepter un événement Click sur une forme ou un décorateur](../Topic/How%20to:%20Intercept%20a%20Click%20on%20a%20Shape%20or%20Decorator.md)|  
|règles limites|Une règle limites sert de manière spécifique de contraindre les limites d'une forme.|[Définition de l'emplacement et de la taille de la forme par la classe BoundsRules](../modeling/boundsrules-constrain-shape-location-and-size.md)|  
|règles de sélection|Les règles de sélection limitent spécifiquement ce que l'utilisateur peut sélectionner.|[Comment : accéder à et contraindre la sélection actuelle](../modeling/how-to-access-and-constrain-the-current-selection.md)|  
|OnAssocatedPropertyChanged|Désignez des rapports d'éléments de modèle à l'aide de les fonctionnalités des formes et les connecteurs tels que l'ombre, les pointes de flèche, la couleur, et les largeurs de ligne et le style.|[Mise à jour des formes et des connecteurs pour refléter le modèle](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|  
  
## **Comparer les règles et les événements du magasin**  
 Modifiez les auteurs de la notification, règles, les événements et sont exécutés lorsque des modifications se produisent dans un modèle.  
  
 Les règles s'appliquent habituellement à la transaction de fin dans laquelle la modification s'est produite, les événements et sont appliqués après que des modifications dans une transaction elles soient.  
  
 Utilisez les événements du magasin pour synchroniser le modèle avec des objets à l'extérieur de le magasin, et des règles d'assurer la cohérence dans le magasin.  
  
-   **Création de règles personnalisées** vous créez une règle personnalisée comme une classe dérivée d'une règle abstraite.  Vous devez également notifier l'infrastructure sur la règle personnalisée.  Pour plus d'informations, consultez [Règles de propagent les modifications dans le modèle](../modeling/rules-propagate-changes-within-the-model.md).  
  
-   **Abonnement à des événements** avant de pouvoir vous abonner à un événement, créer un gestionnaire d'événements et un délégué.  Utilisez ensuite la propriété d' <xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A>pour s'abonner à l'événement.  Pour plus d'informations, consultez [Propagation de modifications en dehors du modèle par des gestionnaires d'événements](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
-   **Annuler change** lorsque vous annulez une transaction, les événements sont déclenchés, mais les règles ne sont pas appliquées.  si une règle modifie une valeur et vous annulez cette modification, la valeur est réinitialisée à la valeur d'origine pendant l'opération d'annulation.  Lorsqu'un événement est déclenché, vous devez modifier manuellement la valeur dans sa valeur d'origine.  Pour en savoir plus sur les transactons et de la commande undo, consultez [Comment : utiliser des transactions pour mettre à jour le modèle](../modeling/how-to-use-transactions-to-update-the-model.md).  
  
-   **Passage des arguments d'événement aux règles et** aux événements et aux règles**d'événements** sont passés un paramètre d' `EventArgs` qui contient des informations sur la façon dont le modèle a été modifiée.  
  
## Voir aussi  
 [Comment : intercepter un événement Click sur une forme ou un décorateur](../Topic/How%20to:%20Intercept%20a%20Click%20on%20a%20Shape%20or%20Decorator.md)   
 [Écrire du Code pour personnaliser un langage spécifique à un domaine](../modeling/writing-code-to-customise-a-domain-specific-language.md)