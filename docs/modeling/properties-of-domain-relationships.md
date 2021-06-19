---
title: Propriétés des relations de domaine
description: En savoir plus sur les propriétés associées à un domaine relationshop, telles que le modificateur d’accès, les attributs personnalisés et la génération de doublons.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fc92bbc32a454208f3d455734b7697a2e69037b4
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390657"
---
# <a name="properties-of-domain-relationships"></a>Propriétés des relations de domaine
Les propriétés du tableau suivant sont associées à une relation de domaine. Pour plus d’informations sur les relations de domaine, consultez [Présentation des modèles, des classes et des relations](../modeling/understanding-models-classes-and-relationships.md). Pour plus d’informations sur l’utilisation de ces propriétés, consultez [personnalisation et extension d’un langage de Domain-Specific](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Propriété|Description|Default|
|-|-|-|
|Modificateur d'accès|Niveau d’accès de la relation de domaine ( `public` ou `internal` ).|`public`|
|Attributs personnalisés|Utilisé pour ajouter des attributs à la classe de code source qui est générée à partir de la relation de domaine.|\<none>|
|Génère un doublon dérivé|Si `True` la valeur est, une classe de base et une classe partielle (pour prendre en charge la personnalisation via des substitutions) sont générées. Pour plus d’informations, consultez [substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|A un constructeur personnalisé|Si `True` , indique qu’un constructeur personnalisé est fourni dans le code source. Pour plus d’informations, consultez [substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Modificateur d’héritage|Décrit le type d’héritage de la classe de code source qui est généré à partir de la relation de domaine ( `none` , `abstract` ou `sealed` ).|\<none>|
|Autorise les doublons|Si `True` la condition est, des liens dupliqués de la relation de domaine peuvent être créés entre les deux mêmes éléments.|`False`|
|Relations de base|Si la relation de domaine est dérivée, il s’agit de la relation de base de la relation de domaine.|\<none>|
|Est en incorporation|Si `True` la, la relation de domaine est une relation d’incorporation. Si `False` , la relation est une relation de référence.|\<both>|
|Nom|Nom de la relation de domaine.|Nom actuel|
|Espace de noms|Espace de noms affilié à la relation de domaine.|Espace de noms actuel|
|Notes|Notes informelles associées à la relation de domaine.|\<none>|
|Description|Description utilisée pour documenter le code et utilisée dans l’interface utilisateur du concepteur généré.|\<none>|
|Nom d’affichage|Nom affiché dans le concepteur généré pour la relation de domaine.|\<none>|
|Help Keyword|Mot clé facultatif utilisé pour indexer l’aide F1 pour la relation de domaine.|\<none>|

## <a name="see-also"></a>Voir aussi

- [Glossaire des Outils Domain-Specific Language](/previous-versions/bb126564(v=vs.100))