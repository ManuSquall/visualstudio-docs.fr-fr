---
title: 'CA1801 : Passez en revue les paramètres inutilisés | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0efbec121e08d026145d8762b574847fbd4a2b88
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68143138"
---
# <a name="ca1801-review-unused-parameters"></a>CA1801 : Passez en revue les paramètres inutilisés
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour obtenir la dernière documentation sur Visual Studio, consultez [CA1801 : Passez en revue les paramètres inutilisés](https://docs.microsoft.com/visualstudio/code-quality/ca1801-review-unused-parameters).  
  
|||  
|-|-|  
|TypeName|ReviewUnusedParameters|  
|CheckId|CA1801|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Sans rupture - Si le membre n’est pas visible en dehors de l’assembly, quelle que soit la modification vous apporter.<br /><br /> Sans rupture - Si vous modifiez le membre pour utiliser le paramètre dans son corps.<br /><br /> Avec rupture - Si vous supprimez le paramètre et il est visible en dehors de l’assembly.|  
  
## <a name="cause"></a>Cause  
 Une signature de méthode inclut un paramètre qui n'est pas utilisé dans le corps de la méthode. Cette règle n’examine pas les méthodes suivantes :  
  
- Méthodes référencées par un délégué.  
  
- Méthodes utilisées en tant que gestionnaires d’événements.  
  
- Les méthodes déclarées avec le `abstract` (`MustOverride` en Visual Basic) modificateur.  
  
- Les méthodes déclarées avec le `virtual` (`Overridable` en Visual Basic) modificateur.  
  
- Les méthodes déclarées avec le `override` (`Overrides` en Visual Basic) modificateur.  
  
- Les méthodes déclarées avec le `extern` (`Declare` instruction en Visual Basic) modificateur.  
  
## <a name="rule-description"></a>Description de la règle  
 Passez en revue les paramètres dans les méthodes non virtuelles qui ne sont pas utilisés dans le corps de méthode pour vous assurer n’empêche existe autour d’y accéder. Les paramètres inutilisés impliquent des coûts de maintenance et de performances.  
  
 Parfois, une violation de cette règle peut pointer vers un bogue d’implémentation dans la méthode. Par exemple, le paramètre doit avoir été utilisé dans le corps de méthode. Supprimer les avertissements de cette règle si le paramètre doit se trouver en raison de la compatibilité descendante.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, supprimez le paramètre inutilisé (une modification avec rupture) ou utilisez le paramètre dans le corps de méthode (une modification sans rupture).  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Il est possible de supprimer un avertissement de cette règle d’un code précédemment livré pour lequel le correctif constituerait une modification avec rupture.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre deux méthodes. Une méthode viole la règle et l’autre méthode satisfait la règle.  
  
 [!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ReviewUnusedParameters/cs/FxCop.Usage.ReviewUnusedPerameters.cs#1)]  
  
## <a name="related-rules"></a>Règles associées  
 [CA1811 : Évitez le recours à code privé non appelé](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812 : Évitez les classes internes non instanciées](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1804 : Supprimez les variables locales inutilisées](../code-quality/ca1804-remove-unused-locals.md)
