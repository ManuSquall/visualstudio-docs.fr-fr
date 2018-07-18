---
title: Propagation et réponse aux modifications en attente
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: d87a93016f2004a45a572374d68a20d2e59073da
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31954003"
---
# <a name="responding-to-and-propagating-changes"></a>Propagation et réponse aux modifications en attente
Lorsqu’un élément est créé, supprimé ou mis à jour, vous pouvez écrire du code qui propage la modification à d’autres parties du modèle, ou à des ressources externes telles que des fichiers, de bases de données ou d’autres composants.

## <a name="in-this-section"></a>Dans cette section
 En règle générale, examinez ces techniques dans l’ordre suivant :

|Technique|Scénarios|Pour plus d'informations|
|---------------|---------------|--------------------------|
|Définir une propriété de domaine calculée.|Une propriété de domaine dont la valeur est calculée à partir d’autres propriétés dans le modèle. Par exemple, un prix qui est la somme des prix des éléments connexes.|[Propriétés de stockage calculées et personnalisées](../modeling/calculated-and-custom-storage-properties.md)|
|Définir une propriété de domaine personnalisé stockage.|Une propriété de domaine stockée dans d’autres parties du modèle ou à l’extérieur. Par exemple, vous pouvez analyser une chaîne d’expression dans une arborescence dans le modèle.|[Propriétés de stockage calculées et personnalisées](../modeling/calculated-and-custom-storage-properties.md)|
|Substituer les gestionnaires de modification telles que OnValueChanging et OnDeleting|Synchroniser les différents éléments et de synchroniser les valeurs externes avec le modèle.<br /><br /> Limiter les valeurs pour les plages définies.<br /><br /> Appelé juste avant et après la valeur de propriété et d’autres modifications. Vous pouvez mettre fin à la modification en levant une exception.|[Gestionnaires de modification de la valeur de propriété du domaine](../modeling/domain-property-value-change-handlers.md)|
|Règles|Vous pouvez définir des règles qui sont en attente de l’exécution juste avant la fin d’une transaction dans laquelle un changement s’est produit. Ils ne sont pas exécutées sur l’annulation ou de restauration par progression. Utilisez-les pour qu’une partie de la banque reste synchronisé avec un autre.|[Propagation de modifications dans le modèle par des règles](../modeling/rules-propagate-changes-within-the-model.md)|
|Stocker les événements|Le magasin de modélisation fournit des notifications d’événements tels que l’ajout ou suppression d’un élément ou un lien ou modification de la valeur d’une propriété. L’événement est également exécuté sur Annuler et rétablir. Événements de la banque permet de mettre à jour les valeurs qui ne sont pas dans le magasin.|[Propagation de modifications en dehors du modèle par des gestionnaires d’événements](../modeling/event-handlers-propagate-changes-outside-the-model.md)|
|Événements .NET|Les formes ont des gestionnaires d’événements qui répondent aux clics de souris et d’autres manipulations. Vous devez l’inscrire pour ces événements pour chaque objet. L’inscription est généralement le cas dans une substitution de InitializeInstanceResources et doit être effectuée pour chaque élément.<br /><br /> Ces événements se produisent généralement en dehors d’une transaction.|[Guide pratique pour intercepter un événement de clic sur une forme ou un décorateur](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)|
|Règles de limites|Une règle de limites est utilisée en particulier pour contraindre les limites d’une forme.|[Emplacement et de la taille de la forme contrainte par BoundsRules](../modeling/boundsrules-constrain-shape-location-and-size.md)|
|Règles de sélection|Règles de sélection contraignent spécifiquement à ce que l’utilisateur peut sélectionner.|[Guide pratique pour accéder à et contraindre la sélection actuelle](../modeling/how-to-access-and-constrain-the-current-selection.md)|
|OnAssocatedPropertyChanged|Indiquer les États des éléments de modèle à l’aide des fonctionnalités des formes et des connecteurs tels que les clichés instantanés, pointes de flèche, couleur et les largeurs de ligne et le style.|[Mise à jour des formes et des connecteurs pour refléter le modèle](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|

## <a name="comparing-rules-and-store-events"></a>**Comparaison des règles et des événements de la banque**
 Utilitaires de notification de modification, les règles et les événements sont exécutées lorsque des modifications se produisent dans un modèle.

 Les règles sont généralement appliquées à la transaction de fin dans laquelle la modification s’est produite, et les événements sont appliqués après que les modifications dans une transaction sont validées.

 Événements de la banque permet de synchroniser le modèle avec des objets en dehors de la banque et les règles pour maintenir la cohérence dans le magasin.

-   **Création de règles personnalisées** vous créez une règle personnalisée comme une classe dérivée à partir d’une règle abstraite. Vous devez également informer l’infrastructure de la règle personnalisée. Pour plus d’informations, consultez [propager les modifications dans le modèle de règles](../modeling/rules-propagate-changes-within-the-model.md).

-   **S’abonner aux événements** avant de vous abonner à un événement, créez un gestionnaire d’événements et d’un délégué. Utilisez ensuite le <xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A>propriété pour vous abonner à l’événement. Pour plus d’informations, consultez [gestionnaires propager les modifications en dehors du modèle d’événement](../modeling/event-handlers-propagate-changes-outside-the-model.md).

-   **Annulation des modifications** lorsque vous annulez une transaction, les événements sont déclenchés, mais les règles ne sont pas appliquées. Si une règle modifie une valeur, vous annulez la modification, la valeur est réinitialisée à la valeur d’origine au cours de l’action d’annulation. Lorsqu’un événement est déclenché, vous devez modifier manuellement la valeur à sa valeur d’origine. Pour en savoir plus sur transactons et d’annulation, consultez [Comment : utiliser les Transactions pour mettre à jour le modèle](../modeling/how-to-use-transactions-to-update-the-model.md).

-   **Passage des Arguments d’événement à des règles et des événements** les deux événements et les règles sont transmises un `EventArgs` de modifier le modèle de paramètre qui contient des informations sur la façon.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour intercepter un événement de clic sur une forme ou un décorateur](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)
- [Écriture de code pour personnaliser un langage spécifique à un domaine](../modeling/writing-code-to-customise-a-domain-specific-language.md)