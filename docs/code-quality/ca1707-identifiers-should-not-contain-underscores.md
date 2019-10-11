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
ms.openlocfilehash: 5ba9e8dda927edca08565b088cbde90d63443908
ms.sourcegitcommit: 3e94d9fb6dc56fa8b23fbacd5d11cf8d6e7e18f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72252575"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707 : Les identificateurs ne doivent pas contenir de traits de soulignement

|||
|-|-|
|TypeName|IdentifiersShouldNotContainUnderscores|
|CheckId|CA1707|
|Catégorie|Microsoft.Naming|
|Modification avec rupture|Avec rupture-en cas de déclenchement sur les assemblys<br /><br /> Sans rupture-en cas de déclenchement sur les paramètres de type|

## <a name="cause"></a>Cause

Le nom d’un identificateur contient le caractère de soulignement (\_).

## <a name="rule-description"></a>Description de la règle

Par Convention, les noms d’identificateur ne contiennent pas le caractère de soulignement (\_). La règle vérifie les espaces de noms, les types, les membres et les paramètres.

Les conventions d’affectation de noms fournissent une apparence commune pour les bibliothèques qui ciblent le common language runtime. Cela réduit la courbe d’apprentissage requise pour les nouvelles bibliothèques logicielles et augmente la confiance des clients dans la mesure où la bibliothèque a été développée par une personne ayant une expertise dans le développement de code géré.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Supprimez tous les traits de soulignement du nom.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez pas les avertissements pour le code de production. Toutefois, il est possible de supprimer cet avertissement en toute sécurité pour le code de test. Vous pouvez supprimer les avertissements de cette règle en affectant la valeur **aucun**à sa [gravité](use-roslyn-analyzers.md#rule-severity) . 

## <a name="related-rules"></a>Règles associées

- @NO__T 0CA1709 : La casse des identificateurs doit être correcte @ no__t-0
- @NO__T 0CA1708 : Les identificateurs doivent différer par plus que la casse @ no__t-0
