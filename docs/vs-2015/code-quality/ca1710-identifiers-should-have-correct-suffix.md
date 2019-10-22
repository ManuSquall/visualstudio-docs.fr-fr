---
title: 'CA1710 : les identificateurs doivent avoir un suffixe correct | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7dc0ed72ddab39bda5f3de9b978f4d55dc2358ba
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669165"
---
# <a name="ca1710-identifiers-should-have-correct-suffix"></a>CA1710 : Les identificateurs doivent être dotés d'un suffixe correct
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectSuffix|
|CheckId|CA1710|
|Category|Microsoft. Naming|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un identificateur n’a pas le suffixe correct.

## <a name="rule-description"></a>Description de la règle
 Par Convention, les noms des types qui étendent certains types de base ou qui implémentent certaines interfaces, ou des types dérivés de ces types, ont un suffixe associé à l’interface ou au type de base.

 Les conventions d’affectation de noms fournissent une recherche commune pour les bibliothèques qui ciblent le common language runtime. Cela réduit la courbe d’apprentissage requise pour les nouvelles bibliothèques logicielles et augmente la confiance des clients dans la mesure où la bibliothèque a été développée par une personne ayant une expertise dans le développement de code géré.

 Le tableau suivant répertorie les types de base et les interfaces qui ont des suffixes associés.

|Type/interface de base|Suffixe|
|--------------------------|------------|
|<xref:System.Attribute?displayProperty=fullName>|Attribut|
|<xref:System.EventArgs?displayProperty=fullName>|EventArgs|
|<xref:System.Exception?displayProperty=fullName>|Exception|
|<xref:System.Collections.ICollection?displayProperty=fullName>|Collection|
|<xref:System.Collections.IDictionary?displayProperty=fullName>|Dictionary|
|<xref:System.Collections.IEnumerable?displayProperty=fullName>|Collection|
|<xref:System.Collections.Queue?displayProperty=fullName>|Collection ou file d’attente|
|<xref:System.Collections.Stack?displayProperty=fullName>|Collection ou pile|
|<xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>|Collection|
|<xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|Dictionary|
|<xref:System.Data.DataSet?displayProperty=fullName>|DataSet|
|<xref:System.Data.DataTable?displayProperty=fullName>|Collection ou DataTable|
|<xref:System.IO.Stream?displayProperty=fullName>|Flux|
|<xref:System.Security.IPermission?displayProperty=fullName>|Autorisation|
|<xref:System.Security.Policy.IMembershipCondition?displayProperty=fullName>|Condition|
|Délégué de gestionnaire d’événements.|Délégué|

 Les types qui implémentent <xref:System.Collections.ICollection> et sont un type généralisé de structure de données, tel qu’un dictionnaire, une pile ou une file d’attente, sont des noms autorisés qui fournissent des informations explicites sur l’utilisation prévue du type.

 Les types qui implémentent <xref:System.Collections.ICollection> et sont une collection d’éléments spécifiques dont les noms se terminent par le mot’collection'. Par exemple, une collection d’objets <xref:System.Collections.Queue> porterait le nom’QueueCollection'. Le suffixe’collection’signifie que les membres de la collection peuvent être énumérés à l’aide de l’instruction `foreach` (`For Each` dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

 Les types qui implémentent <xref:System.Collections.IDictionary> ont des noms qui se terminent par le mot « dictionary », même si le type implémente également <xref:System.Collections.IEnumerable> ou <xref:System.Collections.ICollection>. Les conventions d’affectation des noms des suffixes « collection » et « dictionary » permettent aux utilisateurs de faire la distinction entre les deux modèles d’énumération suivants.

 Les types avec le suffixe’collection’suivent ce modèle d’énumération.

```
foreach(SomeType x in SomeCollection) { }
```

 Les types avec le suffixe « dictionary » suivent ce modèle d’énumération.

```
foreach(SomeType x in SomeDictionary.Values) { }
```

 Un objet <xref:System.Data.DataSet> se compose d’une collection d’objets <xref:System.Data.DataTable>, qui se composent de collections d’objets <xref:System.Data.DataColumn?displayProperty=fullName> et <xref:System.Data.DataRow?displayProperty=fullName>, entre autres. Ces collections implémentent <xref:System.Collections.ICollection> par le biais de la classe de base <xref:System.Data.InternalDataCollectionBase?displayProperty=fullName>.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Renommez le type de manière à ce qu’il soit suivi du terme correct.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement pour utiliser le suffixe’collection’si le type est une structure de données généralisée qui peut être étendue ou qui contiendra un ensemble arbitraire d’éléments divers. Dans ce cas, un nom qui fournit des informations explicites sur l’implémentation, les performances ou d’autres caractéristiques de la structure de données peut être utile (par exemple, BinaryTree). Dans les cas où le type représente une collection d’un type spécifique (par exemple, StringCollection), ne supprimez pas un avertissement de cette règle, car le suffixe indique que le type peut être énuméré à l’aide d’une instruction `foreach`.

 Pour les autres suffixes, ne supprimez pas un avertissement de cette règle. Le suffixe permet à l’utilisation prévue d’être évidente à partir du nom de type.

## <a name="related-rules"></a>Règles associées
 [CA1711 : Les identificateurs ne doivent pas avoir un suffixe incorrect](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

## <a name="see-also"></a>Voir aussi
 Plume d' [attributs](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b) [: événements et délégués](https://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115)
