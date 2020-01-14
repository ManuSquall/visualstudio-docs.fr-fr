---
title: 'CA1801 : passez en revue les paramètres inutilisés | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUnusedParameters
- CA1801
- ReviewUnusedParameters
helpviewer_keywords:
- CA1801
- ReviewUnusedParameters
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0f5789b514d645fc670acf9307e4714c160c3b4c
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918171"
---
# <a name="ca1801-review-unused-parameters"></a>CA1801 : Passez en revue les paramètres inutilisés
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour obtenir la documentation la plus récente sur Visual Studio, consultez [CA1801 : examiner les paramètres inutilisés](/visualstudio/code-quality/ca1801-review-unused-parameters).

|||
|-|-|
|TypeName|ReviewUnusedParameters|
|CheckId|CA1801|
|Catégorie|Microsoft.Usage|
|Modification avec rupture|Sans rupture : si le membre n’est pas visible à l’extérieur de l’assembly, quelle que soit la modification que vous apportez.<br /><br /> Sans rupture : Si vous modifiez le membre pour utiliser le paramètre dans son corps.<br /><br /> Avec rupture : Si vous supprimez le paramètre et qu’il est visible à l’extérieur de l’assembly.|

## <a name="cause"></a>Cause
 Une signature de méthode inclut un paramètre qui n'est pas utilisé dans le corps de la méthode. Cette règle n’examine pas les méthodes suivantes :

- Méthodes référencées par un délégué.

- Méthodes utilisées comme gestionnaires d’événements.

- Les méthodes déclarées avec le modificateur `abstract` (`MustOverride` dans Visual Basic).

- Les méthodes déclarées avec le modificateur `virtual` (`Overridable` dans Visual Basic).

- Les méthodes déclarées avec le modificateur `override` (`Overrides` dans Visual Basic).

- Les méthodes déclarées avec le modificateur `extern` (`Declare` instruction Visual Basic).

## <a name="rule-description"></a>Description de la règle
 Passez en revue les paramètres des méthodes non virtuelles qui ne sont pas utilisées dans le corps de la méthode pour vous assurer qu’il n’existe pas d’exactitude pour l’accès à ces derniers. Les paramètres inutilisés entraînent des coûts de maintenance et de performances.

 Parfois, une violation de cette règle peut pointer vers un bogue d’implémentation dans la méthode. Par exemple, le paramètre doit avoir été utilisé dans le corps de la méthode. Supprimez les avertissements de cette règle si le paramètre doit exister en raison d’une compatibilité descendante.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, supprimez le paramètre inutilisé (une modification avec rupture) ou utilisez le paramètre dans le corps de la méthode (modification sans rupture).

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle pour le code précédemment expédié pour lequel le correctif serait une modification avec rupture.

## <a name="example"></a>Exemple
 L’exemple suivant illustre deux méthodes. Une méthode viole la règle et l’autre méthode remplit la règle.

 [!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ReviewUnusedParameters/cs/FxCop.Usage.ReviewUnusedPerameters.cs#1)]

## <a name="related-rules"></a>Règles associées
 [CA1811 : Évitez le recours à du code privé non appelé](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812 : Évitez les classes internes non instanciées](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804 : Supprimez les variables locales inutilisées](../code-quality/ca1804-remove-unused-locals.md)
