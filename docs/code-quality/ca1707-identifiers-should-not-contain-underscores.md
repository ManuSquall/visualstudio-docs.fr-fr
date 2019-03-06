---
title: 'CA1707 : Les identificateurs ne doivent pas contenir de traits de soulignement'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1cbd6d3999525808180f69652290807d327b6814
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55917738"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707 : Les identificateurs ne doivent pas contenir de traits de soulignement

|||
|-|-|
|TypeName|IdentifiersShouldNotContainUnderscores|
|CheckId|CA1707|
|Category|Microsoft.Naming|
|Modification avec rupture|Rupture - lorsque déclenchée sur les assemblys<br /><br /> Sans rupture - lorsque déclenchée sur les paramètres de type|

## <a name="cause"></a>Cause

Le nom d’un identificateur contient le caractère de soulignement (\_) caractères.

## <a name="rule-description"></a>Description de la règle

Par convention, les noms d’identificateurs ne contiennent pas le caractère de soulignement (\_) caractères. La règle vérifie les espaces de noms, types, membres et paramètres.

Conventions d’affectation de noms fournissent une apparence commune pour les bibliothèques qui ciblent le common language runtime. Cela réduit la courbe d’apprentissage qui est requis pour les nouvelles bibliothèques de logiciels et confirment au client que la bibliothèque a été développée par une personne compétente en matière de développement de code managé.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Supprimez tous les traits de soulignement du nom.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez aucun avertissement de cette règle.

## <a name="related-rules"></a>Règles associées

- [CA1709 : Identificateurs doivent être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708 : Les identificateurs doivent différer par leur casse](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
