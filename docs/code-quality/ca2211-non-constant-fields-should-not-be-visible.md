---
title: 'CA2211 : Les champs non constants ne doivent pas être visibles'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2211
- NonConstantFieldsShouldNotBeVisible
helpviewer_keywords:
- NonConstantFieldsShouldNotBeVisible
- CA2211
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c33db7e5237b8e31011689edb725c8ae0e905522
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806771"
---
# <a name="ca2211-non-constant-fields-should-not-be-visible"></a>CA2211 : Les champs non constants ne doivent pas être visibles

|||
|-|-|
|TypeName|NonConstantFieldsShouldNotBeVisible|
|CheckId|CA2211|
|Category|Microsoft.Usage|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un champ statique public ou protégé n’est pas constante ni en lecture seule.

## <a name="rule-description"></a>Description de la règle
 Les champs statiques qui ne sont ni constants ni en lecture seule ne sont pas thread-safe. Accès à un tel champ doit être scrupuleusement contrôlé et nécessite des techniques de programmation évoluées pour synchroniser l’accès à l’objet de classe. Étant donné que ces compétences sont difficiles à apprendre et master et le test d’un tel objet pose ses propres difficultés, champs statiques sont mieux utilisés pour stocker les données qui ne changent pas. Cette règle s’applique aux bibliothèques ; les applications ne doivent pas exposer tous les champs.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, rendez le champ statique constant ou en lecture seule. Si ce n’est pas possible, reconcevoir le type pour utiliser un autre mécanisme, par exemple une propriété de thread-safe qui gère l’accès thread-safe pour le champ sous-jacent. Notez que les problèmes tels que des conflits de verrous et blocages peuvent affecter les performances et le comportement de la bibliothèque.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si vous développez une application et par conséquent avoir un contrôle total sur l’accès au type qui contient le champ statique. Les concepteurs de bibliothèques ne devraient pas supprimer un avertissement de cette règle ; à l’aide des champs statiques non constants peut rendre à l’aide de la bibliothèque difficile pour les développeurs d’utiliser correctement.

## <a name="example"></a>Exemple
 L’exemple suivant illustre un type qui enfreint cette règle.

 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/VisualBasic/ca2211-non-constant-fields-should-not-be-visible_1.vb)]
 [!code-csharp[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/CSharp/ca2211-non-constant-fields-should-not-be-visible_1.cs)]