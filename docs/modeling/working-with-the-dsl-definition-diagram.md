---
title: "Utilisation du sch&#233;ma de d&#233;finition DSL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.diagram"
  - "vs.dsltools.dsldesigner.dsldiagram"
helpviewer_keywords: 
  - "outils de langage spécifique à un domaine, Bring Tree Here (action)"
  - "outils de langage spécifique à un domaine, schéma"
  - "outils de langage spécifique à un domaine, Show As Class"
  - "outils de langage spécifique à un domaine, Show Map Lines"
  - "outils de langage spécifique à un domaine, Split Tree"
ms.assetid: 1a4c7a58-e134-438e-848e-efd98f92bf10
caps.latest.revision: 21
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 21
---
# Utilisation du sch&#233;ma de d&#233;finition DSL
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le diagramme d'une définition [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] est un outil important pour définir le langage spécifique à un domaine.  Vous pouvez ajouter des éléments à votre modèle de domaine et définir des relations sur le diagramme ; vous pouvez également modifier la disposition du diagramme pour accroître sa lisibilité.  
  
## Disposition du diagramme  
 Le diagramme de définition [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] possède deux partitions, la partition **Classes et relations** et la partition **Éléments de diagramme**.  La partition **Classes et relations** affiche les classes de domaine, les relations de domaine et l'héritage. La partition **Éléments de diagramme** affiche les classes de forme, les classes de connecteur, les classes de couloir et le diagramme du concepteur généré.  
  
 Les classes de domaine peuvent apparaître à plusieurs emplacements des partitions **Classes et relations**.  La définition d'une classe de domaine affiche une arborescence d'héritage si elle est la classe de base d'autres classes de domaine et une arborescence de relations si elle est la source des relations d'incorporation ou de référence.  Les espaces réservés de classes de domaine apparaissent comme les cibles des relations d'incorporation ou de référence.  Par défaut, les éléments des espaces réservés sont affichés avec le compartiment **Propriétés de domaine** réduit.  Ils n'affichent ni l'héritage ni les relations d'incorporation ou de référence.  
  
 Lorsque vous ajoutez une classe de domaine, elle apparaît dans la partie inférieure de la partition **Classes et relations**.  Lorsque vous ajoutez une relation d'incorporation ou de référence, elle est tracée sous et à la droite de la classe de domaine source.  
  
 Au fur et à mesure que vous ajoutez des classes de domaine et des relations, la recherche d'une classe de domaine particulière peut se révéler difficile.  Vous pouvez rechercher une classe de domaine en cliquant dessus avec le bouton droit dans l'**Explorateur DSL**, puis en cliquant sur **Rechercher dans le diagramme**.  
  
 Les sections suivantes expliquent comment vous pouvez modifier l'aspect du diagramme pour accroître sa lisibilité.  
  
## Copie d'éléments  
 Vous pouvez copier, couper ou coller des éléments du diagramme de définition DSL.  
  
## Zoom avant ou arrière sur le diagramme  
 Vous pouvez effectuer un zoom avant ou arrière sur le diagramme en utilisant la barre d'outils du **Concepteur DSL** pour définir le niveau de zoom.  
  
## Masquage des lignes de correspondance  
 Les lignes de correspondance sont les lignes tracées entre une classe de domaine ou une relation de domaine et la forme ou le connecteur auquel elle est mappée.  Vous pouvez masquer les lignes de correspondance en cliquant sur le bouton **Afficher les lignes de correspondance** de la barre d'outils du **Concepteur DSL**.  Pour afficher les lignes, cliquez à nouveau sur le bouton.  
  
## Modification de la disposition du diagramme  
 Vous pouvez modifier la disposition de la partition **Classes et relations** comme suit.  
  
### Développer\/Réduire  
 Vous pouvez réduire la taille d'un élément de forme de compartiment qui représente une classe de domaine ou une forme en cliquant dessus avec le bouton droit, puis en cliquant sur **Réduire**.  Cette action masque le compartiment **Propriétés de domaine** de la forme.  Pour afficher à nouveau le compartiment **Propriétés de domaine**, cliquez avec le bouton droit sur la forme, puis cliquez sur **Développer**.  
  
### Déplacer vers le haut ou vers le bas  
 Vous pouvez déplacer une classe de domaine ou un élément de diagramme vers le haut ou vers le bas en cliquant avec le bouton droit sur l'élément, puis en cliquant sur **Monter** ou **Descendre**.  Si vous déplacez un élément d'espace réservé affiché comme la cible d'une relation d'incorporation ou de référence, la relation sera également déplacée.  
  
### Développer\/réduire l'arborescence des relations  
 Si une classe de domaine joue le rôle source dans les relations d'incorporation ou de référence avec d'autres classes de domaine, vous pouvez masquer les relations en cliquant avec le bouton droit sur la définition de la classe de domaine, puis en cliquant sur **Réduire l'arborescence des relations**.  Pour afficher les relations, cliquez avec le bouton droit sur l'élément de définition, puis cliquez sur **Développer l'arborescence des relations**.  
  
### Développer\/réduire l'arborescence d'héritage  
 Si une classe de domaine est la classe de base d'autres classes de domaine, vous pouvez masquer l'arborescence d'héritage en cliquant avec le bouton droit sur la définition de la classe de domaine, puis en cliquant sur **Réduire l'arborescence d'héritage**.  Pour afficher l'arborescence d'héritage, cliquez avec le bouton droit sur l'élément de définition, puis cliquez sur **Développer l'arborescence d'héritage**.  
  
### Déplacer l'arborescence ici \(action\)  
 Vous pouvez consolider le diagramme en cliquant avec le bouton droit sur une classe de domaine de l'espace réservé, puis en cliquant sur **Déplacer l'arborescence ici**.  La classe de domaine de l'espace réservé devient un élément de définition et affiche les arborescences d'héritage et de relations.  Le précédent élément de définition devient un élément d'espace réservé s'il est la cible d'une relation ou l'enfant d'une relation d'héritage ; dans le cas contraire, il disparaît.  
  
### Arborescence fractionnée  
 Vous pouvez scinder les arborescences d'héritage ou de relations en cliquant avec le bouton droit sur la définition de la clase de domaine qui les affiche, puis en cliquant sur **Arborescence fractionnée**.  L'élément de définition devient un élément d'espace réservé et la classe de domaine de la définition, ainsi que ses relations d'héritage et de relation, s'affiche désormais en bas de la partition.  
  
### Afficher comme classe  
 Si une relation de domaine possède des relations dérivées, ou si elle a des relations d'incorporation ou de référence avec d'autres relations de domaine, vous pouvez afficher la relation en tant que classe en cliquant avec le bouton droit sur la relation, puis en cliquant sur **Afficher comme classe**.  La relation s'affichera avec un compartiment **Propriétés de domaine** et affichera les relations d'héritage et de relation.  
  
## Voir aussi  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/fr-fr/ca5e84cb-a315-465c-be24-76aa3df276aa)