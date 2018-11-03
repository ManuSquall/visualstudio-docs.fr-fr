---
title: Propriétés des relations de domaine
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 3ec468ebedbe1d15ddff3527bcf0783b9831247e
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2018
ms.locfileid: "50966438"
---
# <a name="properties-of-domain-relationships"></a>Propriétés des relations de domaine
Les propriétés dans le tableau suivant sont associées à une relation de domaine. Pour plus d’informations sur les relations de domaine, consultez [présentation des modèles, des Classes et des relations](../modeling/understanding-models-classes-and-relationships.md). Pour plus d’informations sur l’utilisation de ces propriétés, consultez [personnalisation et extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Propriété|Description|Par défaut|
|-|-|-|
|Modificateur d'accès|Le niveau d’accès de la relation de domaine (`public` ou `internal`).|`public`|
|Attributs personnalisés|Utilisé pour ajouter des attributs à la classe de code source qui est générée à partir de la relation de domaine.|\<Aucun >|
|Génère le Double dérivée|Si `True`, une classe de base et une classe partielle (pour prendre en charge la personnalisation via des substitutions) est généré. Pour plus d’informations, consultez [substitution et extension des Classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|A le constructeur personnalisé|Si `True`, indique qu’un constructeur personnalisé est fourni dans le code source. Pour plus d’informations, consultez [substitution et extension des Classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Modificateur d’héritage|Décrit le type d’héritage de la classe de code source qui est générée à partir de la relation de domaine (`none`, `abstract` ou `sealed`).|\<Aucun >|
|Autorise les doublons|Si `True`, des liens en double de la relation de domaine peuvent être créés entre les deux mêmes éléments.|`False`|
|Relations de base|Si la relation de domaine est dérivée, la relation de base de la relation de domaine.|\<Aucun >|
|Est l’incorporation|Si `True`, la relation de domaine est une relation d’incorporation. Si `False`, la relation est une relation de référence.|\<les deux >|
|Name|Le nom de la relation de domaine.|Nom actuel|
|Espace de noms|L’espace de noms qui est affilié à la relation de domaine.|Espace de noms actuel|
|Notes|Remarques informelles associées à la relation de domaine.|\<Aucun >|
|Description|La description qui est utilisée pour documenter le code et est utilisée dans l’interface utilisateur du concepteur généré.|\<Aucun >|
|Nom complet|Le nom qui s’affiche dans le concepteur généré pour la relation de domaine.|\<Aucun >|
|Help Keyword|Le mot clé facultatif qui est utilisé pour indexer l’aide F1 pour la relation de domaine.|\<Aucun >|

## <a name="see-also"></a>Voir aussi

- [Glossaire des outils Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)