---
title: 'CA1501 : éviter l’héritage excessif | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1501
- AvoidExcessiveInheritance
helpviewer_keywords:
- AvoidExcessiveInheritance
- CA1501
ms.assetid: 9e934746-1a4d-492a-91e4-085201abafa4
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: cf797ad67b7df2eb1f3ba1246e965ed6ebbd586d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547860"
---
# <a name="ca1501-avoid-excessive-inheritance"></a>CA1501 : Éviter l'excès d'héritage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|AvoidExcessiveInheritance|
|CheckId|CA1501|
|Category|Microsoft. maintenabilité|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type est imbriqué de plus de quatre niveaux dans sa hiérarchie d'héritage.

## <a name="rule-description"></a>Description de la règle
 Les hiérarchies de type profondément imbriquées peuvent être difficiles à suivre, comprendre et gérer. Cette règle limite l’analyse aux hiérarchies du même module.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, dérivez le type d’un type de base qui est moins profond dans la hiérarchie d’héritage ou éliminez certains des types de base intermédiaires.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle. Toutefois, le code peut être plus difficile à gérer. Notez que, selon la visibilité des types de base, la résolution des violations de cette règle peut entraîner des modifications avec rupture. Par exemple, la suppression de types de base publics est une modification avec rupture.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type qui viole la règle.

 [!code-csharp[FxCop.Maintainability.ExcessiveInheritance#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.ExcessiveInheritance/cs/FxCop.Maintainability.ExcessiveInheritance.cs#1)]
 [!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.ExcessiveInheritance/vb/FxCop.Maintainability.ExcessiveInheritance.vb#1)]
