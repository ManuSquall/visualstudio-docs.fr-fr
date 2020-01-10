---
title: Propriétés des décorateurs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3374c07cac01104354b2ce41abddbeabbec0a373
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75566135"
---
# <a name="properties-of-decorators"></a>Propriétés des décorateurs
Les éléments décoratifs sont des icônes, du texte ou des chevrons de développement/réduction qui peuvent apparaître sur des formes ou des connecteurs sur le diagramme. Les tableaux suivants présentent les propriétés des trois types d’éléments décoratifs. Certaines des propriétés s’affichent uniquement sur les éléments décoratifs de forme ou uniquement sur les éléments décoratifs du connecteur.

 Pour plus d’informations, consultez [comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md). Pour plus d’informations sur l’utilisation de ces propriétés, consultez [personnalisation et extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="expandcollapse-decorator"></a>Développer/réduire le Decorator

|Les|Description|Valeur par défaut|
|-|-|-|
|DisplayName|Nom de l’élément décoratif qui sera affiché dans le concepteur généré.|Développer le dédecoratorur de réduction|
|Name|Nom de l’élément décoratif.|ExpandCollapseDecorator|
|Remarques|Notes informelles associées à cet élément décoratif.|\<aucune>|
|HorizontalOffset|Décalage horizontal par rapport à la position par défaut de l’élément décoratif, en pouces. (Sur les formes uniquement.)|0|
|VerticalOffset|Décalage vertical par rapport à la position par défaut de l’élément décoratif, en pouces. (Sur les formes uniquement.)|0|
|OffsetFromLine|Décalage de l’élément décoratif de la ligne par rapport à sa position par défaut, en pouces. (Uniquement sur les connecteurs.)|0|
|OffsetFromShape|Décalage de l’élément décoratif de la forme par rapport à sa position par défaut, en pouces. (Uniquement sur les connecteurs.)|0|
|Position|Position par défaut de l’élément décoratif.|SourceTop|

## <a name="icon-decorator"></a>Élément décoratif d’icône

|Les|Description|Valeur par défaut|
|-|-|-|
|DefaultIcon|Chemin d’accès de l’icône ou du fichier image à afficher.|\<aucune>|
|DisplayName|Nom de l’élément décoratif à afficher dans le concepteur généré.|Élément décoratif d’icône|
|Name|Nom de l’élément décoratif.|IconDecorator|
|Remarques|Notes informelles associées à l’élément décoratif.|\<aucune>|
|HorizontalOffset|Décalage horizontal par rapport à la position par défaut de l’élément décoratif, en pouces. (Sur les formes uniquement.)|0|
|VerticalOffset|Décalage vertical par rapport à la position par défaut de l’élément décoratif, en pouces. (Sur les formes uniquement.)|0|
|OffsetFromLine|Décalage de l’élément décoratif de la ligne par rapport à sa position par défaut, en pouces. (Uniquement sur les connecteurs.)|0|
|OffsetFromShape|Décalage de l’élément décoratif de la forme par rapport à sa position par défaut, en pouces. (Uniquement sur les connecteurs.)|0|
|Position|Position par défaut de l’élément décoratif.|SourceTop|

## <a name="textdecorator"></a>TextDecorator

|Les|Description|Valeur par défaut|
|-|-|-|
|DefaultText|Texte par défaut à afficher.|Ajouter des contrôles|
|DisplayName|Nom de l’élément décoratif à afficher dans le concepteur généré.|Ajouter des contrôles|
|FontSize|Taille de police du texte affiché dans l’élément décoratif.|8|
|FontStyle|Style de police du texte affiché dans l’élément décoratif.|Regular|
|Name|Nom de l’élément décoratif.|Ajouter des contrôles|
|Remarques|Notes informelles associées à l’élément décoratif.|\<aucune>|
|HorizontalOffset|Décalage horizontal par rapport à la position par défaut de l’élément décoratif, en pouces. (Sur les formes uniquement.)|0|
|VerticalOffset|Décalage vertical par rapport à la position par défaut de l’élément décoratif, en pouces. (Sur les formes uniquement.)|0|
|OffsetFromLine|Décalage de l’élément décoratif de la ligne par rapport à sa position par défaut, en pouces. (Uniquement sur les connecteurs.)|0|
|OffsetFromShape|Décalage de l’élément décoratif de la forme par rapport à sa position par défaut, en pouces. (Uniquement sur les connecteurs.)|0|
|Position|Position par défaut de l’élément décoratif.|TargetBottom|

## <a name="see-also"></a>Voir aussi

- [Glossaire des Outils Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
