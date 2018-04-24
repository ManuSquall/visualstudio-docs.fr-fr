---
title: Guide pratique pour personnaliser des diagrammes de classes (Concepteur de classes) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- class diagrams, customizing
- shapes, removing type from class diagrams
- type shapes, removing from class diagrams
- class diagrams, removing type shapes
ms.assetid: e9030aea-c77d-4cc1-b8f6-b6ca469b692d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5a2f58626008ba50f436f7836fe13ca92fcce155
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-customize-class-diagrams-class-designer"></a>Comment : personnaliser des diagrammes de classes (Concepteur de classes)
Vous pouvez modifier la façon dont les diagrammes de classes affichent les informations. Il est possible de personnaliser le diagramme tout entier ou chaque type sur l'aire de conception.  
  
Par exemple, vous pouvez ajuster le niveau de zoom d'un diagramme de classes entier, modifier la manière dont les membres de type sont groupés et ordonnés, masquer ou afficher les relations, et déplacer chaque type ou ensemble de types à votre guise dans le diagramme.  
  
> [!NOTE]
>  Personnaliser la façon dont les formes apparaissent dans le diagramme ne modifie pas le code sous-jacent pour les types représentés dans le diagramme.  
  
Les sections qui contiennent des membres de type, telles que la section Propriétés d'une classe, sont appelées compartiments. Vous pouvez masquer ou afficher des compartiments spécifiques et des membres de type.  
  
**Dans cette rubrique**  
  
