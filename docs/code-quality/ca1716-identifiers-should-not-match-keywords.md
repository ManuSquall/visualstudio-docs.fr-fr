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
ms.openlocfilehash: 279bcf3aecc2a637a7a36c2041ed63a72017a800
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545828"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716 : Les identificateurs ne doivent pas correspondre à des mots clés

|||
|-|-|
|TypeName|IdentifiersShouldNotMatchKeywords|
|CheckId|CA1716|
|Category|Microsoft.Naming|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Le nom d’un espace de noms, type, ou virtuel ou membre d’interface correspond à un mot clé réservé dans un langage de programmation.

Par défaut, cette règle examine uniquement les espaces de noms extérieurement visibles, les types et membres, mais il s’agit de [configurable](#configurability).

## <a name="rule-description"></a>Description de la règle

Identificateurs pour les espaces de noms, types et virtuels et les membres d’interface ne doivent pas correspondre aux mots clés définis par les langages qui ciblent le common language runtime. Selon le langage qui est utilisé et le mot clé, ambiguïtés et les erreurs du compilateur peuvent rendre la bibliothèque difficile à utiliser.

Cette règle vérifie par rapport à des mots clés dans les langues suivantes :

- Visual Basic
- C#
- C++/CLI

Comparaison de non-respect de la casse est utilisée pour les mots clés Visual Basic et comparaison respectant la casse est utilisée pour les autres langues.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Sélectionnez un nom qui n’apparaît pas dans la liste des mots clés.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Vous pouvez supprimer un avertissement de cette règle si vous êtes convaincu que l’identificateur ne confondez pas les utilisateurs de l’API, et que la bibliothèque est utilisable dans toutes les langues disponibles dans .NET.

## <a name="configurability"></a>Possibilités de configuration

Si vous exécutez cette règle à partir de [analyseurs FxCop](install-fxcop-analyzers.md) (et non par le biais d’analyse statique du code), vous pouvez configurer les parties de votre codebase pour exécuter cette règle sur, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement par rapport à la surface d’API non publics, ajoutez la paire clé-valeur suivante dans un fichier .editorconfig dans votre projet :

```
dotnet_code_quality.ca1716.api_surface = private, internal
```

Vous pouvez configurer cette option pour simplement cette règle, pour toutes les règles ou pour toutes les règles de cette catégorie (d’affectation de noms). Pour plus d’informations, consultez [analyseurs FxCop configurer](configure-fxcop-analyzers.md).