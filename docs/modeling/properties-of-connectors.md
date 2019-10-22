---
title: Propriétés des connecteurs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, connectors
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2244b191bac2456886368992d1dc8f1c571dc227
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658257"
---
# <a name="properties-of-connectors"></a>Propriétés des connecteurs
Les connecteurs représentent les relations de domaine dans un concepteur généré.

 Pour plus d’informations, consultez [comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md). Pour plus d’informations sur l’utilisation de ces propriétés, consultez [personnalisation et extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Les propriétés des connecteurs sont répertoriées dans le tableau suivant.

|Property|Description|Valeur par défaut|
|-|-|-|
|Color|Couleur de ce connecteur.|Noir|
|Style de tiret|Style de tiret pour la ligne de ce connecteur (plein, tiret, point, tiret point, tiret point point ou personnalisé).|Unie|
|Style de fin de la source|Style de l’extrémité source de ce connecteur (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond ou None).|aucune.|
|Style de fin cible|Style de l’extrémité cible de ce connecteur (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond ou None).|aucune.|
|Couleur du texte|Couleur utilisée pour les éléments décoratifs de texte associés à ce connecteur.|Noir|
|Thickness|Épaisseur de la ligne de ce connecteur, mesurée en pouces.|0,03125|
|Modificateur d'accès|Niveau d’accès de la classe (`public` ou `internal`).|Public|
|Attributs personnalisés|Utilisé pour ajouter des attributs à la classe de code source qui est générée à partir de ce connecteur.|\<aucune>|
|Génère un doublon dérivé|Si `True`, une classe de base et une classe partielle (pour prendre en charge la personnalisation via des substitutions) sont générées. Pour plus d’informations, consultez [substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|A un constructeur personnalisé|Si `True`, un constructeur personnalisé est fourni dans le code source. Pour plus d’informations, consultez [substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modificateur d’héritage|Décrit le type d’héritage de la classe de code source qui est généré à partir du connecteur (`none`, `abstract` ou `sealed`).|none|
|Connecteur de base|Classe de base de ce connecteur.|(aucune)|
|Name|Nom de ce connecteur.|Nom actuel|
|Espace de noms|Espace de noms affilié à ce connecteur.|Espace de noms actuel|
|Type d’info-bulle|Comment l’info-bulle est définie (Fixed, variable ou None). S’il est corrigé, la valeur de la propriété `Fixed Tooltip Text` est utilisée comme info-bulle ; Si la variable est, l’info-bulle est définie dans le code personnalisé.|\<aucune>|
|Notes|Notes informelles associées à ce connecteur.|\<aucune>|
|Style de routage|Style utilisé pour router le connecteur. Un connecteur `Rectilinear` fait en sorte que les virages à angle droit s’effectuent comme requis ; ce n’est pas le cas d’un connecteur `Straight`.|Rectilinear|
|Couleur exposée en tant que propriété<br /><br /> Style de tiret exposé en tant que propriété<br /><br /> Epaisseur exposée en tant que propriété<br /><br /> Expose la couleur de texte|Si `True`, l’utilisateur peut définir la propriété déclarée d’une forme. Pour ce faire, cliquez avec le bouton droit sur la définition de la forme, puis cliquez sur **Ajouter exposé**.|False|
|Description|Utilisé pour documenter le concepteur généré.|\<aucune>|
|Display Name|Nom qui sera affiché dans le concepteur généré pour ce connecteur.|\<aucune>|
|Texte d’info-bulle fixe|Texte utilisé pour une info-bulle fixe.|\<aucune>|
|Help Keyword|Mot clé utilisé pour indexer l’aide F1 pour cet élément.|\<aucune>|

## <a name="see-also"></a>Voir aussi

- [Glossaire des Outils Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)