---
title: Propriétés des diagrammes
ms.date: 10/31/2018
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05c348edfa4665b138ac0f6069b0afaf6735da7a
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55937344"
---
# <a name="properties-of-diagrams"></a>Propriétés des diagrammes
Vous pouvez définir des propriétés qui spécifient la manière dont les diagrammes apparaîtront dans le concepteur généré. Par exemple, vous pouvez spécifier une couleur par défaut pour le texte dans le diagramme.

 Pour plus d’informations, consultez [comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md). Pour plus d’informations sur l’utilisation de ces propriétés, consultez [personnaliser et étendre un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Le tableau suivant répertorie les propriétés de diagrammes.

|Propriété|Description|Par défaut|
|-|-|-|
|Couleur de remplissage|La couleur de remplissage pour le diagramme.|Blanc|
|Couleur du texte|La couleur du texte qui s’affiche sur le diagramme.|Noir|
|Modificateur d'accès|Le modificateur d’accès de la classe (public ou interne).|Public|
|Attributs personnalisés|Utilisé pour ajouter des attributs à la classe de code généré.|\<aucune>|
|Génère le Double dérivée|Si `True`, une classe de base et une classe partielle (pour prendre en charge la personnalisation via des substitutions) sont générés. Pour plus d’informations, consultez [remplacer et étendre les classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|A le constructeur personnalisé|Si `True`, un constructeur personnalisé est fourni dans le code source. Pour plus d’informations, consultez [remplacer et étendre les classes générées](../modeling/overriding-and-extending-the-generated-classes.md)...|False|
|Modificateur d’héritage|Décrit le type d’héritage de la classe de code source qui est générée à partir du diagramme (`none`, `abstract`, ou `sealed`).|Aucun.|
|Diagramme de base|La classe de base de ce diagramme.|(aucune)|
|Name|Le nom de ce diagramme.|Nom actuel|
|Espace de noms|L’espace de noms qui est affilié à ce diagramme.|Espace de noms actuel|
|Classe représentée|La classe de domaine racine qui représente ce diagramme.|Classe racine actuelle le cas échéant|
|Notes|Remarques informelles associées à cet élément.|\<aucune>|
|Couleur de remplissage expose en tant que propriété|Si `True`, l’utilisateur peut définir la couleur de remplissage du diagramme du concepteur généré. Pour définir cette propriété, avec le bouton droit de la forme de diagramme, puis cliquez sur **ajouter les objets exposés**.|False|
|Expose la couleur du texte en tant que propriété|Si `True`, l’utilisateur peut définir la couleur du texte du diagramme dans le concepteur généré. Pour définir cette propriété, avec le bouton droit de la forme de diagramme, puis cliquez sur **ajouter les objets exposés**.|False|
|Description|La description est utilisée pour documenter le concepteur généré.|\<aucune>|
|Nom complet|Le nom qui s’affichera dans le concepteur généré pour ce diagramme.|\<aucune>|
|Help Keyword|Le mot clé qui est utilisé pour indexer l’aide F1 pour ce diagramme.|\<aucune>|

## <a name="see-also"></a>Voir aussi

[Glossaire des outils de langage spécifique à un domaine](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
