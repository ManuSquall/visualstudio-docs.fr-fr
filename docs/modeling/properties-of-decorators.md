---
title: Propriétés des décorateurs
description: Découvrez que les éléments décoratifs sont des icônes, du texte ou des chevrons de développement/réduction qui peuvent apparaître sur des formes ou des connecteurs sur le diagramme.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2f3436bb800142e7c85594f4b05cef6fb45c4489
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390800"
---
# <a name="properties-of-decorators"></a>Propriétés des décorateurs
Les éléments décoratifs sont des icônes, du texte ou des chevrons de développement/réduction qui peuvent apparaître sur des formes ou des connecteurs sur le diagramme. Les tableaux suivants présentent les propriétés des trois types d’éléments décoratifs. Certaines des propriétés s’affichent uniquement sur les éléments décoratifs de forme ou uniquement sur les éléments décoratifs du connecteur.

 Pour plus d’informations, consultez [comment définir un langage de Domain-Specific](../modeling/how-to-define-a-domain-specific-language.md). Pour plus d’informations sur l’utilisation de ces propriétés, consultez [personnalisation et extension d’un langage de Domain-Specific](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="expandcollapse-decorator"></a>Développer/réduire le Decorator

|Propriété|Description|Default|
|-|-|-|
|DisplayName|Nom de l’élément décoratif qui sera affiché dans le concepteur généré.|Développer le dédecoratorur de réduction|
|Nom|Nom de l’élément décoratif.|ExpandCollapseDecorator|
|Notes|Notes informelles associées à cet élément décoratif.|\<none>|
|HorizontalOffset|Décalage horizontal par rapport à la position par défaut de l’élément décoratif, en pouces. (Sur les formes uniquement.)|0|
|VerticalOffset|Décalage vertical par rapport à la position par défaut de l’élément décoratif, en pouces. (Sur les formes uniquement.)|0|
|OffsetFromLine|Décalage de l’élément décoratif de la ligne par rapport à sa position par défaut, en pouces. (Uniquement sur les connecteurs.)|0|
|OffsetFromShape|Décalage de l’élément décoratif de la forme par rapport à sa position par défaut, en pouces. (Uniquement sur les connecteurs.)|0|
|Position|Position par défaut de l’élément décoratif.|SourceTop|

## <a name="icon-decorator"></a>Élément décoratif d’icône

|Propriété|Description|Default|
|-|-|-|
|DefaultIcon|Chemin d’accès de l’icône ou du fichier image à afficher.|\<none>|
|DisplayName|Nom de l’élément décoratif à afficher dans le concepteur généré.|Élément décoratif d’icône|
|Nom|Nom de l’élément décoratif.|IconDecorator|
|Notes|Notes informelles associées à l’élément décoratif.|\<none>|
|HorizontalOffset|Décalage horizontal par rapport à la position par défaut de l’élément décoratif, en pouces. (Sur les formes uniquement.)|0|
|VerticalOffset|Décalage vertical par rapport à la position par défaut de l’élément décoratif, en pouces. (Sur les formes uniquement.)|0|
|OffsetFromLine|Décalage de l’élément décoratif de la ligne par rapport à sa position par défaut, en pouces. (Uniquement sur les connecteurs.)|0|
|OffsetFromShape|Décalage de l’élément décoratif de la forme par rapport à sa position par défaut, en pouces. (Uniquement sur les connecteurs.)|0|
|Position|Position par défaut de l’élément décoratif.|SourceTop|

## <a name="textdecorator"></a>TextDecorator

|Propriété|Description|Default|
|-|-|-|
|DefaultText|Texte par défaut à afficher.|Étiquette|
|DisplayName|Nom de l’élément décoratif à afficher dans le concepteur généré.|Étiquette|
|FontSize|Taille de police du texte affiché dans l’élément décoratif.|8|
|FontStyle|Style de police du texte affiché dans l’élément décoratif.|Normal|
|Nom|Nom de l’élément décoratif.|Étiquette|
|Notes|Notes informelles associées à l’élément décoratif.|\<none>|
|HorizontalOffset|Décalage horizontal par rapport à la position par défaut de l’élément décoratif, en pouces. (Sur les formes uniquement.)|0|
|VerticalOffset|Décalage vertical par rapport à la position par défaut de l’élément décoratif, en pouces. (Sur les formes uniquement.)|0|
|OffsetFromLine|Décalage de l’élément décoratif de la ligne par rapport à sa position par défaut, en pouces. (Uniquement sur les connecteurs.)|0|
|OffsetFromShape|Décalage de l’élément décoratif de la forme par rapport à sa position par défaut, en pouces. (Uniquement sur les connecteurs.)|0|
|Position|Position par défaut de l’élément décoratif.|TargetBottom|

## <a name="see-also"></a>Voir aussi

- [Glossaire des Outils Domain-Specific Language](/previous-versions/bb126564(v=vs.100))