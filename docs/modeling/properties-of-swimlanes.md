---
title: Propriétés des couloirs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.swimlane
helpviewer_keywords:
- Domain-Specific Language, swimlane
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a21473f983c56181e3a5d2fc7f9e97cd1c2d6e7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748261"
---
# <a name="properties-of-swimlanes"></a>Propriétés des couloirs
Vous pouvez ajouter des couloirs à un diagramme. Les couloirs divisent un diagramme en zones verticales ou horizontales. Vous pouvez définir d’autres formes à afficher à l’intérieur des couloirs. Pour plus d’informations, consultez [comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md). Pour plus d’informations sur l’utilisation de ces propriétés, consultez [personnalisation et extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Les couloirs ont les propriétés répertoriées dans le tableau suivant.

|Property|Description|Valeur par défaut|
|-|-|-|
|Couleur de remplissage du corps|Couleur de remplissage du corps du couloir.|ajourée|
|Couleur de remplissage d’en-tête|Couleur de remplissage de l’en-tête du couloir.|Gris foncé|
|Couleur du séparateur|Couleur de la ligne de séparation.|LightGray|
|Style de ligne de séparateur|Style de la ligne de séparation (`Solid`, `Dash`, `Dot`, `DashDot`, `DashDotDot` ou `Custom`).|`Dash`|
|Épaisseur du séparateur|Épaisseur de la ligne de séparation, en pouces.|0,03125|
|Couleur du texte|Couleur utilisée pour les éléments décoratifs de texte associés à ce couloir.|Noir|
|Modificateur d'accès|Niveau d’accès de la classe (`public` ou `internal`).|Public|
|Attributs personnalisés|Utilisé pour ajouter des attributs à la classe de code générée à partir de ce couloir.|\<aucune>|
|Génère un doublon dérivé|Si `True`, une classe de base et une classe partielle (pour prendre en charge la personnalisation via des substitutions) sont générées. Pour plus d’informations, consultez [substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|A un constructeur personnalisé|Si `True`, un constructeur personnalisé est fourni dans le code source. Pour plus d’informations, consultez [substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modificateur d’héritage|Décrit le type d’héritage de la classe de code source qui est généré à partir du couloir (`none`, `abstract` ou `sealed`).|none|
|Couloir de base|Classe de base de ce couloir.|(aucune)|
|Name|Nom de ce couloir.|Nom actuel|
|Espace de noms|Espace de noms affilié à ce couloir.|Espace de noms actuel|
|Type d’info-bulle|Comment l’info-bulle est définie (`fixed`, `variable` ou `none`). Si `fixed`, la valeur de la propriété `Fixed Tooltip Text` est utilisée ; Si `variable`, l’info-bulle est définie dans le code personnalisé.|\<aucune>|
|Notes|Notes informelles associées à ce couloir.|\<aucune>|
|Alignement|Alignement horizontal ou vertical.|Vertical|
|Hauteur initiale|Hauteur initiale de ce couloir, en pouces. S’applique uniquement aux couloirs horizontaux.|0|
|Largeur initiale|Largeur initiale de ce couloir, en pouces. S’applique uniquement aux couloirs verticaux.|0|
|Expose la couleur de texte|Si `True`, l’utilisateur peut définir la couleur d’un couloir dans le concepteur généré. Pour ce faire, cliquez avec le bouton droit sur la forme couloir, puis cliquez sur **Ajouter exposé**.|False|
|Description|Utilisé pour documenter le concepteur généré.|\<aucune>|
|Display Name|Nom qui sera affiché dans le concepteur généré pour faire référence à cette classe couloir.|\<aucune>|
|Texte d’info-bulle fixe|Texte utilisé pour une info-bulle fixe.|\<aucune>|
|Help Keyword|Mot clé utilisé pour indexer l’aide F1 pour ce couloir.|\<aucune>|

## <a name="see-also"></a>Voir aussi

- [Glossaire des Outils Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)