-   [Effectuer un zoom avant et arrière dans le diagramme de classes](how-to-customize-class-diagrams.md#ZoomInOut)  
  
-   [Personnaliser le regroupement et le tri des membres de type](how-to-customize-class-diagrams.md#CustomizeGroupingSorting)  
  
-   [Masquer des compartiments sur un type](how-to-customize-class-diagrams.md#HideCompartments)  
  
-   [Masquer des membres spécifiques sur un type](how-to-customize-class-diagrams.md#HideMembers)  
  
-   [Afficher des compartiments et des membres masqués sur un type](how-to-customize-class-diagrams.md#DisplayHiddenCompartmentsAndMemberrs)  
  
-   [Masquer les relations](how-to-customize-class-diagrams.md#HideAssociationAndInheritance)  
  
-   [Afficher les relations masquées](how-to-customize-class-diagrams.md#DisplayAssociationAndInheritance)  
  
-   [Supprimer une forme dans un diagramme de classes](how-to-customize-class-diagrams.md#RemoveCodeAndShape)  
  
-   [Supprimer une forme de type et son code sous-jacent](how-to-customize-class-diagrams.md#DeleteTypeShapeAndCode)  
  
##  <a name="ZoomInOut"></a> Effectuer un zoom avant et arrière dans le diagramme de classes  
  
1.  Ouvrez et sélectionnez un fichier de diagramme de classes dans le Concepteur de classes.  
  
2.  Sur la barre d’outils Concepteur de classes, cliquez sur le bouton **Zoom avant** ou**Zoom arrière** pour modifier le niveau de zoom de l’aire du concepteur.  
  
     ou  
  
     Spécifiez une valeur de zoom particulière. Vous pouvez utiliser la liste déroulante **Zoom** ou taper un niveau de zoom valide (la plage valide est comprise entre 10 % et 400 %).  
  
    > [!NOTE]
    >  La modification du niveau de zoom n'affecte pas l'échelle d'impression de votre diagramme de classes.  
  
##  <a name="CustomizeGroupingSorting"></a> Personnaliser le regroupement et le tri des membres de type  
  
1.  Ouvrez et sélectionnez un fichier de diagramme de classes dans le Concepteur de classes.  
  
2.  Cliquez avec le bouton droit sur une zone vide de l’aire de conception et pointez sur **Membres du groupe**.  
  
3.  Sélectionnez l'une des options disponibles :  
  
    1.  **Grouper par genre** sépare chaque membre de type dans une liste groupée de propriétés, de méthodes, d’événements et de champs. Les groupes dépendent individuellement de la définition d'entités : par exemple, une classe n'affichera pas de groupe d'événements si aucun événement n'a encore été défini pour cette classe.  
  
    2.  **Grouper par accès** sépare chaque membre de type dans une liste groupée en fonction des modificateurs d’accès du membre. Par exemple, Public et Privé.  
  
    3.  **Trier par ordre alphabétique** affiche les éléments qui composent une entité en tant que liste unique classée par ordre alphabétique. La liste est triée dans l'ordre croissant.  
  
##  <a name="HideCompartments"></a> Masquer des compartiments sur un type  
  
1.  Ouvrez et sélectionnez un fichier de diagramme de classes dans le Concepteur de classes.  
  
2.  Cliquez avec le bouton droit sur la catégorie de membre dans le type que vous souhaitez personnaliser (par exemple, sélectionnez le nœud **Méthodes** dans une classe).  
  
3.  Cliquez sur **Masquer le compartiment**.  
  
     Le compartiment sélectionné disparaît du conteneur de type.  
  
##  <a name="HideMembers"></a> Masquer des membres spécifiques sur un type  
  
1.  Ouvrez et sélectionnez un fichier de diagramme de classes dans le Concepteur de classes.  
  
2.  Cliquez avec le bouton droit sur le membre dans le type que vous souhaitez masquer.  
  
3.  Cliquez sur **Masquer**.  
  
     Le membre sélectionné disparaît du conteneur de type.  
  
##  <a name="DisplayHiddenCompartmentsAndMemberrs"></a> Afficher des compartiments et des membres masqués sur un type  
  
1.  Ouvrez et sélectionnez un fichier de diagramme de classes dans le Concepteur de classes.  
  
2.  Cliquez avec le bouton droit sur le nom du type avec le compartiment masqué.  
  
3.  Cliquez sur **Afficher tous les membres**.  
  
     Tous les compartiments et membres masqués s'affichent dans le conteneur de type.  
  
##  <a name="HideAssociationAndInheritance"></a> Masquer les relations  
  
1.  Ouvrez et sélectionnez un fichier de diagramme de classes dans le Concepteur de classes.  
  
2.  Cliquez avec le bouton droit sur la ligne d'association ou d'héritage que vous souhaitez masquer.  
  
3.  Cliquez sur **Masquer** pour les lignes d’association et sur **Masquer la ligne d’héritage** pour les lignes d’héritage.  
  
4.  Cliquez sur **Afficher tous les membres**.  
  
     Tous les compartiments et membres masqués s'affichent dans le conteneur de type.  
  
##  <a name="DisplayAssociationAndInheritance"></a> Afficher les relations masquées  
  
1.  Ouvrez et sélectionnez un fichier de diagramme de classes dans le Concepteur de classes.  
  
2.  Cliquez avec le bouton droit sur le type avec l'association ou l'héritage masqué.  
  
 Cliquez sur **Afficher tous les membres** pour les lignes d’association et sur **Afficher la classe de base** ou **Afficher les classes dérivées** pour les lignes d’héritage.  
  
##  <a name="RemoveCodeAndShape"></a> Supprimer une forme dans un diagramme de classes  
Vous pouvez supprimer une forme de type dans le diagramme de classes sans affecter le code sous-jacent du type. La suppression de formes de type d'un diagramme de classes affecte uniquement ce diagramme : le code sous-jacent qui définit le type et les autres diagrammes qui affichent le type ne sont pas affectés.  
  
1.  Sur le diagramme de classes, sélectionnez la forme de type que vous souhaitez supprimer du diagramme.  
  
2.  Dans le menu **Edition**, choisissez **Supprimer du diagramme**.  
  
     La forme de type et les lignes d'association ou d'héritage connectées à la forme n'apparaissent plus sur le diagramme.  
  
##  <a name="DeleteTypeShapeAndCode"></a> Supprimer une forme de type et son code sous-jacent  
  
1.  Cliquez avec le bouton droit sur la forme dans l'aire de conception.  
  
2.  Sélectionnez **Supprimer le code** dans le menu contextuel.  
  
     La forme est supprimée du diagramme et son code sous-jacent est supprimé du projet.  
  
## <a name="see-also"></a>Voir aussi
[Utilisation des diagrammes de classes](working-with-class-diagrams.md)   
[Guide pratique pour changer la notation entre les membres et les associations](how-to-change-between-member-notation-and-association-notation.md)   
[Guide pratique pour afficher les types existants](how-to-view-existing-types.md)   
[Affichage des types et des relations](viewing-types-and-relationships.md)