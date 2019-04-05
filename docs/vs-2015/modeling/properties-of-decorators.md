---
title: Propriétés des décorateurs | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
ms.assetid: f6322fe5-dc08-4d32-a6b3-0bd18879136d
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 288e0e4d017302a41b3267a3ae751573ab849b64
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58947665"
---
# <a name="properties-of-decorators"></a>Propriétés des décorateurs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Éléments décoratifs sont des icônes, texte ou développer/réduire les chevrons qui peuvent apparaître dans les formes ou des connecteurs sur le diagramme. Les tableaux suivants indiquent les propriétés pour les trois types d’élément décoratif. Certaines propriétés s’affichent uniquement sur les éléments décoratifs ou uniquement sur les éléments décoratifs de connecteur.  
  
 Pour plus d’informations, consultez [comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md). Pour plus d’informations sur l’utilisation de ces propriétés, consultez [personnalisation et extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
## <a name="expandcollapse-decorator"></a>Développer/réduire un élément décoratif  
  
|Propriété|Description|Par défaut|  
|--------------|-----------------|-------------|  
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
|--------------|-----------------|-------------|  
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
|--------------|-----------------|-------------|  
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
 [Glossaire des Outils Domain-Specific Language](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
