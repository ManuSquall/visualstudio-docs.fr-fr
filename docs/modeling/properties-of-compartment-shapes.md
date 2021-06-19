---
title: Propriétés des formes de compartiment
description: Découvrez que les formes compartiments sont l’une des formes que vous pouvez utiliser pour afficher une classe de domaine dans un langage spécifique à un domaine.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.compartmentshape
helpviewer_keywords:
- Domain-Specific Language, compartment shape
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0ec84057bfe7d49760a8f95132a30e8c927f60f0
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390826"
---
# <a name="properties-of-compartment-shapes"></a>Propriétés des formes de compartiment
Les formes compartiments sont l’une des formes que vous pouvez utiliser pour afficher une classe de domaine dans un langage spécifique à un domaine. Vous pouvez développer et réduire les compartiments.

 Pour plus d’informations, consultez [comment définir un langage de Domain-Specific](../modeling/how-to-define-a-domain-specific-language.md). Pour plus d’informations sur l’utilisation de ces propriétés, consultez [personnalisation et extension d’un langage de Domain-Specific](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Les formes de compartiment ont les propriétés qui sont répertoriées dans le tableau suivant.

|Propriété|Description|Default|
|-|-|-|
|État de réduction par défaut développé|Si `Expanded` la, les compartiments sont affichés lors de la création. Si `Collapsed` , ils ne le sont pas.|Développé|
|Couleur de remplissage|Couleur de remplissage de cette forme.|Blancs|
|Mode dégradé de remplissage|Mode de remplissage dégradé de cette forme.|Horizontal|
|Géométrie|Géométrie de cette forme (rectangle ou rectangle arrondi).|Rectangle|
|A des points de connexion par défaut|Si `True` la forme est, la forme utilise les points de connexion du haut, du bas, de gauche et de droite dans le concepteur généré.|False|
|En-tête de compartiment unique visible|Si `False` , et que la forme a un seul compartiment, l’en-tête du compartiment n’est pas visible.|True|
|Couleur de contour|Couleur de contour de cette forme.|Noir|
|Style de tiret de contour|Style de tiret de contour de cette forme (Uni, tiret, point, tiret point, tiret point point, personnalisé).|Unie|
|Épaisseur du contour|Épaisseur de contour de cette forme.|0,03125|
|Couleur du texte|Couleur utilisée pour les éléments décoratifs de texte associés à cette forme.|Noir|
|Modificateur d'accès|Niveau d’accès de la forme de compartiment ( `public` ou `internal` ).|Public|
|Attributs personnalisés|Utilisé pour ajouter des attributs à la classe de code source générée à partir de cette forme de compartiment|\<none>|
|Génère un doublon dérivé|Si `True` la valeur est, une classe de base et une classe partielle (pour prendre en charge la personnalisation via des substitutions) sont générées. Pour plus d’informations, consultez [substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|A un constructeur personnalisé|Si `True` , un constructeur personnalisé est fourni dans le code source. Pour plus d’informations, consultez [substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modificateur d’héritage|Décrit le type d’héritage de la classe de code source qui est généré à partir de la forme de compartiment ( `none` , `abstract` ou `sealed` ).|Aucun|
|Forme de compartiment de base|Classe de base de cette forme.|(aucun)|
|Nom|Nom de cette forme.|Nom actuel|
|Espace de noms|Espace de noms affilié à cette forme.|Espace de noms actuel|
|Type d’info-bulle|Comment l’info-bulle est définie (Fixed, variable ou None). Si elle est fixe, la valeur de la `Fixed Tooltip Text` propriété est utilisée comme info-bulle ; si la variable est, l’info-bulle est définie dans le code personnalisé.|aucun|
|Notes|Notes informelles associées à cette forme.|\<none>|
|Hauteur initiale|Hauteur initiale de cette forme, en pouces. Pour les formes de compartiment, il s’agit de la hauteur de la section d’en-tête uniquement et elle ne peut pas être redimensionnée.|1|
|Largeur initiale|Largeur initiale de cette forme, en pouces.|1.5|
|Couleur de remplissage exposée en tant que propriété<br /><br /> Mode dégradé de remplissage exposé<br /><br /> Couleur de contour exposée en tant que propriété<br /><br /> Exposé du style de tiret de contour en tant que propriété<br /><br /> Exposer l’épaisseur de la structure en tant que propriété<br /><br /> Expose la couleur de texte|Si `True` la valeur est, l’utilisateur peut définir la propriété déclarée d’une forme. Pour ce faire, cliquez avec le bouton droit sur la définition de la forme, puis cliquez sur **Ajouter exposé**.|False|
|Description|Utilisé pour documenter le concepteur généré.|\<none>|
|Nom d’affichage|Nom qui sera affiché dans le concepteur généré pour cette forme.|\<none>|
|Texte d’info-bulle fixe|Texte utilisé pour une info-bulle fixe.|\<none>|
|Help Keyword|Mot clé utilisé pour indexer l’aide F1 pour cette forme.|\<none>|

## <a name="see-also"></a>Voir aussi

- [Glossaire des Outils Domain-Specific Language](/previous-versions/bb126564(v=vs.100))