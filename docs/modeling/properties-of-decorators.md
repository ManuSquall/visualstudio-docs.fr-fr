---
title: "Propriétés des éléments décoratifs | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, decorators
ms.assetid: f6322fe5-dc08-4d32-a6b3-0bd18879136d
caps.latest.revision: "23"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 23288d1afe9b9c0a181a5d978b1956071b683218
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="properties-of-decorators"></a>Propriétés des décorateurs
Éléments décoratifs sont des icônes, texte ou développer/réduire les chevrons qui peuvent s’afficher sur les formes ou des connecteurs du diagramme. Les tableaux suivants présentent les propriétés pour les trois types de decorator. Certaines propriétés s’affichent uniquement sur les éléments décoratifs de forme ou seulement sur des éléments décoratifs du connecteur.  
  
 Pour plus d’informations, consultez [comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md). Pour plus d’informations sur la façon d’utiliser ces propriétés, consultez [personnalisation et l’extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
## <a name="expandcollapse-decorator"></a>Développer/réduire le Decorator  
  
|Propriété|Description|Par défaut|  
|--------------|-----------------|-------------|  
|DisplayName|Le nom de l’élément décoratif qui s’affichera dans le concepteur généré.|Développez Collapse Decorator|  
|Nom|Le nom de l’élément décoratif.|ExpandCollapseDecorator|  
|Remarques|Notes informelles qui sont associés à cet élément décoratif.|\<Aucun >|  
|HorizontalOffset|Le décalage horizontal par rapport à la position par défaut de l’élément décoratif, exprimée en pouces. (Sur les formes uniquement.)|0|  
|VerticalOffset|Le décalage vertical, par rapport à la position par défaut de l’élément décoratif, exprimée en pouces. (Sur les formes uniquement.)|0|  
|OffsetFromLine|Le décalage de l’élément décoratif à partir de la ligne, par rapport à sa position par défaut, exprimée en pouces. (Sur les connecteurs uniquement.)|0|  
|OffsetFromShape|Le décalage de l’élément décoratif de la forme, par rapport à sa position par défaut, exprimée en pouces. (Sur les connecteurs uniquement.)|0|  
|Position|La position par défaut de l’élément décoratif.|SourceTop|  
  
## <a name="icon-decorator"></a>Icône Decorator  
  
|Propriété|Description|Par défaut|  
|--------------|-----------------|-------------|  
|DefaultIcon|Le chemin d’accès du fichier icône ou image à afficher.|\<Aucun >|  
|DisplayName|Le nom de l’élément décoratif à afficher dans le concepteur généré.|Icône Decorator|  
|Nom|Le nom de l’élément décoratif.|IconDecorator|  
|Remarques|Notes informelles qui sont associés à l’élément décoratif.|\<Aucun >|  
|HorizontalOffset|Le décalage horizontal par rapport à la position par défaut de l’élément décoratif, exprimée en pouces. (Sur les formes uniquement.)|0|  
|VerticalOffset|Le décalage vertical, par rapport à la position par défaut de l’élément décoratif, exprimée en pouces. (Sur les formes uniquement.)|0|  
|OffsetFromLine|Le décalage de l’élément décoratif à partir de la ligne, par rapport à sa position par défaut, exprimée en pouces. (Sur les connecteurs uniquement.)|0|  
|OffsetFromShape|Le décalage de l’élément décoratif de la forme, par rapport à sa position par défaut, exprimée en pouces. (Sur les connecteurs uniquement.)|0|  
|Position|La position par défaut de l’élément décoratif.|SourceTop|  
  
## <a name="textdecorator"></a>TextDecorator  
  
|Propriété|Description|Par défaut|  
|--------------|-----------------|-------------|  
|DefaultText|Le texte par défaut à afficher.|Ajouter des contrôles|  
|DisplayName|Le nom de l’élément décoratif à afficher dans le concepteur généré.|Ajouter des contrôles|  
|FontSize|La taille de police pour le texte qui s’affiche dans le decorator.|8|  
|FontStyle|Le style de police du texte qui s’affiche dans le decorator.|Normale|  
|Nom|Le nom de l’élément décoratif.|Ajouter des contrôles|  
|Remarques|Notes informelles qui sont associés à l’élément décoratif.|\<Aucun >|  
|HorizontalOffset|Le décalage horizontal par rapport à la position par défaut de l’élément décoratif, exprimée en pouces. (Sur les formes uniquement.)|0|  
|VerticalOffset|Le décalage vertical, par rapport à la position par défaut de l’élément décoratif, exprimée en pouces. (Sur les formes uniquement.)|0|  
|OffsetFromLine|Le décalage de l’élément décoratif à partir de la ligne, par rapport à sa position par défaut, exprimée en pouces. (Sur les connecteurs uniquement.)|0|  
|OffsetFromShape|Le décalage de l’élément décoratif de la forme, par rapport à sa position par défaut, exprimée en pouces. (Sur les connecteurs uniquement.)|0|  
|Position|La position par défaut de l’élément décoratif.|TargetBottom|  
  
## <a name="see-also"></a>Voir aussi  
 [Glossaire des outils de langage spécifique à un domaine](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)