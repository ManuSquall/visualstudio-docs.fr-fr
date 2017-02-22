---
title: "Propri&#233;t&#233;s des d&#233;corateurs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "langage spécifique à un domaine, décorateurs"
ms.assetid: f6322fe5-dc08-4d32-a6b3-0bd18879136d
caps.latest.revision: 23
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 23
---
# Propri&#233;t&#233;s des d&#233;corateurs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les éléments décoratifs sont des icônes, du texte, ou développent\/chevrons de réduction qui peuvent apparaître sur des formes ou des connecteurs sur le diagramme.  Les tableaux suivants répertorient les propriétés pour les trois genres de décorateur.  Certaines propriétés apparaissent uniquement sur les éléments décoratifs de forme ou uniquement sur les éléments décoratifs de connecteur.  
  
 Pour plus d'informations, consultez [Comment : définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md).  Pour plus d'informations sur l'utilisation de ces propriétés, consultez [Personnalisation et extension d'un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
## Développer\/décorateur de réduction  
  
|Propriété|Description|Par défaut|  
|---------------|-----------------|----------------|  
|DisplayName|Le nom de décorateur qui s'affiche dans le concepteur généré.|Développez de décorateur de réduction|  
|Nom|Le nom de décorateur.|ExpandCollapseDecorator|  
|Remarques|Remarques informelles associées à ce décorateur.|\<aucune\>|  
|HorizontalOffset|L'offset horizontal, relatif à l'emplacement par défaut de décorateur, dans pouces.  \(Sur les formes uniquement.\)|0|  
|VerticalOffset|Le décalage vertical, relatif à l'emplacement par défaut de décorateur, dans pouces.  \(Sur les formes uniquement.\)|0|  
|OffsetFromLine|L'offset du décorateur de la ligne, par rapport à sa position par défaut, dans pouces.  \(Sur les connecteurs uniquement.\)|0|  
|OffsetFromShape|L'offset du décorateur de la forme, par rapport à sa position par défaut, dans pouces.  \(Sur les connecteurs uniquement.\)|0|  
|Position|La position par défaut de décorateur.|SourceTop|  
  
## Élément décoratif d'icône  
  
|Propriété|Description|Par défaut|  
|---------------|-----------------|----------------|  
|DefaultIcon|le chemin d'accès de l'icône ou du fichier image à afficher.|\<aucune\>|  
|DisplayName|Le nom de décorateur à afficher dans le concepteur généré.|Élément décoratif d'icône|  
|Nom|Le nom de décorateur.|IconDecorator|  
|Remarques|Remarques informelles associées au décorateur.|\<aucune\>|  
|HorizontalOffset|L'offset horizontal, relatif à l'emplacement par défaut de décorateur, dans pouces.  \(Sur les formes uniquement.\)|0|  
|VerticalOffset|Le décalage vertical, relatif à l'emplacement par défaut de décorateur, dans pouces.  \(Sur les formes uniquement.\)|0|  
|OffsetFromLine|L'offset du décorateur de la ligne, par rapport à sa position par défaut, dans pouces.  \(Sur les connecteurs uniquement.\)|0|  
|OffsetFromShape|L'offset du décorateur de la forme, par rapport à sa position par défaut, dans pouces.  \(Sur les connecteurs uniquement.\)|0|  
|Position|La position par défaut de décorateur.|SourceTop|  
  
## TextDecorator  
  
|Propriété|Description|Par défaut|  
|---------------|-----------------|----------------|  
|DefaultText|le texte par défaut à afficher.|Étiquette|  
|DisplayName|Le nom de décorateur à afficher dans le concepteur généré.|Étiquette|  
|FontSize|La taille de la police du texte qui est affiché dans l'élément décoratif.|8|  
|FontStyle|Le style de police du texte qui est affiché dans l'élément décoratif.|Normale|  
|Nom|Le nom de décorateur.|Étiquette|  
|Remarques|Remarques informelles associées au décorateur.|\<aucune\>|  
|HorizontalOffset|L'offset horizontal, relatif à l'emplacement par défaut de décorateur, dans pouces.  \(Sur les formes uniquement.\)|0|  
|VerticalOffset|Le décalage vertical, relatif à l'emplacement par défaut de décorateur, dans pouces.  \(Sur les formes uniquement.\)|0|  
|OffsetFromLine|L'offset du décorateur de la ligne, par rapport à sa position par défaut, dans pouces.  \(Sur les connecteurs uniquement.\)|0|  
|OffsetFromShape|L'offset du décorateur de la forme, par rapport à sa position par défaut, dans pouces.  \(Sur les connecteurs uniquement.\)|0|  
|Position|La position par défaut de décorateur.|TargetBottom|  
  
## Voir aussi  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/fr-fr/ca5e84cb-a315-465c-be24-76aa3df276aa)