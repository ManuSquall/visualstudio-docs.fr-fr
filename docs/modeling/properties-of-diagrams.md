---
title: Propriétés des diagrammes
ms.date: 10/31/2018
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 73be8223d661617451d548898164b78a1a1563f0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658230"
---
# <a name="properties-of-diagrams"></a>Propriétés des diagrammes
Vous pouvez définir des propriétés qui spécifient le mode d’affichage des diagrammes dans le concepteur généré. Par exemple, vous pouvez spécifier une couleur par défaut pour le texte dans le diagramme.

 Pour plus d’informations, consultez [comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md). Pour plus d’informations sur l’utilisation de ces propriétés, consultez [personnaliser et étendre un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Le tableau suivant répertorie les propriétés des diagrammes.

|Property|Description|Valeur par défaut|
|-|-|-|
|Couleur de remplissage|Couleur de remplissage du diagramme.|ajourée|
|Couleur du texte|Couleur du texte affiché sur le diagramme.|Noir|
|Modificateur d'accès|Modificateur d’accès de la classe (public ou Internal).|Public|
|Attributs personnalisés|Utilisé pour ajouter des attributs à la classe de code générée.|\<aucune>|
|Génère un doublon dérivé|Si `True`, une classe de base et une classe partielle (pour prendre en charge la personnalisation via des substitutions) sont générées. Pour plus d’informations, consultez [remplacer et étendre les classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|A un constructeur personnalisé|Si `True`, un constructeur personnalisé est fourni dans le code source. Pour plus d’informations, consultez [remplacer et étendre les classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modificateur d’héritage|Décrit le type d’héritage de la classe de code source qui est généré à partir du diagramme (`none`, `abstract` ou `sealed`).|aucune.|
|Diagramme de base|Classe de base de ce diagramme.|(aucune)|
|Name|Nom de ce diagramme.|Nom actuel|
|Espace de noms|Espace de noms affilié à ce diagramme.|Espace de noms actuel|
|Classe représentée|Classe de domaine racine représentée par ce diagramme.|Classe racine actuelle, le cas échéant|
|Notes|Notes informelles associées à cet élément.|\<aucune>|
|Expose la couleur de remplissage en tant que propriété|Si `True`, l’utilisateur peut définir la couleur de remplissage du diagramme du concepteur généré. Pour définir cette propriété, cliquez avec le bouton droit sur la forme de diagramme, puis cliquez sur **Ajouter exposé**.|False|
|Expose la couleur de texte en tant que propriété|Si `True`, l’utilisateur peut définir la couleur de texte du diagramme dans le concepteur généré. Pour définir cette propriété, cliquez avec le bouton droit sur la forme de diagramme, puis cliquez sur **Ajouter exposé**.|False|
|Description|Description utilisée pour documenter le concepteur généré.|\<aucune>|
|Display Name|Nom qui sera affiché dans le concepteur généré pour ce diagramme.|\<aucune>|
|Help Keyword|Mot clé utilisé pour indexer l’aide F1 pour ce diagramme.|\<aucune>|

## <a name="see-also"></a>Voir aussi

[Glossaire des outils de langage spécifique à un domaine](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
