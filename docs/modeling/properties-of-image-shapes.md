---
title: Propriétés des formes d'image
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.selectimagedialog
- vs.dsltools.dsldesigner.imageshape
helpviewer_keywords:
- Domain-Specific Language, image shape
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 7e492996a194c6602af3ec412b86f7477ef233e1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49928709"
---
# <a name="properties-of-image-shapes"></a>Propriétés des formes d'image
Vous pouvez utiliser des formes d’images pour spécifier comment les classes de domaine s’affichent dans un concepteur généré. Définir une forme d’image en définissant le `Image` propriété de la classe dans un fichier image prédéfinie. Les formats suivants sont pris en charge :

- .gif

- .jpg

- .JPEG

- .bmp

- .wmf

- .emf

- .png

  Par défaut, les fichiers de ressources de concepteur, tels que les fichiers image sont situés dans le **ressources**dossier dans le **Dsl** projet.

  Pour plus d’informations, consultez [comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md). Pour plus d’informations sur l’utilisation de ces propriétés, consultez [personnalisation et extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).

  Formes d’images ont les propriétés qui sont répertoriées dans le tableau suivant.

|Propriété|Description|Par défaut|
|-|-|-|
|Couleur de remplissage|La couleur de remplissage de cette forme.|Blanc|
|Mode de remplissage dégradé|Le mode de remplissage dégradé de cette forme.|Horizontal|
|A des Points de connexion par défaut|Si `True`, la forme utilisera haut, bas, gauche et droit connexion pointe dans le concepteur généré.|False|
|Couleur du contour|La couleur de contour de cette forme.|Noir|
|Style de tiret de contour|Le style de tiret de contour de cette forme (solide, tiret, point, tiret, DashDotDot ou personnalisé).|Unie|
|Épaisseur du contour|L’épaisseur du contour de cette forme.|0.03125|
|Couleur du texte|La couleur qui est utilisée pour les éléments décoratifs de texte qui sont associés à cette forme.|Noir|
|Modificateur d'accès|Le modificateur d’accès de la forme de géométrie (public ou interne).|Public|
|Attributs personnalisés|Utilisé pour ajouter des attributs à la classe de code source qui est générée à partir de cette forme.|\<Aucun >|
|Génère le Double dérivée|Si `True`, une classe de base et une classe partielle (pour prendre en charge la personnalisation via des substitutions) sont générés. Pour plus d’informations, consultez [substitution et extension des Classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|A le constructeur personnalisé|Si `True`, un constructeur personnalisé est fourni dans le code source. Pour plus d’informations, consultez [substitution et extension des Classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modificateur d’héritage|Décrit le type d’héritage de la classe de code source qui est générée à partir de la forme d’image (`none`, `abstract` ou `sealed`).|none|
|Forme d’Image de base|La classe de base de cette forme.|(aucune)|
|Name|Le nom de cette forme.|Nom actuel|
|Espace de noms|L’espace de noms qui est affilié à cette forme.|Espace de noms actuel|
|Type de l’info-bulle|L’endroit où l’info-bulle est défini (fixé, variable, ou aucun). Si fixe, puis la valeur de la `Fixed Tooltip Text` propriété est utilisée en tant que l’info-bulle ; si la variable, l’info-bulle est définie dans du code personnalisé.|none|
|Notes|Remarques informelles associées à cette forme.|\<Aucun >|
|Hauteur initiale|La hauteur initiale de cette forme, en pouces.|1|
|Largeur initiale|Largeur initiale de cette forme, en pouces.|1,5|
|Couleur de remplissage exposé en tant que propriété<br /><br /> Mode de remplissage exposé dégradé<br /><br /> Exposé de couleur du contour en tant que propriété<br /><br /> Exposé de Style de tiret de contour en tant que propriété<br /><br /> Épaisseur du contour en tant que propriété d’exposées<br /><br /> Expose la couleur du texte|Si `True`, l’utilisateur peut définir la propriété indiquée d’une forme. Pour définir ceci, avec le bouton droit de la définition de forme, puis cliquez sur **ajouter les objets exposés**.|False|
|Description|Utilisé pour documenter le concepteur généré.|\<Aucun >|
|Nom complet|Le nom qui s’affichera dans le concepteur généré pour cette forme.|\<Aucun >|
|Texte d’info-bulle fixe|Le texte qui est utilisé pour une info-bulle fixe.|\<Aucun >|
|Help Keyword|Le mot clé qui est utilisé pour indexer l’aide F1 pour cet élément.|\<Aucun >|
|Image|Le chemin d’accès au fichier image qui est utilisé pour cette forme.|\<Aucun >|

## <a name="see-also"></a>Voir aussi

- [Glossaire des outils Domain-Specific Language](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)