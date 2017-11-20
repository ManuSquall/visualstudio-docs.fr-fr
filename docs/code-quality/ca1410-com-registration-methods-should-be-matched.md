---
title: "CA1410 : Les méthodes d’inscription COM doivent être mises en correspondance | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
helpviewer_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 65c6191aff1433d050c1f7b50097c88d1d3cf2a0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410 : Les méthodes d'inscription COM doivent être mises en correspondance
|||  
|-|-|  
|TypeName|ComRegistrationMethodsShouldBeMatched|  
|CheckId|CA1410|  
|Catégorie|Microsoft.Interoperability|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Un type déclare une méthode qui est marquée avec la <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> d’attribut, mais ne déclare pas une méthode qui est marquée avec le <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> attribut, ou vice versa.  
  
## <a name="rule-description"></a>Description de la règle  
 Pour les clients du modèle COM (Component Object) créer un [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] type, le type doit d’abord être enregistré. S’il est disponible, une méthode qui est marquée avec le <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> attribut est appelé pendant le processus d’inscription pour exécuter le code spécifié par l’utilisateur. Une méthode correspondante qui est marquée avec la <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> attribut est appelé pendant le processus d’inscription pour inverser les opérations de la méthode d’inscription.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, ajoutez l’inscription ou la méthode de désinscription.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre un type qui enfreint la règle. Le code commenté affiche le correctif de la violation.  
  
 [!code-csharp[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/CSharp/ca1410-com-registration-methods-should-be-matched_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/VisualBasic/ca1410-com-registration-methods-should-be-matched_1.vb)]  
  
## <a name="related-rules"></a>Règles associées  
 [CA1411 : Les méthodes d’inscription COM ne doivent pas être visibles](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>   
 [Inscription d’assemblys dans COM](/dotnet/framework/interop/registering-assemblies-with-com)   
 [Regasm.exe (outil d’inscription d’assemblys)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)