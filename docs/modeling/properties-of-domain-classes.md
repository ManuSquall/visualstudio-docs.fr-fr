---
title: Propriétés des classes de domaine
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain class
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 799b5d2feafbf4a0e7b6ff54673983a585b0d2fe
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53876888"
---
# <a name="properties-of-domain-classes"></a>Propriétés des classes de domaine
Classes de domaine ont les propriétés dans le tableau suivant. Pour plus d’informations sur les classes de domaine, consultez [présentation des modèles, des Classes et des relations](../modeling/understanding-models-classes-and-relationships.md). Pour plus d’informations sur l’utilisation de ces propriétés, consultez [personnalisation et extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Propriété|Description|Par défaut|
|-|-|-|
|Modificateur d'accès|Niveau d'accès de la classe de domaine (`public` ou `internal`).|`public`|
|Attributs personnalisés|Utilisé pour ajouter des attributs à la classe de code source qui est générée à partir de cette classe de domaine.|\<Aucun >|
|Génère le Double dérivée|Si `True`, une classe de base et une classe partielle (pour prendre en charge la personnalisation via des substitutions) sont générés. Pour plus d’informations, consultez [substitution et extension des Classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|A le constructeur personnalisé|Si `True`, un constructeur personnalisé est fourni dans le code source. Pour plus d’informations, consultez [substitution et extension des Classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Modificateur d’héritage|Décrit le type d’héritage de la classe de code source qui est générée à partir de la classe de domaine (`none`, `abstract` ou `sealed`).|`none`|
|Classe de base|Si cette classe de domaine est dérivée, le nom de la classe de base.|\<Aucun >|
|Name|Le nom de cette classe de domaine.|Nom actuel|
|Espace de noms|L’espace de noms de cette classe de domaine.|Espace de noms actuel|
|Notes|Remarques informelles associées à cette classe de domaine.|\<Aucun >|
|Description|La description est utilisée pour documenter l’interface utilisateur du concepteur généré.|\<Aucun >|
|Nom complet|Le nom qui s’affichera dans le concepteur généré pour cette classe de domaine.|\<Aucun >|
|Help Keyword|Le mot clé facultatif qui est utilisé pour indexer l’aide F1 pour cette classe de domaine.|\<Aucun >|

## <a name="see-also"></a>Voir aussi

- [Glossaire des outils Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)