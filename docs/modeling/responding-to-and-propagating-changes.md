---
title: Propagation et réponse aux modifications en attente
description: Découvrez que lorsqu’un élément est créé, supprimé ou mis à jour, vous pouvez écrire du code qui propage la modification à d’autres parties du modèle ou à des ressources externes.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d6fc8345ca90414f410dde9a089d9529ed19536b
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387578"
---
# <a name="respond-to-and-propagate-changes"></a>Répondre aux modifications et les propager

Lorsqu’un élément est créé, supprimé ou mis à jour, vous pouvez écrire du code qui propage la modification à d’autres parties du modèle, ou à des ressources externes telles que des fichiers, des bases de données ou d’autres composants.

## <a name="reference"></a>Informations de référence

À titre indicatif, envisagez ces techniques dans l’ordre suivant :

|Technique|Scénarios|Informations supplémentaires|
|-|-|-|
|Définissez une propriété de domaine calculée.|Propriété de domaine dont la valeur est calculée à partir d’autres propriétés dans le modèle. Par exemple, un prix qui correspond à la somme des prix des éléments associés.|[Propriétés de stockage calculées et personnalisées](../modeling/calculated-and-custom-storage-properties.md)|
|Définissez une propriété de domaine de stockage personnalisée.|Propriété de domaine stockée dans d’autres parties du modèle ou en externe. Par exemple, vous pouvez analyser une chaîne d’expression dans une arborescence du modèle.|[Propriétés de stockage calculées et personnalisées](../modeling/calculated-and-custom-storage-properties.md)|
|Remplacer les gestionnaires de modification tels que OnValueChanging et OnDeleting|Conserver les différents éléments synchronisés et maintenir la synchronisation des valeurs externes avec le modèle.<br /><br /> Limitez les valeurs aux plages définies.<br /><br /> Appelée juste avant et après la valeur de propriété et d’autres modifications. Vous pouvez arrêter la modification en levant une exception.|[Gestionnaires de modification de la valeur de propriété du domaine](../modeling/domain-property-value-change-handlers.md)|
|Règles|Vous pouvez définir des règles qui sont mises en file d’attente d’exécution juste avant la fin d’une transaction dans laquelle une modification s’est produite. Elles ne sont pas exécutées lors d’une opération d’annulation ou de rétablissement. Utilisez-les pour maintenir une partie du magasin synchronisée avec une autre.|[Propagation de modifications dans le modèle par des règles](../modeling/rules-propagate-changes-within-the-model.md)|
|Stocker les événements|Le magasin de modélisation fournit des notifications d’événements, tels que l’ajout ou la suppression d’un élément ou d’un lien, ou la modification de la valeur d’une propriété. L’événement est également exécuté lors des opérations d’annulation et de rétablissement. Utilisez les événements Store pour mettre à jour les valeurs qui ne sont pas dans le magasin.|[Propagation de modifications en dehors du modèle par des gestionnaires d'événements](../modeling/event-handlers-propagate-changes-outside-the-model.md)|
|Événements .NET|Les formes comportent des gestionnaires d’événements qui répondent aux clics de souris et à d’autres gestes. Vous devez vous inscrire pour ces événements pour chaque objet. L’inscription s’effectue généralement dans une substitution de InitializeInstanceResources et doit être effectuée pour chaque élément.<br /><br /> Ces événements se produisent généralement en dehors d’une transaction.|[Guide pratique pour intercepter un événement de clic sur une forme ou un décorateur](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)|
|Règles de limites|Une règle de limites est utilisée spécifiquement pour contraindre les limites d’une forme.|[Emplacement et de la taille de la forme contrainte par BoundsRules](/previous-versions/visualstudio/visual-studio-2015/modeling/boundsrules-constrain-shape-location-and-size?preserve-view=true&view=vs-2015)|
|Règles de sélection|Les règles de sélection limitent spécifiquement ce que l’utilisateur peut sélectionner.|[Comment : accéder à et contraindre la sélection actuelle](../modeling/how-to-access-and-constrain-the-current-selection.md)|
|OnAssocatedPropertyChanged|Indiquer les États des éléments de modèle à l’aide des fonctionnalités des formes et des connecteurs tels que l’ombre, les flèches, la couleur et le style et la largeur des lignes.|[Mise à jour des formes et des connecteurs pour refléter le modèle](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|

## <a name="compare-rules-and-store-events"></a>Comparer des règles et des événements de magasin

Les notifications de modification, les règles et les événements sont exécutés lorsque des modifications se produisent dans un modèle.

Les règles sont généralement appliquées à la transaction finale dans laquelle la modification s’est produite, et les événements sont appliqués après la validation des modifications apportées à une transaction.

Utilisez les événements de Store pour synchroniser le modèle avec des objets en dehors du magasin et des règles pour maintenir la cohérence dans le magasin.

- **Création de règles personnalisées** Vous créez une règle personnalisée en tant que classe dérivée à partir d’une règle abstraite. Vous devez également informer l’infrastructure de la règle personnalisée. Pour plus d’informations, consultez [règles de propagation des modifications dans le modèle](../modeling/rules-propagate-changes-within-the-model.md).

- **Abonnement à des événements** Avant de pouvoir vous abonner à un événement, créez un gestionnaire d’événements et un délégué. Utilisez ensuite la <xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A> propriété pour vous abonner à l’événement. Pour plus d’informations, consultez les [gestionnaires d’événements propagent les modifications en dehors du modèle](../modeling/event-handlers-propagate-changes-outside-the-model.md).

- **Annuler des modifications** Lorsque vous annulez une transaction, les événements sont déclenchés, mais les règles ne sont pas appliquées. Si une règle modifie une valeur et que vous annulez cette modification, la valeur est réinitialisée à la valeur d’origine au cours de l’opération d’annulation. Quand un événement est déclenché, vous devez rétablir manuellement la valeur d’origine. Pour en savoir plus sur les transactions et l’annulation, consultez [procédure : utiliser des transactions pour mettre à jour le modèle](../modeling/how-to-use-transactions-to-update-the-model.md).

- **Passage d’arguments d’événement à des règles et des événements** Un `EventArgs` paramètre qui contient des informations sur la façon dont le modèle a été modifié est passé aux deux événements et règles.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour intercepter un événement de clic sur une forme ou un décorateur](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)
- [Écriture de code pour personnaliser un langage de Domain-Specific](../modeling/writing-code-to-customise-a-domain-specific-language.md)