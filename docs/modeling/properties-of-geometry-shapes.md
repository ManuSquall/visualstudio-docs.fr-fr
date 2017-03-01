---
title: "Propriétés des formes de géométrie | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.geometryshape
helpviewer_keywords:
- Domain-Specific Language, geometry shape
ms.assetid: 3993a23e-eab3-4ceb-b475-c395d5992bfc
caps.latest.revision: 21
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 54e600e5d626828824d5a2584e1ff4f7fdc09810
ms.lasthandoff: 02/22/2017

---
# <a name="properties-of-geometry-shapes"></a>Propriétés des formes de géométrie
Vous pouvez utiliser des formes géométriques pour spécifier comment les instances des classes de domaine sont affichées dans un langage spécifique à un domaine. Pour plus d’informations, consultez [comment définir un langage spécifique au domaine](../modeling/how-to-define-a-domain-specific-language.md). Pour plus d’informations sur l’utilisation de ces propriétés, consultez [personnalisation et extension d’un langage spécifique au domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Formes géométriques ont les propriétés qui sont répertoriées dans le tableau suivant.  
  
|Propriété|Description|Par défaut|  
|--------------|-----------------|-------------|  
|Couleur de remplissage|Couleur de remplissage de cette forme.|Blanc|  
|Mode dégradé de remplissage|Mode remplissage dégradé de cette forme (Horizontal, Vertical, transférer en diagonale, Diagonale descendante ou aucun).|Horizontal|  
|Geometry|La géométrie de cette forme (Rectangle, Rectangle arrondi, Ellipse ou le cercle).|Rectangle|  
|A des Points de connexion par défaut|Si `True`la forme utilisera haut, bas, gauche et droit connexion pointe dans le concepteur généré.|False|  
|Couleur du contour|La couleur de contour de cette forme.|Noir|  
|Style de ligne de plan|Le style de ligne hiérarchique de cette forme (solide, tiret, point, tiret, DashDotDot ou personnalisé).|Unie|  
|Épaisseur du contour|L’épaisseur du contour de cette forme.|0.03125|  
|Couleur du texte|La couleur utilisée pour les décorateurs de texte qui sont associés à cette forme.|Noir|  
|Modificateur d'accès|Le modificateur d’accès de la classe (public ou interne).|Public|  
|Attributs personnalisés|Permet d’ajouter des attributs à la classe de code source qui est générée pour cette forme.|\<Aucun >|  
|Génère les deux dérivées|Si `True`, une classe de base et une classe partielle (pour prendre en charge de la personnalisation à travers les substitutions) seront générés. Pour plus d’informations, consultez [substitution et extension des Classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|A le constructeur personnalisé|Si `True`, un constructeur personnalisé sera fourni dans le code source. Pour plus d’informations, consultez [substitution et extension des Classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificateur d'héritage|Décrit le type d’héritage de la classe de code source qui est générée à partir de la forme (`none`, `abstract` ou `sealed`).|aucun|  
|Forme géométrique de base|La classe de base de cette forme.|(aucun)|  
|Nom|Le nom de cette forme.|Nom actuel|  
|Espace de noms|L’espace de noms est affilié à cette forme.|Espace de noms actuel|  
|Type de l’info-bulle|Comment l’info-bulle est défini (fixe, variable, ou aucun). Si fixe, puis la valeur de la `Fixed Tooltip Text` propriété est utilisée comme info-bulle ; si la variable, l’info-bulle est définie dans le code personnalisé.|Aucun|  
|Notes|Remarques informelles associées à cet élément.|\<Aucun >|  
|Hauteur initiale|Hauteur initiale de cette forme, en pouces.|1|  
|Largeur initiale|Largeur initiale de cette forme, en pouces.|1,5|  
|Couleur de remplissage exposé comme propriété<br /><br /> Mode de remplissage exposé de dégradé<br /><br /> Exposées de couleur du contour en tant que propriété<br /><br /> Exposé de Style de ligne hiérarchique en tant que propriété<br /><br /> Épaisseur du contour en tant que propriété d’exposé<br /><br /> Expose la couleur du texte|Si `True`, l’utilisateur peut définir la propriété de la forme indiquée. Pour cela, cliquez sur la définition de la forme, puis cliquez sur **ajouter exposées**.|False|  
|Description|La description qui est utilisée pour documenter le concepteur généré.|\<Aucun >|  
|Nom complet|Le nom qui sera affiché dans le concepteur généré pour cette forme.|\<Aucun >|  
|Texte info-bulle fixe|Le texte qui est utilisé pour une info-bulle fixe.|\<Aucun >|  
|Help Keyword|Le mot clé est utilisé pour indexer F1 Aide pour cette forme.|\<Aucun >|  
  
## <a name="see-also"></a>Voir aussi  
 [Glossaire des outils Domain-Specific Language](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)
