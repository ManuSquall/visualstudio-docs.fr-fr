---
title: 'CA2123 : les demandes de liaison de substitution doivent être identiques à la base | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2123
- OverrideLinkDemandsShouldBeIdenticalToBase
helpviewer_keywords:
- OverrideLinkDemandsShouldBeIdenticalToBase
- CA2123
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: bec8f129c094f94ba3eb4021092c402e8263812b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660254"
---
# <a name="ca2123-override-link-demands-should-be-identical-to-base"></a>CA2123 : Les demandes de liaison de substitution doivent être identiques au composant de base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideLinkDemandsShouldBeIdenticalToBase|
|CheckId|CA2123|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une méthode publique ou protégée dans un type public se substitue à une méthode ou implémente une interface, et n’a pas les mêmes [demandes de liaison](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) que l’interface ou la méthode virtuelle.

## <a name="rule-description"></a>Description de la règle
 Cette règle met en correspondance une méthode et sa méthode de base, qui est soit une interface, soit une méthode virtuelle dans un autre type, puis compare les demandes de liaison sur chacune. Une violation est signalée si la méthode ou la méthode de base a une demande de liaison et que l’autre ne le fait pas.

 Si cette règle est violée, un appelant malveillant peut ignorer la demande de liaison simplement en appelant la méthode non sécurisée.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, appliquez la même demande de liaison à la méthode ou à l’implémentation de l’application. Si ce n’est pas possible, marquez la méthode avec une demande complète ou supprimez complètement l’attribut.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant illustre différentes violations de cette règle.

 [!code-csharp[FxCop.Security.OverridesAndSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.OverridesAndSecurity/cs/FxCop.Security.OverridesAndSecurity.cs#1)]

## <a name="see-also"></a>Voir aussi
 [Instructions de codage sécurisé](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [demandes de liaison](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)
