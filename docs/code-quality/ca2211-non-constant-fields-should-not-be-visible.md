---
title: 'CA2211 : Les champs non constants ne doivent pas être visibles'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b3c508aaf8632ff7fc064fabb4367044e079fa8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="ca2211-non-constant-fields-should-not-be-visible"></a>CA2211 : Les champs non constants ne doivent pas être visibles
|||
|-|-|
|TypeName|NonConstantFieldsShouldNotBeVisible|
|CheckId|CA2211|
|Category|Microsoft.Usage|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un champ statique public ou protégé n’est pas constant et n’est pas en lecture seule.

## <a name="rule-description"></a>Description de la règle
 Les champs static qui ne sont ni constants ni en lecture seule ne sont pas thread-safe. Accès à un tel champ doit être scrupuleusement contrôlé et requiert des techniques de programmation évoluées pour synchroniser l’accès à l’objet de classe. Étant donné que ces compétences sont difficiles à en savoir plus et principale et le test d’un tel objet pose ses propres défis, champs statiques sont mieux utilisés pour stocker les données qui ne changent pas. Cette règle s’applique aux bibliothèques ; les applications ne doivent pas exposer de tous les champs.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, rendez le champ statique constant ou en lecture seule. Si ce n’est pas possible, modifier le type pour utiliser un autre mécanisme, par exemple une propriété de thread-safe qui gère l’accès thread-safe au champ sous-jacent. Notez que les problèmes de contention de verrouillage et les interblocages peuvent affecter les performances et le comportement de la bibliothèque.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si vous développez une application et par conséquent avoir un contrôle total sur l’accès au type qui contient le champ statique. Les concepteurs de bibliothèque ne devraient pas supprimer un avertissement de cette règle ; les champs statiques non constants permet d’effectuer à l’aide de la bibliothèque difficile pour les développeurs d’utiliser correctement.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type qui viole cette règle.

 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/VisualBasic/ca2211-non-constant-fields-should-not-be-visible_1.vb)]
 [!code-csharp[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/CSharp/ca2211-non-constant-fields-should-not-be-visible_1.cs)]