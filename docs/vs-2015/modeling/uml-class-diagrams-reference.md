---
title: 'Diagrammes de classes UML : référence | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.common.generalization.properties
- vs.teamarch.logicalclassdiagram.toolbox
- vs.teamarch.UMLModelExplorer.association
- vs.teamarch.common.unspecifiedtype.properties
- vs.teamarch.logicalclassdiagram.diagram
- vs.teamarch.UMLModelExplorer.logicalclassdiagram
- vs.teamarch.UMLModelExplorer.generalization
- vs.teamarch.common.unspecifiedtype
helpviewer_keywords:
- UML diagrams, class
- diagrams - modeling, class
- UML, class diagrams
- class diagrams - UML
- diagrams - modeling, UML class
ms.assetid: b7c88be0-0d86-4d65-af74-f37e8812d20f
caps.latest.revision: 43
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 06e83e254cad77d4ede9716a18a51f6476fb51ad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850178"
---
# <a name="uml-class-diagrams-reference"></a>Diagrammes de classes UML : référence
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un diagramme de classes UML décrit les structures des objets et des informations utilisés par votre application, à la fois en interne et en communication avec ses utilisateurs. Il décrit les informations sans référence à une implémentation particulière. Ses classes et relations peuvent être implémentées de différentes manières, par exemple avec des tables de bases de données, des nœuds XML ou des compositions d'objets logiciels.

