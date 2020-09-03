---
title: Propriétés des couloirs | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.swimlane
helpviewer_keywords:
- Domain-Specific Language, swimlane
ms.assetid: 47edbc2d-09e4-48ac-b4d1-5268a06a27e6
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1b76bef291e23bc570534aa79f9471453c59491c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671341"
---
# <a name="properties-of-swimlanes"></a>Propriétés des couloirs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez ajouter des couloirs à un diagramme. Les couloirs divisent un diagramme en zones verticales ou horizontales. Vous pouvez définir d’autres formes à afficher à l’intérieur des couloirs. Pour plus d’informations, consultez [comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md). Pour plus d’informations sur l’utilisation de ces propriétés, consultez [personnalisation et extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Les couloirs ont les propriétés répertoriées dans le tableau suivant.

|Propriété|Description|Default|
|--------------|-----------------|-------------|
|Couleur de remplissage du corps|Couleur de remplissage du corps du couloir.|White|
|Couleur de remplissage d’en-tête|Couleur de remplissage de l’en-tête du couloir.|DarkGray|
|Couleur du séparateur|Couleur de la ligne de séparation.|LightGray|
|Style de ligne de séparateur|Style de la ligne de séparation ( `Solid` , `Dash` , `Dot` , `DashDot` , `DashDotDot` ou `Custom` ).|`Dash`|
|Épaisseur du séparateur|Épaisseur de la ligne de séparation, en pouces.|0,03125|
|Couleur du texte|Couleur utilisée pour les éléments décoratifs de texte associés à ce couloir.|Noir|
|Modificateur d'accès|Niveau d’accès de la classe ( `public` ou `internal` ).|Public|
|Attributs personnalisés|Utilisé pour ajouter des attributs à la classe de code générée à partir de ce couloir.|\<none>|
|Génère un doublon dérivé|Si `True` la valeur est, une classe de base et une classe partielle (pour prendre en charge la personnalisation via des substitutions) sont générées. Pour plus d’informations, consultez [substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|Faux|
|A un constructeur personnalisé|Si `True` , un constructeur personnalisé est fourni dans le code source. Pour plus d’informations, consultez [substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|Faux|
|Modificateur d’héritage|Décrit le type d’héritage de la classe de code source qui est généré à partir du couloir ( `none` , `abstract` ou `sealed` ).|Aucun|
|Couloir de base|Classe de base de ce couloir.|(aucun)|
|Nom|Nom de ce couloir.|Nom actuel|
|Espace de noms|Espace de noms affilié à ce couloir.|Espace de noms actuel|
|Type d’info-bulle|Comment l’info-bulle est définie ( `fixed` , `variable` ou `none` ). Si la `fixed` valeur est, la valeur de la `Fixed Tooltip Text` propriété est utilisée ; si `variable` la valeur est, l’info-bulle est définie dans le code personnalisé.|\<none>|
|Notes|Notes informelles associées à ce couloir.|\<none>|
|Alignment|Alignement horizontal ou vertical.|Vertical|
|Hauteur initiale|Hauteur initiale de ce couloir, en pouces. S’applique uniquement aux couloirs horizontaux.|0|
|Largeur initiale|Largeur initiale de ce couloir, en pouces. S’applique uniquement aux couloirs verticaux.|0|
|Expose la couleur de texte|Si la `True` valeur est, l’utilisateur peut définir la couleur d’un couloir dans le concepteur généré. Pour ce faire, cliquez avec le bouton droit sur la forme couloir, puis cliquez sur **Ajouter exposé**.|Faux|
|Description|Utilisé pour documenter le concepteur généré.|\<none>|
|Nom d’affichage|Nom qui sera affiché dans le concepteur généré pour faire référence à cette classe couloir.|\<none>|
|Texte d’info-bulle fixe|Texte utilisé pour une info-bulle fixe.|\<none>|
|Help Keyword|Mot clé utilisé pour indexer l’aide F1 pour ce couloir.|\<none>|

## <a name="see-also"></a>Voir aussi
 [Glossaire des Outils Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
