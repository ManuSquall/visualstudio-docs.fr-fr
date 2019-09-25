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
ms.openlocfilehash: 3d097a67c9a62a6847ff6ab0bb882257c082ca6f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231303"
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227 : Les propriétés de collection doivent être en lecture seule

|||
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|Category|Microsoft.Usage|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Une propriété accessible en écriture, visible de l’extérieur, est d’un <xref:System.Collections.ICollection?displayProperty=fullName>type qui implémente. Cette règle ignore les tableaux, les indexeurs (propriétés portant le nom « Item ») et les jeux d’autorisations.

## <a name="rule-description"></a>Description de la règle

Une propriété de collection accessible en écriture permet à un utilisateur de remplacer la collection par une collection complètement différente. Une propriété en lecture seule empêche le remplacement de la collection, mais permet toujours de définir les membres individuels. Si le remplacement de la collection est un objectif, le modèle de conception par défaut consiste à inclure une méthode pour supprimer tous les éléments de la collection, et une méthode pour remplir à nouveau la collection. Pour obtenir <xref:System.Collections.ArrayList.Clear%2A> un <xref:System.Collections.ArrayList.AddRange%2A> exemple de ce <xref:System.Collections.ArrayList?displayProperty=fullName> modèle, consultez les méthodes et de la classe.

La sérialisation binaire et la sérialisation XML prennent toutes deux en charge les propriétés en lecture seule qui sont des collections. La <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> classe a des exigences spécifiques pour les types <xref:System.Collections.ICollection> qui <xref:System.Collections.IEnumerable?displayProperty=fullName> implémentent et afin d’être sérialisables.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, définissez la propriété en lecture seule. Si la conception l’exige, ajoutez des méthodes pour effacer et remplir de nouveau la collection.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Vous pouvez supprimer l’avertissement si la propriété fait partie d’une classe d' [objets transfert de données (DTO)](/previous-versions/msp-n-p/ff649585(v=pandp.10)) .

Dans le cas contraire, ne supprimez pas les avertissements de cette règle.

## <a name="example"></a>Exemple

L’exemple suivant montre un type avec une propriété de collection accessible en écriture et montre comment la collection peut être remplacée directement. En outre, il montre le mode de remplacement par défaut d’une propriété de collection en `Clear` lecture `AddRange` seule à l’aide des méthodes et.

[!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CSharp/ca2227-collection-properties-should-be-read-only_1.cs)]
[!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/VisualBasic/ca2227-collection-properties-should-be-read-only_1.vb)]
[!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CPP/ca2227-collection-properties-should-be-read-only_1.cpp)]

## <a name="related-rules"></a>Règles associées

- [CA1819 Les propriétés ne doivent pas retourner des tableaux](../code-quality/ca1819-properties-should-not-return-arrays.md)