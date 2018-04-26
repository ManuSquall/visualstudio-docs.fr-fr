---
title: 'CA1053 : Les types de conteneurs statiques ne doivent pas comporter de constructeur'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d7f99804abeac1c9f536c94c542f6e031bf16ec6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="ca1053-static-holder-types-should-not-have-constructors"></a>CA1053 : Les types de conteneurs statiques ne doivent pas comporter de constructeur
|||
|-|-|
|TypeName|StaticHolderTypesShouldNotHaveConstructors|
|CheckId|CA1053|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type public ou imbriqué déclare uniquement des membres statiques et dispose d'un constructeur par défaut public ou protégé.

## <a name="rule-description"></a>Description de la règle
 Le constructeur est inutile car l'appel à des membres statiques ne requiert aucune instance du type. En outre, étant donné que le type n’a pas de membres non statiques, création d’une instance ne donne pas accès à un des membres du type.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, supprimez le constructeur par défaut ou rendez-le privé.

> [!NOTE]
>  Certains compilateurs créent automatiquement un constructeur public par défaut si le type ne définit pas de constructeur. Si c’est le cas avec le type, ajoutez un constructeur par défaut privé pour éliminer la violation.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle. La présence du constructeur suggère que le type n’est pas un type static.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type qui viole cette règle. Notez qu’il n’y a aucun constructeur par défaut dans le code source. Lorsque ce code est compilé dans un assembly, le compilateur c# insérera un constructeur par défaut, ce qui enfreint cette règle. Pour corriger cela, déclarez un constructeur privé.

 [!code-csharp[FxCop.Design.StaticTypes#1](../code-quality/codesnippet/CSharp/ca1053-static-holder-types-should-not-have-constructors_1.cs)]