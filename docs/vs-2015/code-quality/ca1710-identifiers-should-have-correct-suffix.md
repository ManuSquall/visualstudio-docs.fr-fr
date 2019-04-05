---
title: 'CA1710 : Les identificateurs doivent avoir un suffixe correct | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1710
- IdentifiersShouldHaveCorrectSuffix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectSuffix
- CA1710
ms.assetid: 2b8e6dce-b4e8-4a66-ba9a-6b79be5bfe8c
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c5b0336e1f503d3f540fb8129beab57891564ce0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58949258"
---
# <a name="ca1710-identifiers-should-have-correct-suffix"></a>CA1710 : Les identificateurs doivent être dotés d'un suffixe correct
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

 Les conventions d’affectation de noms fournissent une apparence commune pour les bibliothèques qui ciblent le common language runtime. Cela réduit la courbe d’apprentissage qui est requis pour les nouvelles bibliothèques de logiciels et confirment au client que la bibliothèque a été développée par une personne compétente en matière de développement de code managé.

 Le tableau suivant répertorie les types de base et les interfaces qui sont associés à des suffixes.

|Interface/type de base|Suffix|
|--------------------------|------------|
|<xref:System.Attribute?displayProperty=fullName>|Attribut|
|<xref:System.EventArgs?displayProperty=fullName>|EventArgs|
|<xref:System.Exception?displayProperty=fullName>|Exception|
|<xref:System.Collections.ICollection?displayProperty=fullName>|Collection|
|<xref:System.Collections.IDictionary?displayProperty=fullName>|Dictionary|
|<xref:System.Collections.IEnumerable?displayProperty=fullName>|Collection|
|<xref:System.Collections.Queue?displayProperty=fullName>|Collection ou File d'attente|
|<xref:System.Collections.Stack?displayProperty=fullName>|Collection ou Stack|
|<xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>|Collection|
|<xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|Dictionary|
|<xref:System.Data.DataSet?displayProperty=fullName>|DataSet|
|<xref:System.Data.DataTable?displayProperty=fullName>|Collection ou DataTable|
|<xref:System.IO.Stream?displayProperty=fullName>|Stream|
|<xref:System.Security.IPermission?displayProperty=fullName>|Autorisation|
|<xref:System.Security.Policy.IMembershipCondition?displayProperty=fullName>|Condition|
|Un délégué de gestionnaire d’événements.|EventHandler|

 Les types qui implémentent <xref:System.Collections.ICollection> et sont un type généralisé de structure de données, comme un dictionnaire, une pile ou une file d’attente, peuvent avoir des noms qui fournissent des informations explicites sur l’utilisation prévue du type.

 Les types qui implémentent <xref:System.Collections.ICollection> et sont une collection d’éléments spécifiques ont des noms qui se terminent par le mot « Collection ». Par exemple, une collection d’objets <xref:System.Collections.Queue> aurait pour nom « QueueCollection ». Le suffixe 'Collection' signifie que les membres de la collection peuvent être énumérés à l’aide de l’instruction `foreach` (`For Each` dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

 Les types qui implémentent <xref:System.Collections.IDictionary> ont des noms qui se terminent par le mot « Dictionary » même si le type implémente également <xref:System.Collections.IEnumerable> ou <xref:System.Collections.ICollection>. Les conventions d’affectation des suffixes 'Collection' et 'Dictionary' permettent aux utilisateurs de faire la distinction entre les deux modèles d’énumération suivants.

 Les types avec le suffixe 'Collection' suivent le modèle d’énumération suivant.

```
foreach(SomeType x in SomeCollection) { }
```

 Les types avec le suffixe 'Dictionary' suivent le modèle d’énumération suivant.

```
foreach(SomeType x in SomeDictionary.Values) { }
```

 Un objet <xref:System.Data.DataSet> se compose d’une collection d’objets <xref:System.Data.DataTable>, qui consistent en des collections d’objets <xref:System.Data.DataColumn?displayProperty=fullName> et <xref:System.Data.DataRow?displayProperty=fullName>, entre autres. Ces collections implémentent <xref:System.Collections.ICollection> via la classe de base <xref:System.Data.InternalDataCollectionBase?displayProperty=fullName>.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Renommer le type afin qu’il soit suivi du suffixe correct.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement à utiliser le suffixe 'Collection' si le type est une structure de données généralisée susceptible d’être étendue ou qui contiendra un ensemble arbitraire d’éléments divers. Dans ce cas, un nom qui fournit des informations significatives sur l’implémentation, les performances ou d’autres caractéristiques de la structure de données peut être pertinent (par exemple, BinaryTree). Dans les cas où le type représente une collection d’un type spécifique (par exemple, StringCollection), ne supprimez pas un avertissement de cette règle car le suffixe indique que le type peut être énuméré à l’aide d’une instruction `foreach`.

 Pour les autres suffixes, ne supprimez pas d’avertissement de cette règle. Le suffixe permet à l’utilisation prévue d’être évidente à partir du nom du type.

## <a name="related-rules"></a>Règles associées
 [CA1711 : Les identificateurs ne doivent pas porter un suffixe incorrect](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

## <a name="see-also"></a>Voir aussi
 [Attributs](http://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b) [NIB : Événements et délégués](http://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115)
