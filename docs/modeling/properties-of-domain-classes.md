---
title: Propriétés des classes de domaine
description: En savoir plus sur les différentes propriétés des classes de domaine, telles que le modificateur d’accès, les attributs personnalisés, et la génération de doublons.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain class
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: eaaae0028d574a521319ae045cdb4f7f1bdafaa2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390006"
---
# <a name="properties-of-domain-classes"></a>Propriétés des classes de domaine
Les classes de domaine ont les propriétés dans le tableau suivant. Pour plus d’informations sur les classes de domaine, consultez [Présentation des modèles, des classes et des relations](../modeling/understanding-models-classes-and-relationships.md). Pour plus d’informations sur l’utilisation de ces propriétés, consultez [personnalisation et extension d’un langage de Domain-Specific](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Propriété|Description|Default|
|-|-|-|
|Modificateur d'accès|Niveau d'accès de la classe de domaine (`public` ou `internal`).|`public`|
|Attributs personnalisés|Utilisé pour ajouter des attributs à la classe de code source qui est générée à partir de cette classe de domaine.|\<none>|
|Génère un doublon dérivé|Si `True` la valeur est, une classe de base et une classe partielle (pour prendre en charge la personnalisation via des substitutions) sont générées. Pour plus d’informations, consultez [substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|A un constructeur personnalisé|Si `True` , un constructeur personnalisé est fourni dans le code source. Pour plus d’informations, consultez [substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Modificateur d’héritage|Décrit le type d’héritage de la classe de code source qui est généré à partir de la classe de domaine ( `none` , `abstract` ou `sealed` ).|`none`|
|Classe de base|Si cette classe de domaine est dérivée, il s’agit du nom de la classe de base.|\<none>|
|Nom|Nom de cette classe de domaine.|Nom actuel|
|Espace de noms|Espace de noms de cette classe de domaine.|Espace de noms actuel|
|Notes|Notes informelles associées à cette classe de domaine.|\<none>|
|Description|Description utilisée pour documenter l’interface utilisateur du concepteur généré.|\<none>|
|Nom d’affichage|Nom qui sera affiché dans le concepteur généré pour cette classe de domaine.|\<none>|
|Help Keyword|Mot clé facultatif utilisé pour indexer l’aide F1 pour cette classe de domaine.|\<none>|

## <a name="see-also"></a>Voir aussi

- [Glossaire des Outils Domain-Specific Language](/previous-versions/bb126564(v=vs.100))