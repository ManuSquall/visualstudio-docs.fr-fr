---
title: Propriétés des décorateurs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 76129141ed293281eeb3179a654f470bcf608bdf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62996797"
---
# <a name="properties-of-decorators"></a>Propriétés des décorateurs
Éléments décoratifs sont des icônes, texte ou développer/réduire les chevrons qui peuvent apparaître dans les formes ou des connecteurs sur le diagramme. Les tableaux suivants indiquent les propriétés pour les trois types d’élément décoratif. Certaines propriétés s’affichent uniquement sur les éléments décoratifs ou uniquement sur les éléments décoratifs de connecteur.

 Pour plus d’informations, consultez [comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md). Pour plus d’informations sur l’utilisation de ces propriétés, consultez [personnalisation et extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="expandcollapse-decorator"></a>Développer/réduire un élément décoratif

|Propriété|Description|Par défaut|
|-|-|-|
|DisplayName|Le nom de l’élément décoratif qui s’affichera dans le concepteur généré.|Développez réduire le décorateur|
|Nom|Le nom de l’élément décoratif.|ExpandCollapseDecorator|
|Notes|Remarques informelles associées à cet élément décoratif.|\<aucune>|
|HorizontalOffset|Le décalage horizontal par rapport à la position par défaut de l’élément décoratif, en pouces. (Sur les formes uniquement.)|0|
|VerticalOffset|Le décalage vertical par rapport à la position par défaut de l’élément décoratif, en pouces. (Sur les formes uniquement.)|0|
|OffsetFromLine|Le décalage de l’élément décoratif à partir de la ligne, par rapport à sa position par défaut, en pouces. (Sur les connecteurs uniquement.)|0|
|OffsetFromShape|Le décalage de l’élément décoratif à partir de la forme, par rapport à sa position par défaut, en pouces. (Sur les connecteurs uniquement.)|0|
|Position|La position par défaut de l’élément décoratif.|SourceTop|

## <a name="icon-decorator"></a>Icône Decorator

|Propriété|Description|Par défaut|
|-|-|-|
|DefaultIcon|Le chemin d’accès du fichier icône ou une image à afficher.|\<aucune>|
|DisplayName|Le nom de l’élément décoratif à afficher dans le concepteur généré.|Icône Decorator|
|Nom|Le nom de l’élément décoratif.|IconDecorator|
|Notes|Remarques informelles associées à l’élément décoratif.|\<aucune>|
|HorizontalOffset|Le décalage horizontal par rapport à la position par défaut de l’élément décoratif, en pouces. (Sur les formes uniquement.)|0|
|VerticalOffset|Le décalage vertical par rapport à la position par défaut de l’élément décoratif, en pouces. (Sur les formes uniquement.)|0|
|OffsetFromLine|Le décalage de l’élément décoratif à partir de la ligne, par rapport à sa position par défaut, en pouces. (Sur les connecteurs uniquement.)|0|
|OffsetFromShape|Le décalage de l’élément décoratif à partir de la forme, par rapport à sa position par défaut, en pouces. (Sur les connecteurs uniquement.)|0|
|Position|La position par défaut de l’élément décoratif.|SourceTop|

## <a name="textdecorator"></a>TextDecorator

|Propriété|Description|Par défaut|
|-|-|-|
|DefaultText|Le texte par défaut à afficher.|Etiquette|
|DisplayName|Le nom de l’élément décoratif à afficher dans le concepteur généré.|Etiquette|
|FontSize|La taille de police pour le texte qui est affiché dans l’élément décoratif.|8|
|FontStyle|Le style de police pour le texte qui est affiché dans l’élément décoratif.|Normale|
|Nom|Le nom de l’élément décoratif.|Etiquette|
|Notes|Remarques informelles associées à l’élément décoratif.|\<aucune>|
|HorizontalOffset|Le décalage horizontal par rapport à la position par défaut de l’élément décoratif, en pouces. (Sur les formes uniquement.)|0|
|VerticalOffset|Le décalage vertical par rapport à la position par défaut de l’élément décoratif, en pouces. (Sur les formes uniquement.)|0|
|OffsetFromLine|Le décalage de l’élément décoratif à partir de la ligne, par rapport à sa position par défaut, en pouces. (Sur les connecteurs uniquement.)|0|
|OffsetFromShape|Le décalage de l’élément décoratif à partir de la forme, par rapport à sa position par défaut, en pouces. (Sur les connecteurs uniquement.)|0|
|Position|La position par défaut de l’élément décoratif.|TargetBottom|

## <a name="see-also"></a>Voir aussi

- [Glossaire des Outils Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)