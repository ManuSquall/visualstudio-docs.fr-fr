---
title: "Propriétés des formes de géométrie | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.dsltools.dsldesigner.geometryshape
helpviewer_keywords: Domain-Specific Language, geometry shape
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 84773891342b18a583cf2919a7d09e0aaa9d2b93
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2018
---
# <a name="properties-of-geometry-shapes"></a>Propriétés des formes de géométrie
Vous pouvez utiliser des formes de géométrie pour spécifier l’affichage des instances de classes de domaine dans un langage spécifique à un domaine. Pour plus d’informations, consultez [comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md). Pour plus d’informations sur la façon d’utiliser ces propriétés, consultez [personnalisation et l’extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Formes de géométrie ont les propriétés qui sont répertoriées dans le tableau suivant.  
  
|Propriété|Description|Par défaut|  
|--------------|-----------------|-------------|  
|Couleur de remplissage|La couleur de remplissage de cette forme.|Blanc|  
|Remplir le Mode dégradé|Le mode remplissage dégradé de cette forme (Horizontal, Vertical, Diagonal vers l’avant, Diagonale descendante ou aucun).|Horizontal|  
|Géométrie|La géométrie de cette forme (Rectangle, Rectangle arrondi, Ellipse ou le cercle).|Rectangle|  
|A des Points de connexion par défaut|Si `True`, la forme utilisera haut, bas, gauche et droit connexion pointe dans le concepteur généré.|False|  
|Couleur du contour|La couleur de contour de cette forme.|Noir|  
|Style de ligne de plan|Le style de ligne hiérarchique de cette forme (solide, tiret, point, tiret, DashDotDot ou personnalisé).|Unie|  
|Épaisseur du contour|L’épaisseur du contour de cette forme.|0.03125|  
|Couleur du texte|La couleur qui est utilisée pour les éléments décoratifs de texte qui sont associés à cette forme.|Noir|  
|Modificateur d'accès|Le modificateur d’accès de la classe (public ou internal).|Public|  
|Attributs personnalisés|Utilisé pour ajouter des attributs à la classe de code source qui est générée pour cette forme.|\<Aucun >|  
|Génère deux dérivées|Si `True`, une classe de base et une classe partielle (pour la personnalisation par des remplacements) seront générés. Pour plus d’informations, consultez [substituer et étendre les Classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|A constructeur personnalisé|Si `True`, un constructeur personnalisé sera fourni dans le code source. Pour plus d’informations, consultez [substituer et étendre les Classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificateur d’héritage|Décrit le type d’héritage de la classe de code source qui est générée à partir de la forme (`none`, `abstract` ou `sealed`).|aucun|  
|Forme de la géométrie de base|La classe de base de cette forme.|(aucune)|  
|Name|Le nom de cette forme.|Nom actuel|  
|Espace de noms|L’espace de noms n’est affilié à cette forme.|Espace de noms actuel|  
|Type de l’info-bulle|Comment l’info-bulle est défini (fixe, variable, ou aucun). Si fixe, puis la valeur de la `Fixed Tooltip Text` propriété est utilisée en tant que l’info-bulle ; si la variable, l’info-bulle est défini dans le code personnalisé.|Aucun.|  
|Notes|Notes informelles qui sont associés à cet élément.|\<Aucun >|  
|Hauteur initiale|Hauteur initiale de cette forme, exprimée en pouces.|1|  
|Largeur initiale|Largeur initiale de cette forme, exprimée en pouces.|1,5|  
|Couleur de remplissage exposé en tant que propriété<br /><br /> Mode de remplissage exposé de dégradé<br /><br /> Exposée de couleur de contour comme propriété<br /><br /> Exposé un Style de ligne hiérarchique en tant que propriété<br /><br /> Épaisseur du contour en tant que propriété d’exposé<br /><br /> Expose la couleur du texte|Si `True`, l’utilisateur peut définir la propriété indiquée d’une forme. Pour configurer cela, cliquez sur la définition de la forme, puis cliquez sur **ajouter exposées**.|False|  
|Description|La description qui est utilisée pour documenter le concepteur généré.|\<Aucun >|  
|Nom complet|Le nom qui sera affiché dans le concepteur généré pour cette forme.|\<Aucun >|  
|Texte info-bulle fixe|Le texte qui est utilisé pour une info-bulle fixe.|\<Aucun >|  
|Help Keyword|Le mot clé qui est utilisé pour l’index d’aide (F1) pour cette forme.|\<Aucun >|  
  
## <a name="see-also"></a>Voir aussi  
 [Glossaire des outils de langage spécifique à un domaine](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)