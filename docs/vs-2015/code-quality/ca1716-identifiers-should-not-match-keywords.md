---
title: 'CA1716 : les identificateurs ne doivent pas correspondre à des mots clés | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f81aec5973d1915ba646c20c3b84186443678754
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669098"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716 : Les identificateurs ne doivent pas correspondre à des mots clés
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldNotMatchKeywords|
|CheckId|CA1716|
|Category|Microsoft. Naming|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Le nom d’un espace de noms, d’un type, d’un viritual ou d’un membre d’interface correspond à un mot clé réservé dans un langage de programmation.

## <a name="rule-description"></a>Description de la règle
 Les identificateurs pour les espaces de noms, les types et les membres virtuels et d’interface ne doivent pas correspondre à des mots clés définis par les langages qui ciblent le common language runtime. En fonction du langage utilisé et du mot clé, les erreurs et les ambiguïtés du compilateur peuvent compliquer l’utilisation de la bibliothèque.

 Cette règle vérifie les mots clés dans les langues suivantes :

- Visual Basic

- C#

- C++/CLI

  La comparaison ne respectant pas la casse est utilisée pour les mots clés [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], et la comparaison respectant la casse est utilisée pour les autres langages.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Sélectionnez un nom qui n’apparaît pas dans la liste des mots clés.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Vous pouvez supprimer un avertissement de cette règle si vous êtes convaincu que l’identificateur ne confondra pas les utilisateurs de l’API et que la bibliothèque est utilisable dans toutes les langues disponibles dans le [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].
