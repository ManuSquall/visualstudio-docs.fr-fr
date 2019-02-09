---
title: "CA1710 : Les identificateurs doivent être dotés d'un suffixe correct"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1710
- IdentifiersShouldHaveCorrectSuffix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectSuffix
- CA1710
ms.assetid: 2b8e6dce-b4e8-4a66-ba9a-6b79be5bfe8c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4a3c602c249c7507d516e74c32f2d4db8447b645
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55944453"
---
# <a name="ca1710-identifiers-should-have-correct-suffix"></a>CA1710 : Les identificateurs doivent être dotés d'un suffixe correct

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectSuffix|
|CheckId|CA1710|
|Category|Microsoft.Naming|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Un identificateur n’a pas le suffixe correct.

## <a name="rule-description"></a>Description de la règle

Par convention, les noms des types qui étendent certains types de base ou qui implémentent certaines interfaces, ou les types dérivés de ces types, présentent un suffixe qui est associé au type de base ou interface.

Conventions d’affectation de noms fournissent une apparence commune pour les bibliothèques qui ciblent le common language runtime. Cela réduit la courbe d’apprentissage qui est requis pour les nouvelles bibliothèques de logiciels et confirment au client que la bibliothèque a été développée par une personne compétente en matière de développement de code managé.

Le tableau suivant répertorie les types de base et les interfaces qui sont associés à des suffixes.

|Interface/type de base|Suffix|
|--------------------------|------------|
|<xref:System.Attribute?displayProperty=fullName>|Attribut|
|<xref:System.EventArgs?displayProperty=fullName>|EventArgs|
|<xref:System.Exception?displayProperty=fullName>|Exception|
|<xref:System.Collections.ICollection?displayProperty=fullName>|Collection|
|<xref:System.Collections.IDictionary?displayProperty=fullName>|Dictionary|
|<xref:System.Collections.IEnumerable?displayProperty=fullName>|Collection|
|<xref:System.Collections.Queue?displayProperty=fullName>|File d’attente ou de collection|
|<xref:System.Collections.Stack?displayProperty=fullName>|Collection ou Stack|
|<xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>|Collection|
|<xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|Dictionary|
|<xref:System.Data.DataSet?displayProperty=fullName>|DataSet|
|<xref:System.Data.DataTable?displayProperty=fullName>|Collection ou un DataTable|
|<xref:System.IO.Stream?displayProperty=fullName>|Flux|
|<xref:System.Security.IPermission?displayProperty=fullName>|Autorisation|
|<xref:System.Security.Policy.IMembershipCondition?displayProperty=fullName>|Condition|
|Un délégué de gestionnaire d’événements.|EventHandler|

Types qui implémentent <xref:System.Collections.ICollection> et sont un type généralisé de structure de données, comme un dictionnaire, la pile ou la file d’attente, sont des noms autorisés qui fournissent des informations explicites sur l’utilisation prévue du type.

Types qui implémentent <xref:System.Collections.ICollection> et sont une collection d’éléments spécifiques ont des noms qui se terminent par le mot « Collection ». Par exemple, une collection de <xref:System.Collections.Queue> objets aurait pour nom « QueueCollection ». Le suffixe 'Collection' signifie que les membres de la collection peuvent être énumérés à l’aide de la `foreach` (`For Each` dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) instruction.

Types qui implémentent <xref:System.Collections.IDictionary> ont des noms qui se terminent par le mot « Dictionary » même si le type implémente également <xref:System.Collections.IEnumerable> ou <xref:System.Collections.ICollection>. Les conventions d’affectation de noms de suffixe 'Collection' et 'Dictionary' permettent aux utilisateurs de faire la distinction entre les modèles de deux énumération suivants.

Types avec le suffixe 'Collection' procèdent de cette énumération.

```
foreach(SomeType x in SomeCollection) { }
```

Types avec le suffixe 'Dictionary' procèdent de cette énumération.

```
foreach(SomeType x in SomeDictionary.Values) { }
```

Un <xref:System.Data.DataSet> objet se compose d’une collection de <xref:System.Data.DataTable> objets, qui consistent en des collections de <xref:System.Data.DataColumn?displayProperty=fullName> et <xref:System.Data.DataRow?displayProperty=fullName> objects, parmi d’autres. Ces collections implémentent <xref:System.Collections.ICollection> via la base de <xref:System.Data.InternalDataCollectionBase?displayProperty=fullName> classe.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Renommer le type afin qu’il est suivi du suffixe le terme correct.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer un avertissement à utiliser le suffixe 'Collection' Si le type est une structure de données généralisée susceptible d’être étendue ou qui contiendra un ensemble arbitraire d’éléments divers. Dans ce cas, un nom qui fournit des informations significatives sur l’implémentation, de performances ou d’autres caractéristiques de la structure de données peut être pertinent (par exemple, BinaryTree). Dans les cas où le type représente une collection d’un type spécifique (par exemple, StringCollection), ne supprimez pas un avertissement de cette règle car le suffixe indique que le type peut être énuméré à l’aide un `foreach` instruction.

Pour les autres suffixes, ne supprimez pas d’avertissement de cette règle. Le suffixe permet l’utilisation prévue être évidente à partir du nom de type.

## <a name="related-rules"></a>Règles associées

[CA1711 : Les identificateurs ne doivent pas porter un suffixe incorrect](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

## <a name="see-also"></a>Voir aussi

- [Attributs](/dotnet/standard/design-guidelines/attributes)
- [Gestion et déclenchement d’événements](/dotnet/standard/events/index)