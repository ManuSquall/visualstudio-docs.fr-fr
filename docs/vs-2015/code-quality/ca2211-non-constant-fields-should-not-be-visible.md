---
title: 'CA2211 : Les champs non constants ne doivent pas être visibles | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2211
- NonConstantFieldsShouldNotBeVisible
helpviewer_keywords:
- NonConstantFieldsShouldNotBeVisible
- CA2211
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 48d1a449301c422aa457346d1eb3d48d2f395f2a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58951331"
---
# <a name="ca2211-non-constant-fields-should-not-be-visible"></a>CA2211 : Les champs non constants ne doivent pas être visibles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

 [!code-csharp[FxCop.Usage.AvoidStaticNonConstants#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.AvoidStaticNonConstants/cs/FxCop.Usage.AvoidStaticNonConstants.cs#1)]
 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.AvoidStaticNonConstants/vb/FxCop.Usage.AvoidStaticNonConstants.vb#1)]
