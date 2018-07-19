---
title: 'CA2227 : Les propriétés de collection doivent être en lecture seule'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: aa1d8644049f78eccfda7402360bdbc930b61601
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2018
ms.locfileid: "34447672"
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227 : Les propriétés de collection doivent être en lecture seule

|||
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|Category|Microsoft.Usage|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Une propriété accessible en écriture extérieurement visible est d’un type qui implémente <xref:System.Collections.ICollection?displayProperty=fullName>. Cette règle ignore les tableaux, les indexeurs (propriétés portant le nom 'Item') et les jeux d’autorisations.

## <a name="rule-description"></a>Description de la règle

Une propriété de collection accessible en écriture permet à un utilisateur de remplacer la collection par une collection complètement différente. Une propriété en lecture seule empêche la collection en cours de remplacement, mais permet quand même aux membres individuels d’être définie. Si le remplacement de la collection est un objectif, le modèle de conception par défaut consiste à inclure une méthode pour supprimer tous les éléments de la collection et une méthode pour remplir la collection. Consultez le <xref:System.Collections.ArrayList.Clear%2A> et <xref:System.Collections.ArrayList.AddRange%2A> méthodes de la <xref:System.Collections.ArrayList?displayProperty=fullName> classe pour obtenir un exemple de ce modèle.

Binaire et la sérialisation XML prend en charge les propriétés en lecture seule qui sont des collections. Le <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> classe a des exigences spécifiques pour les types qui implémentent <xref:System.Collections.ICollection> et <xref:System.Collections.IEnumerable?displayProperty=fullName> afin d’être sérialisables.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, rendez la propriété en lecture seule. Si la conception impose, ajouter des méthodes pour effacer et de remplir la collection.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple

L’exemple suivant montre un type avec une propriété de collection accessible en écriture et montre comment la collection peut être remplacée directement. En outre, la meilleure manière de remplacer une propriété de collection en lecture seule à l’aide de `Clear` et `AddRange` méthodes s’affiche.

[!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CSharp/ca2227-collection-properties-should-be-read-only_1.cs)]
[!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/VisualBasic/ca2227-collection-properties-should-be-read-only_1.vb)]
[!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CPP/ca2227-collection-properties-should-be-read-only_1.cpp)]

## <a name="related-rules"></a>Règles associées

[CA1819 : Les propriétés ne doivent pas retourner des tableaux](../code-quality/ca1819-properties-should-not-return-arrays.md)