---
title: Propriétés des formes de compartiment
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.compartmentshape
helpviewer_keywords:
- Domain-Specific Language, compartment shape
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 95af639a6874aac79d96693dcf58a8d6b2088f80
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2018
---
# <a name="properties-of-compartment-shapes"></a>Propriétés des formes de compartiment
Formes de compartiment sont une des formes que vous pouvez utiliser pour afficher une classe de domaine dans un langage spécifique à un domaine. Vous pouvez développer et réduire les compartiments.

 Pour plus d’informations, consultez [comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md). Pour plus d’informations sur la façon d’utiliser ces propriétés, consultez [personnalisation et l’extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Formes de compartiment ont les propriétés qui sont répertoriées dans le tableau suivant.

|Propriété|Description|Par défaut|
|--------------|-----------------|-------------|
|Par défaut développer l’état de la réduction|Si `Expanded`, les compartiments sont affichées lors de la création. Si `Collapsed`, ils ne sont pas.|Développé|
|Couleur de remplissage|La couleur de remplissage de cette forme.|Blanc|
|Remplir le Mode dégradé|Le mode remplissage dégradé de cette forme.|Horizontal|
|Géométrie|La géométrie de cette forme (Rectangle ou un Rectangle arrondi).|Rectangle|
|A des Points de connexion par défaut|Si `True`, la forme utilisera haut, bas, gauche et droit connexion pointe dans le concepteur généré.|False|
|En-tête de compartiment unique n’est Visible|Si `False`et la forme comporte un seul compartiment, l’en-tête du compartiment n’est pas visible.|True|
|Couleur du contour|La couleur de contour de cette forme.|Noir|
|Style de ligne de plan|Le style de ligne hiérarchique de cette forme (solide, tiret, point, tiret, DashDotDot, personnalisé).|Unie|
|Épaisseur du contour|L’épaisseur du contour de cette forme.|0.03125|
|Couleur du texte|La couleur utilisée pour les éléments décoratifs de texte qui sont associés à cette forme.|Noir|
|Modificateur d'accès|Le niveau d’accès de la forme de compartiment (`public` ou `internal`).|Public|
|Attributs personnalisés|Permet d’ajouter des attributs à la classe de code source qui est générée à partir de cette forme de compartiment|\<Aucun >|
|Génère deux dérivées|Si `True`, une classe de base et une classe partielle (pour la personnalisation par des remplacements) seront générés. Pour plus d’informations, consultez [substituer et étendre les Classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|A constructeur personnalisé|Si `True`, un constructeur personnalisé sera fourni dans le code source. Pour plus d’informations, consultez [substituer et étendre les Classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modificateur d’héritage|Décrit le type d’héritage de la classe de code source qui est générée à partir de la forme de compartiment (`none`, `abstract` ou `sealed`).|Aucun|
|Forme de compartiment de base|La classe de base de cette forme.|(aucune)|
|Name|Le nom de cette forme.|Nom actuel|
|Espace de noms|L’espace de noms n’est affilié à cette forme.|Espace de noms actuel|
|Type de l’info-bulle|Comment l’info-bulle est défini (fixe, variable, ou aucun). Si fixe, puis la valeur de la `Fixed Tooltip Text` propriété est utilisée en tant que l’info-bulle ; si la variable, l’info-bulle est défini dans le code personnalisé.|aucun|
|Notes|Notes informelles qui sont associés à cette forme.|\<Aucun >|
|Hauteur initiale|La hauteur initiale de cette forme, exprimée en pouces. Pour les formes de compartiment, c’est la hauteur de la section d’en-tête, et il ne peut pas être redimensionné.|1|
|Largeur initiale|La largeur initiale de cette forme, exprimée en pouces.|1,5|
|Couleur de remplissage exposé en tant que propriété<br /><br /> Mode de remplissage exposé de dégradé<br /><br /> Exposée de couleur de contour comme propriété<br /><br /> Exposé un Style de ligne hiérarchique en tant que propriété<br /><br /> Épaisseur du contour en tant que propriété d’exposé<br /><br /> Expose la couleur du texte|Si `True`, l’utilisateur peut définir la propriété indiquée d’une forme. Pour configurer cela, cliquez sur la définition de la forme, puis cliquez sur **ajouter exposées**.|False|
|Description|Utilisé pour documenter le concepteur généré.|\<Aucun >|
|Nom complet|Le nom qui sera affiché dans le concepteur généré pour cette forme.|\<Aucun >|
|Texte info-bulle fixe|Le texte qui est utilisé pour une info-bulle fixe.|\<Aucun >|
|Help Keyword|Le mot clé qui est utilisé pour l’index d’aide (F1) pour cette forme.|\<Aucun >|

## <a name="see-also"></a>Voir aussi

- [Glossaire des outils de langage spécifique à un domaine](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)