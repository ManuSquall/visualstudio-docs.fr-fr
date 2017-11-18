---
title: "Propriétés des connecteurs | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, connectors
ms.assetid: b1f24e8d-cdd7-4a5d-af37-1038f43b45c7
caps.latest.revision: "21"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 503f171b2af5e06fd3c890caf07525ba880d0658
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="properties-of-connectors"></a>Propriétés des connecteurs
Connecteurs de représentent les relations de domaine dans un concepteur généré.  
  
 Pour plus d’informations, consultez [comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md). Pour plus d’informations sur la façon d’utiliser ces propriétés, consultez [personnalisation et l’extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Les connecteurs ont les propriétés qui sont répertoriées dans le tableau suivant.  
  
|Propriété|Description|Par défaut|  
|--------------|-----------------|-------------|  
|Color|La couleur de ce connecteur.|Noir|  
|Style de ligne|Le style de ligne de la ligne de ce connecteur (solide, tiret, point, tiret, DashDotDot ou personnalisé).|Unie|  
|Style de fin source|Le style de fin de source pour ce connecteur (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond ou aucun).|Aucune|  
|Style de fin cible|Le style de fin cible pour ce connecteur (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond ou aucun).|Aucune|  
|Couleur du texte|La couleur qui est utilisée pour les éléments décoratifs de texte qui sont associés à ce connecteur.|Noir|  
|Thickness|L’épaisseur de la ligne pour ce connecteur, mesurée en pouces.|0.03125|  
|Modificateur d'accès|Le niveau d’accès de la classe (`public` ou `internal`).|Public|  
|Attributs personnalisés|Utilisé pour ajouter des attributs à la classe de code source qui est générée à partir de ce connecteur.|\<Aucun >|  
|Génère deux dérivées|Si `True`, une classe de base et une classe partielle (pour la personnalisation par des remplacements) seront générés. Pour plus d’informations, consultez [substituer et étendre les Classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|A constructeur personnalisé|Si `True`, un constructeur personnalisé sera fourni dans le code source. Pour plus d’informations, consultez [substituer et étendre les Classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificateur d’héritage|Décrit le type d’héritage de la classe de code source qui est générée à partir du connecteur (`none`, `abstract` ou `sealed`).|aucun|  
|Connecteur de base|La classe de base de ce connecteur.|(aucun)|  
|Nom|Le nom de ce connecteur.|Nom actuel|  
|Espace de noms|L’espace de noms n’est affilié à ce connecteur.|Espace de noms actuel|  
|Type de l’info-bulle|Comment l’info-bulle est défini (fixe, variable, ou aucun). Si fixe, puis la valeur de la `Fixed Tooltip Text` propriété est utilisée en tant que l’info-bulle ; si la variable, l’info-bulle est défini dans le code personnalisé.|\<Aucun >|  
|Remarques|Notes informelles qui sont associés à ce connecteur.|\<Aucun >|  
|Style de routage|Le style qui est utilisé pour le connecteur de routage. A `Rectilinear` connecteur permet à angle droit active en fonction des besoins ; un `Straight` n’est pas le cas du connecteur.|Rectilignes|  
|Couleur exposé en tant que propriété<br /><br /> Style de tiret exposé en tant que propriété<br /><br /> Épaisseur exposé en tant que propriété<br /><br /> Expose la couleur du texte|Si `True`, l’utilisateur peut définir la propriété indiquée d’une forme. Pour configurer cela, cliquez sur la définition de la forme, puis cliquez sur **ajouter exposées**.|False|  
|Description|Utilisé pour documenter le concepteur généré.|\<Aucun >|  
|Nom complet|Le nom qui sera affiché dans le concepteur généré pour ce connecteur.|\<Aucun >|  
|Texte info-bulle fixe|Le texte qui est utilisé pour une info-bulle fixe.|\<Aucun >|  
|Help Keyword|Le mot clé qui est utilisé pour l’index d’aide (F1) pour cet élément.|\<Aucun >|  
  
## <a name="see-also"></a>Voir aussi  
 [Glossaire des outils de langage spécifique à un domaine](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)