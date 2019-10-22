---
title: Propriétés des relations de domaine
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26de877643e25413168d074d85a2aeab0794adc1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658188"
---
# <a name="properties-of-domain-relationships"></a>Propriétés des relations de domaine
Les propriétés du tableau suivant sont associées à une relation de domaine. Pour plus d’informations sur les relations de domaine, consultez [Présentation des modèles, des classes et des relations](../modeling/understanding-models-classes-and-relationships.md). Pour plus d’informations sur l’utilisation de ces propriétés, consultez [personnalisation et extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Property|Description|Valeur par défaut|
|-|-|-|
|Modificateur d'accès|Niveau d’accès de la relation de domaine (`public` ou `internal`).|`public`|
|Attributs personnalisés|Utilisé pour ajouter des attributs à la classe de code source qui est générée à partir de la relation de domaine.|\<aucune>|
|Génère un doublon dérivé|Si `True`, une classe de base et une classe partielle (pour prendre en charge la personnalisation via des substitutions) sont générées. Pour plus d’informations, consultez [substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|A un constructeur personnalisé|Si `True`, indique qu’un constructeur personnalisé est fourni dans le code source. Pour plus d’informations, consultez [substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Modificateur d’héritage|Décrit le type d’héritage de la classe de code source qui est généré à partir de la relation de domaine (`none`, `abstract` ou `sealed`).|\<aucune>|
|Autorise les doublons|Si `True`, des liens dupliqués de la relation de domaine peuvent être créés entre les deux mêmes éléments.|`False`|
|Relations de base|Si la relation de domaine est dérivée, il s’agit de la relation de base de la relation de domaine.|\<aucune>|
|Est en incorporation|Si `True`, la relation de domaine est une relation d’incorporation. Si `False`, la relation est une relation de référence.|\<both >|
|Name|Nom de la relation de domaine.|Nom actuel|
|Espace de noms|Espace de noms affilié à la relation de domaine.|Espace de noms actuel|
|Notes|Notes informelles associées à la relation de domaine.|\<aucune>|
|Description|Description utilisée pour documenter le code et utilisée dans l’interface utilisateur du concepteur généré.|\<aucune>|
|Display Name|Nom affiché dans le concepteur généré pour la relation de domaine.|\<aucune>|
|Help Keyword|Mot clé facultatif utilisé pour indexer l’aide F1 pour la relation de domaine.|\<aucune>|

## <a name="see-also"></a>Voir aussi

- [Glossaire des Outils Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)