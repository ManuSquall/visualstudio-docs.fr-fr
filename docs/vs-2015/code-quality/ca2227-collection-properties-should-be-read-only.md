---
title: 'CA2227 : les propriétés de collection doivent être en lecture seule | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
helpviewer_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8aee6f7172414de809d964652411c1f077fe0cdd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658870"
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227 : Les propriétés de collection doivent être en lecture seule
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|Category|Microsoft. usage|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une propriété accessible en écriture de manière externe est un type qui implémente <xref:System.Collections.ICollection?displayProperty=fullName>. Les tableaux, les indexeurs (propriétés portant le nom « Item ») et les jeux d’autorisations sont ignorés par la règle.

## <a name="rule-description"></a>Description de la règle
 Une propriété de collection accessible en écriture permet à un utilisateur de remplacer la collection par une collection complètement différente. Une propriété en lecture seule empêche le remplacement de la collection, mais permet quand même aux membres individuels d’être définis. Si le remplacement de la collection est un objectif, le modèle de conception par défaut consiste à inclure une méthode pour supprimer tous les éléments de la collection et une méthode pour remplir à nouveau la collection. Pour obtenir un exemple de ce modèle, consultez les méthodes <xref:System.Collections.ArrayList.Clear%2A> et <xref:System.Collections.ArrayList.AddRange%2A> de la classe <xref:System.Collections.ArrayList?displayProperty=fullName>.

 La sérialisation binaire et la sérialisation XML prennent toutes deux en charge les propriétés en lecture seule qui sont des collections. La classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> a des exigences spécifiques pour les types qui implémentent <xref:System.Collections.ICollection> et <xref:System.Collections.IEnumerable?displayProperty=fullName> afin d’être sérialisable.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, définissez la propriété en lecture seule et, si la conception l’exige, ajoutez des méthodes pour effacer et remplir de nouveau la collection.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type avec une propriété de collection accessible en écriture et montre comment la collection peut être remplacée directement. En outre, le mode de remplacement par défaut d’une propriété de collection en lecture seule à l’aide des méthodes `Clear` et `AddRange` est affiché.

 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cpp/FxCop.Usage.PropertiesReturningCollections.cpp#1)]
 [!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cs/FxCop.Usage.PropertiesReturningCollections.cs#1)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/vb/FxCop.Usage.PropertiesReturningCollections.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1819 : Les propriétés ne doivent pas retourner des tableaux](../code-quality/ca1819-properties-should-not-return-arrays.md)
