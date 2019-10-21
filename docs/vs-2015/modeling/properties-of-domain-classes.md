---
title: Propriétés des classes de domaine | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain class
ms.assetid: a3993995-19e7-4761-a972-b1de89131a1b
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 91599e17fc132001de9fbb1a62a62918321a2dea
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652004"
---
# <a name="properties-of-domain-classes"></a>Propriétés des classes de domaine
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les classes de domaine ont les propriétés dans le tableau suivant. Pour plus d’informations sur les classes de domaine, consultez [Présentation des modèles, des classes et des relations](../modeling/understanding-models-classes-and-relationships.md). Pour plus d’informations sur l’utilisation de ces propriétés, consultez [personnalisation et extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Property|Description|Valeur par défaut|
|--------------|-----------------|-------------|
|Modificateur d'accès|Niveau d'accès de la classe de domaine (`public` ou `internal`).|`public`|
|Attributs personnalisés|Utilisé pour ajouter des attributs à la classe de code source qui est générée à partir de cette classe de domaine.|\<aucune>|
|Génère un doublon dérivé|Si `True`, une classe de base et une classe partielle (pour prendre en charge la personnalisation via des substitutions) sont générées. Pour plus d’informations, consultez [substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|A un constructeur personnalisé|Si `True`, un constructeur personnalisé est fourni dans le code source. Pour plus d’informations, consultez [substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Modificateur d’héritage|Décrit le type d’héritage de la classe de code source qui est généré à partir de la classe de domaine (`none`, `abstract` ou `sealed`).|`none`|
|Classe de base|Si cette classe de domaine est dérivée, il s’agit du nom de la classe de base.|\<aucune>|
|Name|Nom de cette classe de domaine.|Nom actuel|
|Espace de noms|Espace de noms de cette classe de domaine.|Espace de noms actuel|
|Notes|Notes informelles associées à cette classe de domaine.|\<aucune>|
|Description|Description utilisée pour documenter l’interface utilisateur du concepteur généré.|\<aucune>|
|Display Name|Nom qui sera affiché dans le concepteur généré pour cette classe de domaine.|\<aucune>|
|Help Keyword|Mot clé facultatif utilisé pour indexer l’aide F1 pour cette classe de domaine.|\<aucune>|

## <a name="see-also"></a>Voir aussi
 [Glossaire des Outils Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
