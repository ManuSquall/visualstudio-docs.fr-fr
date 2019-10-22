---
title: Propriétés des formes de port | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.port
helpviewer_keywords:
- Domain-Specific Language, port shape
ms.assetid: 9d69c4c1-4f72-4876-96b6-9b846e0495a4
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 906a35f1b564c4e3794d1000f03cb32cda003ca2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671363"
---
# <a name="properties-of-port-shapes"></a>Propriétés des formes de port
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez utiliser des formes port pour représenter des classes de domaine dans le concepteur généré.

 Pour plus d’informations, consultez [comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md). Pour plus d’informations sur l’utilisation de ces propriétés, consultez [personnalisation et extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Les formes de port ont les propriétés répertoriées dans le tableau suivant.

|Property|Description|Valeur par défaut|
|--------------|-----------------|-------------|
|Couleur de remplissage|Couleur de remplissage de cette forme.|ajourée|
|Mode dégradé de remplissage|Mode de remplissage dégradé de cette forme.|Horizontal|
|Geometr|Géométrie de cette forme (Rectangle, Rectangle arrondi, ellipse ou cercle).|Rectangle|
|A des points de connexion par défaut|Si `True`, la forme utilise les points de connexion du haut, du bas, de gauche et de droite dans le concepteur généré.|False|
|Couleur de contour|Couleur de contour de cette forme.|Noir|
|Style de tiret de contour|Style de tiret de contour de cette forme (plein, tiret, point, tiret point, tiret point point ou personnalisé).|Unie|
|Épaisseur du contour|Épaisseur de contour de cette forme.|0,03125|
|Couleur du texte|Couleur utilisée pour les éléments décoratifs de texte associés à cette forme.|Noir|
|Modificateur d'accès|Niveau d’accès de la classe (`public` ou `internal`).|Public|
|Attributs personnalisés|Utilisé pour ajouter des attributs à la classe de code source générée à partir de cette forme.|\<aucune>|
|Génère un doublon dérivé|Si `True`, une classe de base et une classe partielle (pour prendre en charge la personnalisation via des substitutions) sont générées. Pour plus d’informations, consultez [substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md)|False|
|A un constructeur personnalisé|Si `True`, un constructeur personnalisé est fourni dans le code source. Pour plus d’informations, consultez [substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modificateur d’héritage|Décrit le type d’héritage de la classe de code source générée à partir du port (`none`, `abstract` ou `sealed`).|none|
|Port de base|Classe de base de cette forme.|(aucune)|
|Name|Nom de cette forme.|Nom actuel|
|Espace de noms|Espace de noms affilié à cette forme.|Espace de noms actuel|
|Type d’info-bulle|Comment l’info-bulle est définie (Fixed, variable ou None). S’il est corrigé, la valeur de la propriété `Fixed Tooltip Text` est utilisée comme info-bulle ; Si la variable est, l’info-bulle est définie dans le code personnalisé.|none|
|Notes|Notes informelles associées à cette forme.|\<aucune>|
|Hauteur initiale|Hauteur initiale de cette forme, en pouces.|1|
|Largeur initiale|Largeur initiale de cette forme, en pouces.|1,5|
|Couleur de remplissage exposée en tant que propriété<br /><br /> Mode dégradé de remplissage exposé<br /><br /> Couleur de contour exposée en tant que propriété<br /><br /> Exposé du style de tiret de contour en tant que propriété<br /><br /> Exposer l’épaisseur de la structure en tant que propriété<br /><br /> Expose la couleur de texte|Si `True`, l’utilisateur peut définir la propriété déclarée d’une forme. Pour ce faire, cliquez avec le bouton droit sur la définition de la forme, puis cliquez sur **Ajouter exposé**.|False|
|Description|Utilisé pour documenter le concepteur généré.|\<aucune>|
|Display Name|Nom qui sera affiché dans le concepteur généré pour cette forme.|\<aucune>|
|Correction du texte d’info-bulle|Texte utilisé pour une info-bulle fixe.|\<aucune>|
|Help Keyword|Mot clé utilisé pour indexer l’aide F1 pour cette forme.|\<aucune>|

## <a name="see-also"></a>Voir aussi
 [Glossaire des Outils Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
