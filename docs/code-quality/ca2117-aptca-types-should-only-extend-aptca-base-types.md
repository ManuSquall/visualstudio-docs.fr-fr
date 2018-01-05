---
title: "CA2117 : Les types APTCA doivent uniquement étendre des types de base APTCA | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2117
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
helpviewer_keywords:
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
- CA2117
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: be208c156e8710b6aa6b2821a5a85131f3c2e4b2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2117-aptca-types-should-only-extend-aptca-base-types"></a>CA2117 : Les types APTCA doivent uniquement étendre des types de base APTCA
|||  
|-|-|  
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|  
|CheckId|CA2117|  
|Category|Microsoft.Security|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Un type public ou protégé dans un assembly avec le <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> attribut hérite d’un type déclaré dans un assembly qui n’a pas l’attribut.  
  
## <a name="rule-description"></a>Description de la règle  
 Par défaut, les types publics ou protégés dans les assemblys avec noms forts sont implicitement protégés par un <xref:System.Security.Permissions.SecurityAction.InheritanceDemand> pour la confiance totale. Assemblys avec nom fort est marqué avec le <xref:System.Security.AllowPartiallyTrustedCallersAttribute> de l’attribut (APTCA) n’ont pas cette protection. L’attribut désactive la demande d’héritage. Cela rend les types exposés déclarés dans l’assembly pouvant être héritées par les types qui n’ont pas de confiance totale.  
  
 Lorsque l’attribut APTCA est présent sur un assembly entièrement fiable, et un type dans l’assembly hérite d’un type qui n’autorise pas les appelants partiellement approuvés, une attaque de sécurité est possible. Si deux types `T1` et `T2` remplissent les conditions suivantes, des appelants malveillants peuvent utiliser le type `T1` pour ignorer la demande d’héritage de confiance totale implicite qui protège `T2`:  
  
-   `T1`un type public est déclaré dans un assembly entièrement fiable qui possède l’attribut APTCA.  
  
-   `T1`hérite d’un type `T2` en dehors de son assembly.  
  
-   `T2`d’assembly n’a pas l’attribut APTCA et, doit donc pas être héritée par les types dans les assemblys de confiance partiel.  
  
 Un type de niveau de confiance partiel `X` peut hériter que de `T1`, ce qui donne accès aux membres hérités déclarés dans `T2`. Étant donné que `T2` n’a pas l’attribut APTCA, son type dérivé immédiat (`T1`) doit satisfaire une demande d’héritage pour la confiance totale ; `T1` dispose d’une confiance totale et par conséquent satisfait cette vérification. Le risque de sécurité est car `X` ne participe pas satisfaire la demande d’héritage qui protège `T2` de sous-classement non approuvé. Pour cette raison, les types avec l’attribut APTCA ne doivent pas étendre les types qui n’ont pas l’attribut.  
  
 Un autre problème de sécurité et éventuellement une plus courant, qui est le type dérivé (`T1`) peut, par erreur du programmeur, exposer des membres protégés du type qui requiert une confiance totale (`T2`). Lorsque cela se produit, les appelants non approuvés ont accès aux informations qui doivent être disponibles uniquement pour les types de niveau de confiance totale.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Si le type indiqué par la violation est dans un assembly qui ne requiert pas l’attribut APTCA, supprimez-le.  
  
 Si l’attribut APTCA est requis, ajoutez une demande d’héritage pour la confiance totale pour le type. Cela protège contre l’héritage par les types non approuvés.  
  
 Il est possible de corriger une violation en ajoutant l’attribut APTCA aux assemblys des types de base rapportés par celle-ci. Ne procédez pas ainsi sans procède à une révision de sécurité de tout le code dans les assemblys et tout code qui dépend d’assemblys.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Pour supprimer sans risque un avertissement de cette règle, vous devez vous assurer que les membres protégés exposés par votre type n’autorisent pas, directement ou indirectement, à des appelants non approuvés à accéder à des informations sensibles, des opérations ou des ressources qui peuvent être utilisées dans une action destructrice.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise deux assemblys et une application de test pour illustrer la vulnérabilité de sécurité détectée par cette règle. Le premier assembly ne dispose pas de l’attribut APTCA et ne doit pas être hérité par les types de niveau de confiance partiel (représenté par `T2` dans la discussion précédente).  
  
 [!code-csharp[FxCop.Security.NoAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_1.cs)]  
  
## <a name="example"></a>Exemple  
 Le second assembly, représenté par `T1` dans la discussion précédente, est le niveau de confiance totale et autorise les appelants partiellement approuvés.  
  
 [!code-csharp[FxCop.Security.YesAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_2.cs)]  
  
## <a name="example"></a>Exemple  
 Le type de test, représenté par `X` dans la discussion précédente, est dans un assembly partiellement approuvé.  
  
 [!code-csharp[FxCop.Security.TestAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_3.cs)]  
  
 Cet exemple produit la sortie suivante.  
  
 **Satisfait à l’état glen 2/22/2003 12:00:00 AM !**  
**À partir de Test : Ensoleillé pré**  
**Satisfait à la pré ensoleillé 2/22/2003 12:00:00 AM !**   
## <a name="related-rules"></a>Règles associées  
 [CA2116 : Les méthodes APTCA doivent appeler seulement des méthodes APTCA](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de codage sécurisé](/dotnet/standard/security/secure-coding-guidelines)   
 [L’utilisation de bibliothèques à partir du Code partiellement fiable](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)   
