---
title: "Propriétés des formes d’Image | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.selectimagedialog
- vs.dsltools.dsldesigner.imageshape
helpviewer_keywords: Domain-Specific Language, image shape
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 953be16c3bf48a865acf131a2fd8fe02085b0637
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="properties-of-image-shapes"></a>Propriétés des formes d'image
Vous pouvez utiliser des formes d’image pour spécifier l’aspect des classes de domaine dans un concepteur généré. Définir une forme de l’image en définissant le `Image` propriété de la classe dans un fichier image prédéfinie. Les formats suivants sont pris en charge :  
  
-   .gif  
  
-   .jpg  
  
-   .jpeg  
  
-   .bmp  
  
-   .wmf  
  
-   .emf  
  
-   .png  
  
 Par défaut, les fichiers de ressource du concepteur, tels que les fichiers image sont situés dans le **ressources**dossier dans le **Dsl** projet.  
  
 Pour plus d’informations, consultez [comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md). Pour plus d’informations sur la façon d’utiliser ces propriétés, consultez [personnalisation et l’extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Formes d’image ont les propriétés qui sont répertoriées dans le tableau suivant.  
  
|Propriété|Description|Default|  
|--------------|-----------------|-------------|  
|Couleur de remplissage|La couleur de remplissage de cette forme.|Blanc|  
|Remplir le Mode dégradé|Le mode remplissage dégradé de cette forme.|Horizontal|  
|A des Points de connexion par défaut|Si `True`, la forme utilisera haut, bas, gauche et droit connexion pointe dans le concepteur généré.|False|  
|Couleur du contour|La couleur de contour de cette forme.|Noir|  
|Style de ligne de plan|Le style de ligne hiérarchique de cette forme (solide, tiret, point, tiret, DashDotDot ou personnalisé).|Unie|  
|Épaisseur du contour|L’épaisseur du contour de cette forme.|0.03125|  
|Couleur du texte|La couleur qui est utilisée pour les éléments décoratifs de texte qui sont associés à cette forme.|Noir|  
|Modificateur d'accès|Le modificateur d’accès de la forme de géométrie (public ou internal).|Public|  
|Attributs personnalisés|Utilisé pour ajouter des attributs à la classe de code source qui est générée à partir de cette forme.|\<none>|  
|Génère deux dérivées|Si `True`, une classe de base et une classe partielle (pour la personnalisation par des remplacements) seront générés. Pour plus d’informations, consultez [substituer et étendre les Classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|A constructeur personnalisé|Si `True`, un constructeur personnalisé sera fourni dans le code source. Pour plus d’informations, consultez [substituer et étendre les Classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificateur d’héritage|Décrit le type d’héritage de la classe de code source qui est générée à partir de la forme d’image (`none`, `abstract` ou `sealed`).|aucun|  
|Forme de l’Image de base|La classe de base de cette forme.|(aucun)|  
|Nom|Le nom de cette forme.|Nom actuel|  
|Espace de noms|L’espace de noms n’est affilié à cette forme.|Espace de noms actuel|  
|Type de l’info-bulle|L’endroit où l’info-bulle est défini (fixé, variable, ou aucun). Si fixe, puis la valeur de la `Fixed Tooltip Text` propriété est utilisée en tant que l’info-bulle ; si la variable, l’info-bulle est défini dans le code personnalisé.|aucun|  
|Remarques|Notes informelles qui sont associés à cette forme.|\<none>|  
|Hauteur initiale|La hauteur initiale de cette forme, exprimée en pouces.|1|  
|Largeur initiale|La largeur initiale de cette forme, exprimée en pouces.|1,5|  
|Couleur de remplissage exposé en tant que propriété<br /><br /> Mode de remplissage exposé de dégradé<br /><br /> Exposée de couleur de contour comme propriété<br /><br /> Exposé un Style de ligne hiérarchique en tant que propriété<br /><br /> Épaisseur du contour en tant que propriété d’exposé<br /><br /> Expose la couleur du texte|Si `True`, l’utilisateur peut définir la propriété indiquée d’une forme. Pour configurer cela, cliquez sur la définition de la forme, puis cliquez sur **ajouter exposées**.|False|  
|Description|Utilisé pour documenter le concepteur généré.|\<none>|  
|Nom complet|Le nom qui sera affiché dans le concepteur généré pour cette forme.|\<none>|  
|Texte info-bulle fixe|Le texte qui est utilisé pour une info-bulle fixe.|\<none>|  
|Help Keyword|Le mot clé qui est utilisé pour l’index d’aide (F1) pour cet élément.|\<none>|  
|Image|Le chemin d’accès au fichier image qui est utilisé pour cette forme.|\<none>|  
  
## <a name="see-also"></a>Voir aussi  
 [Glossaire des outils de langage spécifique à un domaine](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)