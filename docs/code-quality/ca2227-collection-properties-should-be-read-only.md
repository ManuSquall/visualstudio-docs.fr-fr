---
title: 'CA2227 : Les propriétés de collection doivent être en lecture seule'
ms.date: 09/28/2018
ms.topic: reference
f1_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
helpviewer_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 8a6ced277aa442450418ce55f4e1db56ad5d8af1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806535"
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227 : Les propriétés de collection doivent être en lecture seule

|||
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|Category|Microsoft.Usage|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Une propriété accessible en écriture extérieurement visible est d’un type qui implémente <xref:System.Collections.ICollection?displayProperty=fullName>. Cette règle ignore les tableaux, les indexeurs (propriétés portant le nom 'Item') et les jeux d’autorisations.

## <a name="rule-description"></a>Description de la règle

Une propriété de collection accessible en écriture permet à un utilisateur de remplacer la collection par une collection complètement différente. Une propriété en lecture seule s’arrête à la collection ne soit pas remplacé, tout en permettant les membres individuels à définir. Si le remplacement de la collection est un objectif, le modèle de conception par défaut consiste à inclure une méthode pour supprimer tous les éléments de la collection et une méthode pour remplir la collection. Consultez le <xref:System.Collections.ArrayList.Clear%2A> et <xref:System.Collections.ArrayList.AddRange%2A> méthodes de la <xref:System.Collections.ArrayList?displayProperty=fullName> classe pour obtenir un exemple de ce modèle.

Binaire et sérialisation XML prend en charge les propriétés en lecture seule qui sont des collections. Le <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> classe a des exigences spécifiques pour les types qui implémentent <xref:System.Collections.ICollection> et <xref:System.Collections.IEnumerable?displayProperty=fullName> afin d’être sérialisable.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, rendez la propriété en lecture seule. Si la conception exige, ajoutez des méthodes pour effacer et de remplir la collection.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Vous pouvez supprimer l’avertissement si la propriété fait partie d’un [objet de transfert de données (DTO)](/previous-versions/msp-n-p/ff649585(v=pandp.10)) classe.

Sinon, ne supprimez pas les avertissements de cette règle.

## <a name="example"></a>Exemple

L’exemple suivant illustre un type avec une propriété de collection accessible en écriture et montre comment la collection peut être remplacée directement. En outre, il montre la meilleure manière de remplacer une propriété de collection en lecture seule à l’aide `Clear` et `AddRange` méthodes.

[!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CSharp/ca2227-collection-properties-should-be-read-only_1.cs)]
[!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/VisualBasic/ca2227-collection-properties-should-be-read-only_1.vb)]
[!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CPP/ca2227-collection-properties-should-be-read-only_1.cpp)]

## <a name="related-rules"></a>Règles associées

- [CA1819 : Propriétés ne doivent pas retourner de tableaux](../code-quality/ca1819-properties-should-not-return-arrays.md)