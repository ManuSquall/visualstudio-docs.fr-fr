---
title: 'CA1702 : La casse des mots composés doit être correcte'
ms.date: 03/28/2018
ms.topic: reference
f1_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f78ea4f44c48d2740df58def03a6335bce6637a2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545930"
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702 : La casse des mots composés doit être correcte

|||
|-|-|
|TypeName|CompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1702|
|Category|Microsoft.Naming|
|Modification avec rupture|Avec rupture-lorsque déclenchée sur les assemblys.<br /><br /> Sans rupture - lorsque déclenchée sur les paramètres de type.|

## <a name="cause"></a>Cause

Le nom d'un identificateur contient plusieurs mots et au moins l'un des mots semble être un mot composé qui ne présente pas une casse correcte.

## <a name="rule-description"></a>Description de la règle

Le nom de l’identificateur est fractionné en mots qui sont basées sur la casse. Chaque combinaison de deux mots contiguë est vérifiée par la bibliothèque de vérificateur d’orthographe Microsoft. S’il est reconnu, l’identificateur de produit une violation de la règle. Exemples de mots composés qui enfreint sont « CheckSum » et « MultiPart », la casse doit être en tant que « Checksum » et « Multipart », respectivement. En raison d’une utilisation commune précédente, plusieurs exceptions sont intégrées dans la règle et plusieurs mots entiers sont signalés, telles que « Toolbar » et « Filename », qui doit être celle de deux mots distincts (dans ce cas, « Barre d’outils » et « FileName »).

Les conventions d’affectation de noms fournissent une apparence commune pour les bibliothèques qui ciblent le common language runtime. Cela réduit la courbe d’apprentissage qui est requis pour les nouvelles bibliothèques de logiciels et confirment au client que la bibliothèque a été développée par une personne compétente en matière de développement de code managé.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Modifiez le nom afin qu’elle est correcte.

## <a name="language"></a>Langue

Actuellement, le vérificateur d’orthographe vérifie uniquement à des dictionnaires de culture en anglais. Vous pouvez modifier la culture de votre projet dans le fichier projet, en ajoutant le **CodeAnalysisCulture** élément.

Exemple :

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> Si vous définissez la culture sur autre chose qu’une culture en anglais, cette règle d’analyse du code est désactivée en mode silencieux.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer un avertissement de cette règle si les deux parties du mot composé sont reconnues par le dictionnaire d’orthographe, et l’objectif consiste à utiliser deux mots.

## <a name="related-rules"></a>Règles associées

- [CA1701 : Mots composés de chaînes de ressources doivent être correcte](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1709 : Identificateurs doivent être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708 : Les identificateurs doivent différer par leur casse](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Voir aussi

- [Directives de nommage](/dotnet/standard/design-guidelines/naming-guidelines)
- [Conventions de mise en majuscules](/dotnet/standard/design-guidelines/capitalization-conventions)