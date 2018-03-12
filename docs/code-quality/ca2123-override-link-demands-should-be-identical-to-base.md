---
title: "CA2123 : Les demandes de liaison de remplacement doivent être identiques au base | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2123
- OverrideLinkDemandsShouldBeIdenticalToBase
helpviewer_keywords:
- OverrideLinkDemandsShouldBeIdenticalToBase
- CA2123
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3181e791d95f0268fd60654e8ceedb8fa394f7a0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2123-override-link-demands-should-be-identical-to-base"></a>CA2123 : Les demandes de liaison de substitution doivent être identiques au composant de base
|||  
|-|-|  
|TypeName|OverrideLinkDemandsShouldBeIdenticalToBase|  
|CheckId|CA2123|  
|Category|Microsoft.Security|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Une méthode publique ou protégée dans un type public substitue une méthode ou implémente une interface et n’a pas la même [les demandes de liaison](/dotnet/framework/misc/link-demands) que l’interface ou la méthode virtuelle.  
  
## <a name="rule-description"></a>Description de la règle  
 Cette règle met en correspondance une méthode et sa méthode de base, qui est soit une interface, soit une méthode virtuelle dans un autre type, puis compare les demandes de liaison sur chacune. Une violation est signalée si la méthode ou la méthode de base a une demande de liaison et l’autre non.  
  
 Si cette règle est violée, un appelant malveillant peut ignorer la demande de liaison simplement en appelant la méthode non protégée.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, appliquez la même demande de liaison à la méthode ou implémentation override. Si ce n’est pas possible, marquez la méthode avec une demande complète ou supprimez l’attribut entièrement.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre différentes violations de cette règle.  
  
 [!code-csharp[FxCop.Security.OverridesAndSecurity#1](../code-quality/codesnippet/CSharp/ca2123-override-link-demands-should-be-identical-to-base_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de codage sécurisé](/dotnet/standard/security/secure-coding-guidelines)   
 [Demandes de liaison](/dotnet/framework/misc/link-demands)