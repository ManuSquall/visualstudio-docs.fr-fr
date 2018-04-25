---
title: Propriétés des diagrammes
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: bd02bd7f91d80392553d4c9f5e7ff10ab71b1abe
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2018
---
# <a name="properties-of-diagrams"></a>Propriétés des diagrammes
Vous pouvez définir des propriétés qui spécifient comment les diagrammes seront affichera dans le concepteur généré. Par exemple, vous pouvez spécifier une couleur par défaut pour le texte dans le diagramme.

 Pour plus d’informations, consultez [comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md). Pour plus d’informations sur la façon d’utiliser ces propriétés, consultez [personnalisation et l’extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Le tableau suivant répertorie les propriétés de diagrammes.

|Propriété|Description|Par défaut|
|--------------|-----------------|-------------|
|Couleur de remplissage|La couleur de remplissage pour le diagramme.|Blanc|
|Couleur du texte|La couleur du texte qui s’affiche sur le diagramme.|Noir|
|Modificateur d'accès|Le modificateur d’accès de la classe (public ou internal).|Public|
|Attributs personnalisés|Utilisé pour ajouter des attributs à la classe du code généré.|\<Aucun >|
|Génère deux dérivées|Si `True`, une classe de base et une classe partielle (pour la personnalisation par des remplacements) seront générés. Pour plus d’informations, consultez [substituer et étendre les Classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|A constructeur personnalisé|Si `True`, un constructeur personnalisé sera fourni dans le code source. Pour plus d’informations, consultez [substituer et étendre les Classes générées](../modeling/overriding-and-extending-the-generated-classes.md)...|False|
|Modificateur d’héritage|Décrit le type d’héritage de la classe de code source qui est générée à partir du diagramme (`none`, `abstract` ou `sealed`).|Aucun|
|Diagramme de base|La classe de base de ce schéma.|(aucune)|
|Name|Le nom de ce schéma.|Nom actuel|
|Espace de noms|L’espace de noms n’est affilié à ce schéma.|Espace de noms actuel|
|Classe représentée|La classe de domaine racine représentant ce diagramme.|Classe racine actuelle le cas échéant|
|Notes|Notes informelles qui sont associés à cet élément.|\<Aucun >|
|Couleur de remplissage expose en tant que propriété|Si `True`, l’utilisateur peut définir la couleur de remplissage du diagramme du concepteur généré. Pour configurer cela, cliquez avec le bouton droit sur la forme de diagramme, puis cliquez sur **Explosed d’ajouter**.|False|
|Expose la couleur du texte en tant que propriété|Si `True`, l’utilisateur peut définir la couleur du texte du diagramme dans le concepteur généré. Pour configurer cela, cliquez avec le bouton droit sur la forme de diagramme, puis cliquez sur **Explosed d’ajouter**.|False|
|Description|La description qui est utilisée pour documenter le concepteur généré.|\<Aucun >|
|Nom complet|Le nom qui sera affiché dans le concepteur généré pour ce schéma.|\<Aucun >|
|Help Keyword|Le mot clé qui est utilisé pour l’index d’aide (F1) pour ce diagramme.|\<Aucun >|

## <a name="see-also"></a>Voir aussi

- [Glossaire des outils de langage spécifique à un domaine](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)