---
title: 'CA1711 : les identificateurs ne doivent pas avoir un suffixe incorrect | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1711
- IdentifiersShouldNotHaveIncorrectSuffix
helpviewer_keywords:
- CA1711
- IdentifiersShouldNotHaveIncorrectSuffix
ms.assetid: a63359ab-386d-44ae-b381-ee3a983aca29
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f59a1c88701cf132a46c66eb6550f03eb870d63d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669176"
---
# <a name="ca1711-identifiers-should-not-have-incorrect-suffix"></a>CA1711 : Les identificateurs ne doivent pas porter un suffixe incorrect
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectSuffix|
|CheckId|CA1711|
|Category|Microsoft. Naming|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un identificateur a un suffixe incorrect.

## <a name="rule-description"></a>Description de la règle
 Par Convention, seuls les noms des types qui étendent certains types de base ou qui implémentent certaines interfaces, ou des types dérivés de ces types, doivent se terminer par des suffixes réservés spécifiques. Les autres noms de types ne doivent pas utiliser ces suffixes réservés.

 Le tableau suivant répertorie les suffixes réservés et les types de base et les interfaces auxquels ils sont associés.

|Suffixe|Type/interface de base|
|------------|--------------------------|
|Attribut|<xref:System.Attribute?displayProperty=fullName>|
|Collection|<xref:System.Collections.ICollection?displayProperty=fullName><br /><br /> <xref:System.Collections.IEnumerable?displayProperty=fullName><br /><br /> <xref:System.Collections.Queue?displayProperty=fullName><br /><br /> <xref:System.Collections.Stack?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName><br /><br /> <xref:System.Data.DataSet?displayProperty=fullName><br /><br /> <xref:System.Data.DataTable?displayProperty=fullName>|
|Dictionary|<xref:System.Collections.IDictionary?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|
|EventArgs|<xref:System.EventArgs?displayProperty=fullName>|
|Délégué|Délégué de gestionnaire d’événements|
|Exception|<xref:System.Exception?displayProperty=fullName>|
|Autorisation|<xref:System.Security.IPermission?displayProperty=fullName>|
|File d'attente|<xref:System.Collections.Queue?displayProperty=fullName>|
|Stack|<xref:System.Collections.Stack?displayProperty=fullName>|
|Flux|<xref:System.IO.Stream?displayProperty=fullName>|

 En outre, les suffixes suivants ne doivent **pas** être utilisés :

- délégué

- Enum

- Impl : utilisez’Core’à la place

- Ex ou suffixe similaire pour le distinguer d’une version antérieure du même type

  Les conventions d’affectation de noms fournissent une recherche commune pour les bibliothèques qui ciblent le common language runtime. Cela réduit la courbe d’apprentissage requise pour les nouvelles bibliothèques logicielles et augmente la confiance des clients dans la mesure où la bibliothèque a été développée par une personne ayant une expertise dans le développement de code géré.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Supprimez le suffixe du nom de type.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas un avertissement de cette règle, sauf si le suffixe a une signification non ambiguë dans le domaine d’application.

## <a name="related-rules"></a>Règles associées
 [CA1710 : Les identificateurs doivent avoir un suffixe correct](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)

## <a name="see-also"></a>Voir aussi
 Plume d' [attributs](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b) [: événements et délégués](https://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115)