> [!NOTE]
> Cette rubrique concerne les diagrammes de classes UML. Il existe un autre genre de diagramme de classes, le diagramme de classes .NET, qui sert à visualiser le code de programme. Pour plus d’informations, consultez [conception et affichage des classes et des types](https://msdn.microsoft.com/library/ab7aty24.aspx).

 Pour créer un diagramme de classes UML, dans le menu **architecture** , choisissez **nouveau diagramme UML ou diagramme de couche**. Pour plus d’informations sur la façon de dessiner des diagrammes de classes UML, consultez [diagrammes de classes UML : indications](../modeling/uml-class-diagrams-guidelines.md). Pour plus d’informations sur la création et le dessin de diagrammes de modélisation, consultez [modifier des modèles et des diagrammes UML](../modeling/edit-uml-models-and-diagrams.md).

 Pour connaître les versions de Visual Studio qui prennent en charge cette fonctionnalité, consultez [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="reading-class-diagrams"></a>Lecture des diagrammes de classes
 Le tableau de cette section décrit les éléments visibles sur un diagramme de classes UML. Pour plus d'informations sur les propriétés de ces éléments, consultez les rubriques suivantes :

- [Propriétés de types dans des diagrammes de classes UML](../modeling/properties-of-types-on-uml-class-diagrams.md)

- [Propriétés d’attributs dans des diagrammes de classes UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)

- [Propriétés d’opérations dans des diagrammes de classes UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)

- [Propriétés des associations dans les diagrammes de classes UML](../modeling/properties-of-associations-on-uml-class-diagrams.md)

  ![Trois classes affichant des relations et des propriétés](../modeling/media/uml-classovreading.png "UML_ClassOvReading")

| **Forme** |       **Element**        |                                                                                                                                                             **Description**                                                                                                                                                              |
|-----------|--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     1     |        **Classe**         |                                                           Définition d'objets qui partagent des caractéristiques structurelles ou comportementales données. Pour plus d’informations, consultez [Propriétés de types dans des diagrammes de classes UML](../modeling/properties-of-types-on-uml-class-diagrams.md).                                                            |
|     1     |        Classifieur        |                                                                                                             Nom général d'une classe, d'une interface ou d'une énumération. Les composants, les cas d'usage et les acteurs sont également des classifieurs.                                                                                                             |
|     2     | Contrôle Réduire / Développer |                                                                                         Si vous ne pouvez pas voir les détails d'un classifieur, cliquez sur l'Expander dans la partie supérieure gauche du classifieur. Vous devrez peut-être également cliquer sur le signe plus [+] sur chaque segment.                                                                                         |
|     3     |      **Attribut**       |   Valeur typée attachée à chaque instance d'un classifieur.<br /><br /> Pour ajouter un attribut, cliquez sur la section **attributs** , puis appuyez sur **entrée**. Tapez la signature de l'attribut. Pour plus d’informations, consultez [propriétés d’attributs dans des diagrammes de classes UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md).   |
|     4     |      **opération**       | Méthode ou fonction qui peut être exécutée par des instances d'un classifieur. Pour ajouter une opération, cliquez sur la section **opérations** , puis appuyez sur **entrée**. Tapez la signature de l'opération. Pour plus d’informations, consultez [propriétés d’opérations sur des diagrammes de classes UML](../modeling/properties-of-operations-on-uml-class-diagrams.md). |
|     5     |     **Association**      |                                                                  Relation entre les membres de deux classifieurs. Pour plus d’informations, consultez [propriétés d’associations dans des diagrammes de classes UML](../modeling/properties-of-associations-on-uml-class-diagrams.md).                                                                   |
|    5a     |     **Agrégation**      |                                                                                                    Association représentant une relation de propriété partagée. La propriété **Aggregation** du rôle propriétaire a la valeur **partagé**.                                                                                                     |
|    5b     |     **Composition**      |                                                                                                      Association représentant une relation de partie entière. La propriété **Aggregation** du rôle propriétaire a la valeur **composite**.                                                                                                      |
|     6     |   **Nom de l’association**   |                                                                                                                                         Nom d'une association. Le nom peut être laissé vide.                                                                                                                                          |
|     7     |      **Nom du rôle**       |                       Nom d'un rôle, autrement dit une extrémité d'une association. Peut être utilisé pour faire référence à l'objet associé. Dans l'illustration précédente, pour toute commande `O`, `O.ChosenMenu` est son Menu associé.<br /><br /> Chaque rôle possède ses propres propriétés, répertoriées sous les propriétés de l'association.                       |
|     8     |     **Multiplicité**     |                                         Indique combien des objets à cette extrémité peuvent être liés à chaque objet à l'autre extrémité. Dans l'exemple, chaque commande doit être liée à exactement un menu.<br /><br /> **\\**\* signifie qu’il n’y a pas de limite supérieure pour le nombre de liens qui peuvent être créés.                                         |
|     9     |    **Généralisation**    |  Le classifieur *spécifique* hérite une partie de sa définition du classifieur *général* . Le classifieur général se trouve à l'extrémité flèchée du connecteur. Les attributs, associations et opérations sont hérités par le classifieur spécifique.<br /><br /> Utilisez l’outil **héritage** pour créer une généralisation entre deux classifieurs.   |

 ![Package contenant une interface et une énumération](../modeling/media/uml-classovpackage.png "UML_ClassOvPackage")

|Forme|Élément|Description|
|-----------|-------------|-----------------|
|10|**Interface**|Définition d'une partie du comportement extérieurement visible d'un objet. Pour plus d’informations, consultez [Propriétés de types dans des diagrammes de classes UML](../modeling/properties-of-types-on-uml-class-diagrams.md).|
|11|**Enumeration**|Classifieur composé d'un ensemble de valeurs littérales.|
|12|**Package**|Groupe de classifieurs, associations, actions, lignes de vie, composants et packages. Un diagramme de classes logique montre que les packages et les classifieurs de membres sont contenus dans le package.<br /><br /> Les noms sont étendus au sein des packages afin que **Class1** dans **package1** soit distinct de **Class1** en dehors de ce package. Le nom du package s’affiche dans les propriétés de **nom qualifié** de son contenu.<br /><br /> Vous pouvez définir la propriété **package lié** d’un diagramme UML pour faire référence à un package. Tous les éléments que vous créez dans ce diagramme feront alors partie du package. Ils s’affichent sous le package dans l' **Explorateur de modèles UML**.|
|13|**Importer**|Relation entre des packages, indiquant qu'un package inclut toutes les définitions d'un autre.|
|14|**Dépendance**|La définition ou l'implémentation du classifieur dépendant peut changer si le classifieur à l'extrémité fléchée est modifié.|

 ![Réalisation présentée avec connecteur et lollipop](../modeling/media/uml-classovrealize.png "UML_ClassOvRealize")

|Forme|**Element**|Description|
|-----------|-----------------|-----------------|
|15|**Réalisation**|La classe implémente les opérations et les attributs définis par l'interface.<br /><br /> Utilisez l’outil d' **héritage** pour créer une réalisation entre une classe et une interface.|
|16|**Réalisation**|Autre présentation de la même relation. L'étiquette sur le symbole d'interface Lollipop identifie l'interface.<br /><br /> Pour créer cette présentation, sélectionnez une relation de réalisation existante. Une balise d'action apparaît près de l'association. Cliquez sur la balise d’action, puis sur **afficher sous forme d’interface Lollipop**.|

## <a name="see-also"></a>Voir aussi
 [Modifier des diagrammes et des modèles UML](../modeling/edit-uml-models-and-diagrams.md) [diagrammes de classes UML : indications](../modeling/uml-class-diagrams-guidelines.md) [Propriétés de types dans des diagrammes de classes UML](../modeling/properties-of-types-on-uml-class-diagrams.md) propriétés [d’attributs dans des diagrammes de classes UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md) [propriétés d’opérations sur des diagrammes de classes UML](../modeling/properties-of-operations-on-uml-class-diagrams.md) [propriétés d’associations dans des diagrammes de classes](../modeling/properties-of-associations-on-uml-class-diagrams.md) UML
