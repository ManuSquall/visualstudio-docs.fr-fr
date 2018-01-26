---
title: "Propriétés des couloirs | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.dsltools.dsldesigner.swimlane
helpviewer_keywords: Domain-Specific Language, swimlane
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 84107514e728dbfa79b7dfdaee6c3febaee21274
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="properties-of-swimlanes"></a>Propriétés des couloirs
Vous pouvez ajouter des couloirs pour un diagramme. Couloirs divisent un diagramme en zones verticales ou horizontales. Vous pouvez définir d’autres formes à afficher à l’intérieur des couloirs. Pour plus d’informations, consultez [comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md). Pour plus d’informations sur la façon d’utiliser ces propriétés, consultez [personnalisation et l’extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Couloirs ont les propriétés qui sont répertoriées dans le tableau suivant.  
  
|Propriété|Description|Default|  
|--------------|-----------------|-------------|  
|Couleur de remplissage de corps|La couleur de remplissage pour le corps de la couloir.|Blanc|  
|Couleur de remplissage d’en-tête|La couleur de remplissage de l’en-tête du couloir.|Gris foncé|  
|Couleur de séparateur|Couleur de la ligne de séparation.|LightGray|  
|Style de séparateur de ligne|Le style de la ligne de séparation (`Solid`, `Dash`, `Dot`, `DashDot`, `DashDotDot`, ou `Custom`).|`Dash`|  
|Épaisseur du séparateur|L’épaisseur de la ligne de séparation en pouces.|0.03125|  
|Couleur du texte|La couleur qui est utilisée pour les éléments décoratifs de texte qui sont associés à ce couloir.|Noir|  
|Modificateur d'accès|Le niveau d’accès de la classe (`public` ou `internal`).|Public|  
|Attributs personnalisés|Utilisé pour ajouter des attributs à la classe de code est générée à partir de ce couloir.|\<none>|  
|Génère deux dérivées|Si `True`, une classe de base et une classe partielle (pour la personnalisation par des remplacements) seront générés. Pour plus d’informations, consultez [substituer et étendre les Classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|A constructeur personnalisé|Si `True`, un constructeur personnalisé sera fourni dans le code source. Pour plus d’informations, consultez [substituer et étendre les Classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificateur d’héritage|Décrit le type d’héritage de la classe de code source qui est générée à partir du couloir (`none`, `abstract` ou `sealed`).|aucun|  
|Base couloir|La classe de base de ce couloir.|(aucun)|  
|Nom|Le nom de ce couloir.|Nom actuel|  
|Espace de noms|L’espace de noms n’est affilié à ce couloir.|Espace de noms actuel|  
|Type de l’info-bulle|Comment l’info-bulle est défini (`fixed`, `variable`, ou `none`). Si `fixed`, alors la valeur de la `Fixed Tooltip Text` propriété est utilisée ; si `variable`, puis l’info-bulle est défini dans le code personnalisé.|\<none>|  
|Remarques|Notes informelles qui sont associés à ce couloir.|\<none>|  
|Alignement|Alignement horizontal ou vertical.|Vertical|  
|Hauteur initiale|La hauteur initiale de ce couloir, exprimée en pouces. Applicable uniquement aux couloirs horizontaux.|0|  
|Largeur initiale|La largeur initiale de ce couloir, exprimée en pouces. Applicable uniquement aux couloirs verticale.|0|  
|Expose la couleur du texte|Si `True`, l’utilisateur peut définir la couleur d’un couloir dans le concepteur généré. Pour configurer cela, avec le bouton droit de la forme couloir, puis cliquez sur **ajouter exposées**.|False|  
|Description|Utilisé pour documenter le concepteur généré.|\<none>|  
|Nom complet|Le nom qui sera affiché dans le concepteur généré pour faire référence à cette classe couloir.|\<none>|  
|Texte info-bulle fixe|Le texte qui est utilisé pour une info-bulle fixe.|\<none>|  
|Help Keyword|Le mot clé qui est utilisé pour l’index d’aide (F1) pour ce couloir.|\<none>|  
  
## <a name="see-also"></a>Voir aussi  
 [Glossaire des outils de langage spécifique à un domaine](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)