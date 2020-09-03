---
title: 'CA2117 : les types APTCA doivent uniquement étendre les types de base APTCA | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2117
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
helpviewer_keywords:
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
- CA2117
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 90c1f66f36fc689ee077ec66f154487d65ee13a1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543609"
---
# <a name="ca2117-aptca-types-should-only-extend-aptca-base-types"></a>CA2117 : Les types APTCA doivent uniquement étendre des types de base APTCA
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|
|CheckId|CA2117|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause :
 Un type public ou protégé dans un assembly avec l' <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> attribut hérite d’un type déclaré dans un assembly qui n’a pas l’attribut.

## <a name="rule-description"></a>Description de la règle
 Par défaut, les types publics ou protégés dans les assemblys avec des noms forts sont protégés implicitement par une [demande d’héritage](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) pour une confiance totale. Les assemblys avec nom fort marqués avec l' <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribut (APTCA) n’ont pas cette protection. L’attribut désactive la demande d’héritage. Ainsi, les types exposés déclarés dans l’assembly peuvent être hérités par des types qui n’ont pas une confiance totale.

 Lorsque l’attribut APTCA est présent sur un assembly d’un niveau de confiance totale et qu’un type dans l’assembly hérite d’un type qui n’autorise pas les appelants d’un niveau de confiance partiel, une faille de sécurité est possible. Si deux types `T1` et `T2` remplissent les conditions suivantes, les appelants malveillants peuvent utiliser le type `T1` pour contourner la demande d’héritage de confiance totale implicite qui protège `T2` :

- `T1` est un type public déclaré dans un assembly de confiance totale qui a l’attribut APTCA.

- `T1` hérite d’un type `T2` en dehors de son assembly.

- `T2`l’assembly de n’a pas l’attribut APTCA et, par conséquent, ne peut pas être hérité par les types dans les assemblys partiellement approuvés.

  Un type de confiance partielle `X` peut hériter de `T1` , ce qui lui donne accès aux membres hérités déclarés dans `T2` . Étant donné que `T2` n’a pas l’attribut APTCA, son type dérivé immédiat ( `T1` ) doit répondre à une demande d’héritage pour une confiance totale ; `T1` a une confiance totale et, par conséquent, est conforme à cette vérification. Le risque de sécurité est dû au fait que `X` ne participe pas à la demande d’héritage qui protège `T2` des sous-classes non approuvées. Pour cette raison, les types avec l’attribut APTCA ne doivent pas étendre les types qui n’ont pas l’attribut.

  Un autre problème de sécurité, et peut-être plus courant, est que le type dérivé ( `T1` ) peut, par le biais d’une erreur du programmeur, exposer des membres protégés du type qui requiert une confiance totale ( `T2` ). Lorsque cela se produit, les appelants non fiables accèdent aux informations qui doivent être disponibles uniquement pour les types entièrement fiables.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Si le type signalé par la violation se trouve dans un assembly qui ne requiert pas l’attribut APTCA, supprimez-le.

 Si l’attribut APTCA est requis, ajoutez une demande d’héritage pour un niveau de confiance totale au type. Cela protège contre l’héritage par des types non fiables.

 Il est possible de corriger une violation en ajoutant l’attribut APTCA aux assemblys des types de base signalés par la violation. N’effectuez pas cette opération sans commencer par effectuer un examen intensif de la sécurité de tout le code dans les assemblys et de tout le code qui dépend des assemblys.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Pour supprimer sans risque un avertissement de cette règle, vous devez vous assurer que les membres protégés exposés par votre type n’autorisent pas directement ou indirectement les appelants non approuvés à accéder à des informations, des opérations ou des ressources sensibles qui peuvent être utilisées de manière destructrice.

## <a name="example"></a>Exemple
 L’exemple suivant utilise deux assemblys et une application de test pour illustrer la vulnérabilité de sécurité détectée par cette règle. Le premier assembly n’a pas l’attribut APTCA et ne peut pas être hérité par des types de confiance partielle (représenté par `T2` dans la discussion précédente).

 [!code-csharp[FxCop.Security.NoAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptcaInherit/cs/FxCop.Security.NoAptcaInherit.cs#1)]

## <a name="example"></a>Exemple
 Le deuxième assembly, représenté par `T1` dans la discussion précédente, est entièrement fiable et autorise les appelants d’un niveau de confiance partiel.

 [!code-csharp[FxCop.Security.YesAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptcaInherit/cs/FxCop.Security.YesAptcaInherit.cs#1)]

## <a name="example"></a>Exemple
 Le type de test, représenté par `X` dans la discussion précédente, se trouve dans un assembly de confiance partielle.

 [!code-csharp[FxCop.Security.TestAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaInherit/cs/FxCop.Security.TestAptcaInherit.cs#1)]

 Cet exemple produit la sortie suivante.

 **Rencontrez le Glen d’ombrage 2/22/2003 12:00:00 AM !** 
 **À partir du test : pré** 
 -ensoleillé **Rencontrez le pré-ensoleillé 2/22/2003 12:00:00 AM !**
## <a name="related-rules"></a>Règles associées
 [CA2116 : Les méthodes APTCA doivent uniquement appeler des méthodes APTCA](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)

## <a name="see-also"></a>Voir aussi
 [Instructions de codage sécurisé](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [.NET Framework assemblys pouvant être appelés par du code d’un code d’confiance partiel](https://msdn.microsoft.com/a417fcd4-d3ca-4884-a308-3a1a080eac8d) [à l’aide de bibliothèques de demandes d’héritage de code d’un confiance partielle](https://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74) [Inheritance Demands](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9)
