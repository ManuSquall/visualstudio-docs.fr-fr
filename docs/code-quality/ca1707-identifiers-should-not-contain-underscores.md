---
title: 'CA1707 : Identificateurs ne doivent pas contenir de traits de soulignement'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5c5e514599b655febc7086c21c6b037ebe3619e9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53825109"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707 : Identificateurs ne doivent pas contenir de traits de soulignement

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
