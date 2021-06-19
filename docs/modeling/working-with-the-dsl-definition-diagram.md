---
title: Utilisation du schéma de définition DSL
description: Découvrez que le diagramme d’une définition d’outils DSL est un outil important pour la définition d’un langage spécifique à un domaine.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.diagram
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language Tools, diagram
- Domain-Specific Language Tools, Split Tree
- Domain-Specific Language Tools, Show Map Lines
- Domain-Specific Language Tools, Show As Class
- Domain-Specific Language Tools, Bring Tree Here
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f401fe0509fc425fff873a7dc224c69359156861
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388072"
---
# <a name="working-with-the-dsl-definition-diagram"></a>Utilisation du schéma de définition DSL
Le diagramme d’une [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] définition est un outil important pour définir le langage spécifique à un domaine. Vous pouvez ajouter des éléments à votre modèle de domaine et définir des relations sur le diagramme ; vous pouvez également modifier la disposition du diagramme pour accroître sa lisibilité.

## <a name="the-layout-of-the-diagram"></a>Disposition du diagramme
 Le [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] diagramme de définition comporte deux partitions : la partition **classes et relations** et la partition **éléments du diagramme** . La partition **classes et relations** affiche les classes de domaine, les relations de domaine et l’héritage. La partition **éléments de diagramme** affiche les classes de forme, les classes de connecteur, les classes de couloir et le diagramme de concepteur généré.

 Les classes de domaine peuvent apparaître à plusieurs emplacements dans les partitions **classes et relations** . La définition d'une classe de domaine affiche une arborescence d'héritage si elle est la classe de base d'autres classes de domaine et une arborescence de relations si elle est la source des relations d'incorporation ou de référence. Les espaces réservés de classes de domaine apparaissent comme les cibles des relations d'incorporation ou de référence. Par défaut, les éléments d’espace réservé sont affichés avec le compartiment **Propriétés de domaine** réduit. Ils n'affichent ni l'héritage ni les relations d'incorporation ou de référence.

 Lorsque vous ajoutez une classe de domaine, elle apparaît dans la partie inférieure de la partition **classes et relations** . Lorsque vous ajoutez une relation d'incorporation ou de référence, elle est tracée sous et à la droite de la classe de domaine source.

 Au fur et à mesure que vous ajoutez des classes de domaine et des relations, la recherche d'une classe de domaine particulière peut se révéler difficile. Vous pouvez trouver une classe de domaine en cliquant dessus avec le bouton droit dans l' **Explorateur DSL** , puis en cliquant sur **Rechercher dans le diagramme**.

 Les sections suivantes expliquent comment vous pouvez modifier l'aspect du diagramme pour accroître sa lisibilité.

## <a name="copying-elements"></a>Copie d'éléments
 Vous pouvez copier, couper ou coller des éléments du diagramme de définition DSL.

## <a name="zooming-in-or-out-on-the-diagram"></a>Zoom avant ou arrière sur le diagramme
 Vous pouvez effectuer un zoom avant ou arrière sur le diagramme à l’aide de la barre d’outils **Concepteur DSL** pour définir le niveau de zoom.

## <a name="hiding-map-lines"></a>Masquage des lignes de correspondance
 Les lignes de correspondance sont les lignes tracées entre une classe de domaine ou une relation de domaine et la forme ou le connecteur auquel elle est mappée. Vous pouvez masquer les lignes de la carte en cliquant sur le bouton **afficher les lignes** de la carte dans la barre d’outils **Concepteur DSL** . Pour afficher les lignes, cliquez à nouveau sur le bouton.

## <a name="changing-the-diagram-layout"></a>Modification de la disposition du diagramme
 Vous pouvez modifier la disposition de la partition **classes et relations** comme suit.

### <a name="expandcollapse"></a>Développer/Réduire
 Vous pouvez réduire la taille d’un élément de forme de compartiment qui représente une classe de domaine ou une forme en cliquant dessus avec le bouton droit, puis en cliquant sur **réduire**. Cela masque le compartiment des **Propriétés de domaine** de la forme. Pour afficher à nouveau le compartiment des **Propriétés de domaine** , cliquez avec le bouton droit sur la forme, puis cliquez sur **développer**.

### <a name="move-updown"></a>Déplacer vers le haut ou vers le bas
 Vous pouvez déplacer une classe de domaine ou un élément de diagramme vers le haut ou vers le haut dans la partition en cliquant avec le bouton droit sur l’élément, puis en cliquant sur **monter** ou **descendre**. Si vous déplacez un élément d'espace réservé affiché comme la cible d'une relation d'incorporation ou de référence, la relation sera également déplacée.

### <a name="expandcollapse-relationships-tree"></a>Développer/réduire l'arborescence des relations
 Si une classe de domaine joue le rôle source dans les relations d’incorporation ou de référence avec d’autres classes de domaine, vous pouvez masquer les relations en cliquant avec le bouton droit sur la définition de classe de domaine, puis en cliquant sur **réduire l’arborescence des relations**. Pour afficher les relations, cliquez avec le bouton droit sur l’élément de définition, puis cliquez sur **développer l’arborescence des relations**.

### <a name="expandcollapse-inheritance-tree"></a>Développer/réduire l'arborescence d'héritage
 Si une classe de domaine est la classe de base d’autres classes de domaine, vous pouvez masquer l’arborescence d’héritage en cliquant avec le bouton droit sur la définition de classe de domaine, puis en cliquant sur **réduire l’arborescence d’héritage**. Pour afficher l’arborescence d’héritage, cliquez avec le bouton droit sur l’élément de définition, puis cliquez sur **développer l’arborescence d’héritage**.

### <a name="bring-tree-here"></a>Bring Tree Here (action)
 Vous pouvez consolider le diagramme en cliquant avec le bouton droit sur une classe de domaine d’espace réservé, puis en cliquant sur **Placer l’arborescence ici**. La classe de domaine de l'espace réservé devient un élément de définition et affiche les arborescences d'héritage et de relations. Le précédent élément de définition devient un élément d'espace réservé s'il est la cible d'une relation ou l'enfant d'une relation d'héritage ; dans le cas contraire, il disparaît.

### <a name="split-tree"></a>Arborescence fractionnée
 Vous pouvez décomposer les arborescences d’héritage ou de relations en cliquant avec le bouton droit sur la définition de classe de domaine qui les affiche, puis en cliquant sur **fractionner l’arborescence**. L'élément de définition devient un élément d'espace réservé et la classe de domaine de la définition, ainsi que ses relations d'héritage et de relation, s'affiche désormais en bas de la partition.

### <a name="show-as-class"></a>Show As Class
 Si une relation de domaine a des relations dérivées, ou si elle a des relations d’incorporation ou de référence avec d’autres relations de domaine, vous pouvez afficher la relation en tant que classe en cliquant avec le bouton droit sur la relation, puis en cliquant sur **afficher en tant que classe**. La relation sera affichée avec un compartiment **Propriétés de domaine** et affichera les arborescences héritage et relations.

## <a name="see-also"></a>Voir aussi

- [Glossaire des Outils Domain-Specific Language](/previous-versions/bb126564(v=vs.100))