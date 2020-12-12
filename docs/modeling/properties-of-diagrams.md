---
title: Propriétés des diagrammes
description: En savoir plus sur les diagrammes et sur la façon dont vous pouvez définir des propriétés qui spécifient comment les diagrammes s’afficheront dans le concepteur généré.
ms.custom: SEO-VS-2020
ms.date: 10/31/2018
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe27eb7dcfb8a984fceaee0700e1df44b6de4ef1
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361948"
---
# <a name="properties-of-diagrams"></a>Propriétés des diagrammes
Vous pouvez définir des propriétés qui spécifient le mode d’affichage des diagrammes dans le concepteur généré. Par exemple, vous pouvez spécifier une couleur par défaut pour le texte dans le diagramme.

 Pour plus d’informations, consultez [comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md). Pour plus d’informations sur l’utilisation de ces propriétés, consultez [personnaliser et étendre un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Le tableau suivant répertorie les propriétés des diagrammes.

|Propriété|Description|Default|
|-|-|-|
|Couleur de remplissage|Couleur de remplissage du diagramme.|White|
|Couleur du texte|Couleur du texte affiché sur le diagramme.|Noir|
|Modificateur d'accès|Modificateur d’accès de la classe (public ou Internal).|Public|
|Attributs personnalisés|Utilisé pour ajouter des attributs à la classe de code générée.|\<none>|
|Génère un doublon dérivé|Si `True` la valeur est, une classe de base et une classe partielle (pour prendre en charge la personnalisation via des substitutions) sont générées. Pour plus d’informations, consultez [remplacer et étendre les classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|A un constructeur personnalisé|Si `True` , un constructeur personnalisé est fourni dans le code source. Pour plus d’informations, consultez [remplacer et étendre les classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modificateur d’héritage|Décrit le type d’héritage de la classe de code source qui est généré à partir du diagramme ( `none` , `abstract` ou `sealed` ).|None|
|Diagramme de base|Classe de base de ce diagramme.|(aucun)|
|Nom|Nom de ce diagramme.|Nom actuel|
|Espace de noms|Espace de noms affilié à ce diagramme.|Espace de noms actuel|
|Classe représentée|Classe de domaine racine représentée par ce diagramme.|Classe racine actuelle, le cas échéant|
|Remarques|Notes informelles associées à cet élément.|\<none>|
|Expose la couleur de remplissage en tant que propriété|Si la `True` valeur est, l’utilisateur peut définir la couleur de remplissage du diagramme du concepteur généré. Pour définir cette propriété, cliquez avec le bouton droit sur la forme de diagramme, puis cliquez sur **Ajouter exposé**.|False|
|Expose la couleur de texte en tant que propriété|Si la `True` valeur est, l’utilisateur peut définir la couleur de texte du diagramme dans le concepteur généré. Pour définir cette propriété, cliquez avec le bouton droit sur la forme de diagramme, puis cliquez sur **Ajouter exposé**.|False|
|Description|Description utilisée pour documenter le concepteur généré.|\<none>|
|Nom complet|Nom qui sera affiché dans le concepteur généré pour ce diagramme.|\<none>|
|Help Keyword|Mot clé utilisé pour indexer l’aide F1 pour ce diagramme.|\<none>|

## <a name="see-also"></a>Voir aussi

[Glossaire des outils de langage spécifique à un domaine](/previous-versions/bb126564(v=vs.100))