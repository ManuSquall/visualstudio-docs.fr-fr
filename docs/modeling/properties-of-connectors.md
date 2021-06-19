---
title: Propriétés des connecteurs
description: Découvrez que les connecteurs représentent les relations de domaine dans un concepteur généré et que vous utilisez ces propriétés pour personnaliser et étendre un langage spécifique à un domaine.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, connectors
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 43f55aecf134bf8e4d043a4fc7f6ffa2201f8e95
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390813"
---
# <a name="properties-of-connectors"></a>Propriétés des connecteurs
Les connecteurs représentent les relations de domaine dans un concepteur généré.

 Pour plus d’informations, consultez [comment définir un langage de Domain-Specific](../modeling/how-to-define-a-domain-specific-language.md). Pour plus d’informations sur l’utilisation de ces propriétés, consultez [personnalisation et extension d’un langage de Domain-Specific](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Les propriétés des connecteurs sont répertoriées dans le tableau suivant.

|Propriété|Description|Default|
|-|-|-|
|Couleur|Couleur de ce connecteur.|Noir|
|Style de tiret|Style de tiret pour la ligne de ce connecteur (plein, tiret, point, tiret point, tiret point point ou personnalisé).|Unie|
|Style de fin de la source|Style de l’extrémité source de ce connecteur (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond ou None).|Aucun|
|Style de fin cible|Style de l’extrémité cible de ce connecteur (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond ou None).|Aucun|
|Couleur du texte|Couleur utilisée pour les éléments décoratifs de texte associés à ce connecteur.|Noir|
|Thickness|Épaisseur de la ligne de ce connecteur, mesurée en pouces.|0,03125|
|Modificateur d'accès|Niveau d’accès de la classe ( `public` ou `internal` ).|Public|
|Attributs personnalisés|Utilisé pour ajouter des attributs à la classe de code source qui est générée à partir de ce connecteur.|\<none>|
|Génère un doublon dérivé|Si `True` la valeur est, une classe de base et une classe partielle (pour prendre en charge la personnalisation via des substitutions) sont générées. Pour plus d’informations, consultez [substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|A un constructeur personnalisé|Si `True` , un constructeur personnalisé est fourni dans le code source. Pour plus d’informations, consultez [substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modificateur d’héritage|Décrit le type d’héritage de la classe de code source qui est généré à partir du connecteur ( `none` , `abstract` ou `sealed` ).|aucun|
|Connecteur de base|Classe de base de ce connecteur.|(aucun)|
|Nom|Nom de ce connecteur.|Nom actuel|
|Espace de noms|Espace de noms affilié à ce connecteur.|Espace de noms actuel|
|Type d’info-bulle|Comment l’info-bulle est définie (Fixed, variable ou None). Si elle est fixe, la valeur de la `Fixed Tooltip Text` propriété est utilisée comme info-bulle ; si la variable est, l’info-bulle est définie dans le code personnalisé.|\<none>|
|Notes|Notes informelles associées à ce connecteur.|\<none>|
|Style de routage|Style utilisé pour router le connecteur. Un `Rectilinear` connecteur fait en sorte que les virages à angle droit s’effectuent comme requis ; un `Straight` connecteur ne le fait pas.|Rectilinear|
|Couleur exposée en tant que propriété<br /><br /> Style de tiret exposé en tant que propriété<br /><br /> Epaisseur exposée en tant que propriété<br /><br /> Expose la couleur de texte|Si `True` la valeur est, l’utilisateur peut définir la propriété déclarée d’une forme. Pour ce faire, cliquez avec le bouton droit sur la définition de la forme, puis cliquez sur **Ajouter exposé**.|False|
|Description|Utilisé pour documenter le concepteur généré.|\<none>|
|Nom d’affichage|Nom qui sera affiché dans le concepteur généré pour ce connecteur.|\<none>|
|Texte d’info-bulle fixe|Texte utilisé pour une info-bulle fixe.|\<none>|
|Help Keyword|Mot clé utilisé pour indexer l’aide F1 pour cet élément.|\<none>|

## <a name="see-also"></a>Voir aussi

- [Glossaire des Outils Domain-Specific Language](/previous-versions/bb126564(v=vs.100))