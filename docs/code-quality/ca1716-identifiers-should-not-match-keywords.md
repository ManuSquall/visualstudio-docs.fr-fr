---
title: 'CA1716 : Les identificateurs ne doivent pas correspondre à des mots clés'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: e1ecd5fc5163bfcb5a0f217e21b5aab353a074a7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54972938"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716 : Les identificateurs ne doivent pas correspondre à des mots clés

|||
|-|-|
|TypeName|IdentifiersShouldNotMatchKeywords|
|CheckId|CA1716|
|Category|Microsoft.Naming|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Un nom d’un espace de noms, un type ou un membre d’interface ou virtuel correspond à un mot clé réservé dans un langage de programmation.

## <a name="rule-description"></a>Description de la règle

Identificateurs pour les espaces de noms, types et virtuels et les membres d’interface ne doivent pas correspondre aux mots clés définis par les langages qui ciblent le common language runtime. Selon le langage qui est utilisé et le mot clé, ambiguïtés et les erreurs du compilateur peuvent rendre la bibliothèque difficile à utiliser.

Cette règle vérifie par rapport à des mots clés dans les langues suivantes :

- Visual Basic

- C#

- C++/CLI

Comparaison de non-respect de la casse est utilisée pour [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] mots clés et comparaison respectant la casse est utilisée pour les autres langues.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Sélectionnez un nom qui n’apparaît pas dans la liste des mots clés.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Vous pouvez supprimer un avertissement de cette règle si vous êtes convaincu que l’identificateur sera confondez pas les utilisateurs de l’API, et que la bibliothèque est utilisable dans toutes les langues disponibles dans le .NET Framework.