---
title: 'CA1716 : Les identificateurs ne doivent pas correspondre à des mots clés'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9a51ac9509cf891c05166d46e4b72b862c0dc723
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547082"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716 : Les identificateurs ne doivent pas correspondre à des mots clés

|||
|-|-|
|TypeName|IdentifiersShouldNotMatchKeywords|
|CheckId|CA1716|
|Catégorie|Microsoft.Naming|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Le nom d’un espace de noms, d’un type ou d’un membre virtuel ou d’interface correspond à un mot clé réservé dans un langage de programmation.

Par défaut, cette règle recherche uniquement les espaces de noms, les types et les membres visibles de l’extérieur, mais elle peut [être configurée](#configurability).

## <a name="rule-description"></a>Description de la règle

Les identificateurs pour les espaces de noms, les types et les membres virtuels et d’interface ne doivent pas correspondre à des mots clés définis par les langages qui ciblent le common language runtime. En fonction du langage utilisé et du mot clé, les erreurs et les ambiguïtés du compilateur peuvent compliquer l’utilisation de la bibliothèque.

Cette règle vérifie les mots clés dans les langues suivantes:

- Visual Basic
- C#
- C++/CLI

La comparaison ne respectant pas la casse est utilisée pour les mots clés Visual Basic, et la comparaison respectant la casse est utilisée pour les autres langages.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Sélectionnez un nom qui n’apparaît pas dans la liste des mots clés.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Vous pouvez supprimer un avertissement de cette règle si vous êtes convaincu que l’identificateur ne confondra pas les utilisateurs de l’API et que la bibliothèque est utilisable dans toutes les langues disponibles dans .NET.

## <a name="configurability"></a>Configurabilité

Si vous exécutez cette règle à partir d' [analyseurs FxCop](install-fxcop-analyzers.md) (et non avec l’analyse héritée), vous pouvez configurer les parties de votre code base sur lesquelles exécuter cette règle, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement sur la surface d’API non publique, ajoutez la paire clé-valeur suivante à un fichier. editorconfig dans votre projet:

```ini
dotnet_code_quality.ca1716.api_surface = private, internal
```

Vous pouvez configurer cette option uniquement pour cette règle, pour toutes les règles ou pour toutes les règles de cette catégorie (affectation de noms). Pour plus d’informations, consultez [configurer les analyseurs FxCop](configure-fxcop-analyzers.md).