---
title: "CA2118 : Utilisation de SuppressUnmanagedCodeSecurityAttribute de révision | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2118
- ReviewSuppressUnmanagedCodeSecurityUsage
helpviewer_keywords:
- ReviewSuppressUnmanagedCodeSecurityUsage
- CA2118
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6a6c5e60ed84a79e6e81d4cd066d75b1270bdb71
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2118-review-suppressunmanagedcodesecurityattribute-usage"></a>CA2118 : Revue de l’utilisation de SuppressUnmanagedCodeSecurityAttribute
|||  
|-|-|  
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|  
|CheckId|CA2118|  
|Category|Microsoft.Security|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Un type public ou protégé ou un membre a le <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> attribut.  
  
## <a name="rule-description"></a>Description de la règle  
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>modifie le comportement par défaut du système de sécurité pour les membres qui s’exécutent à l’aide de COM interop ou plateforme de l’appel de code non managé. En général, le système effectue un [données et modélisation](/dotnet/framework/data/index) pour l’autorisation de code non managé. Cette demande se produit au moment de l’exécution pour chaque appel du membre et vérifie chaque appelant dans la pile des appels pour autorisation. Lorsque l’attribut est présent, le système effectue un [les demandes de liaison](/dotnet/framework/misc/link-demands) pour l’autorisation : les autorisations de l’appelant immédiat sont vérifiées lorsque l’appelant est compilé par JIT.  
  
 Cet attribut est essentiellement utilisé pour accroître les performances ; toutefois, les gains de performance s’accompagnent de risques substantiels pour la sécurité. Si vous placez l’attribut sur des membres publics qui appellent des méthodes natives, les appelants dans la pile des appels (autre que l’appelant immédiat) est inutile des autorisations de code non managé pour exécuter du code non managé. En fonction de gestion de l’entrée et actions du membre public, pourrait permettre à des appelants non fiables pour accéder aux fonctionnalités normalement restreintes à du code fiable.  
  
 Le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] s’appuie sur les vérifications de sécurité pour empêcher des appelants d’obtenir un accès direct à l’espace d’adressage du processus actuel. Étant donné que cet attribut contourne la sécurité normale, votre code constitue une menace grave s’il peut être utilisé pour lire ou écrire dans la mémoire du processus. Notez que le risque n’est pas limité à méthodes qui fournissent l’accès au processus mémoire ; intentionnellement Il est également présent dans tout scénario où code nuisible peut atteindre l’accès par quelque moyen que, par exemple, en fournissant l’entrée étonnant, incorrecte ou non valide.  
  
 La stratégie de sécurité par défaut n’accorde pas l’autorisation de code non managé à un assembly, sauf si elle s’exécute à partir de l’ordinateur local, soit un membre d’un des groupes suivants :  
  
-   Mon groupe de codes Zone ordinateur  
  
-   Groupe de codes de nom fort Microsoft  
  
-   Groupe de codes de nom fort ECMA  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Lisez attentivement votre code pour vous assurer que cet attribut est absolument nécessaire. Si vous n’êtes pas familiarisé avec la sécurité du code managé, ou que vous ne comprenez pas les implications de sécurité de l’utilisation de cet attribut, supprimez-le de votre code. Si l’attribut est requis, vous devez vous assurer que les appelants ne peuvent pas utiliser votre code à des fins malveillantes. Si votre code n’a pas l’autorisation d’exécuter du code non managé, cet attribut n’a aucun effet et doit être supprimé.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Pour supprimer sans risque un avertissement de cette règle, vous devez vous assurer que votre code ne fournit pas les appelants accès aux ressources qui peuvent être utilisés dans une action destructrice ou des opérations natives.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant enfreint la règle.  
  
 [!code-csharp[FxCop.Security.TypesDoNotSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_1.cs)]  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, la `DoWork` méthode fournit un chemin d’accès de code publiquement accessible à la méthode d’appel de plateforme `FormatHardDisk`.  
  
 [!code-csharp[FxCop.Security.PInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_2.cs)]  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, la méthode publique `DoDangerousThing` entraîne une violation. Pour corriger la violation, `DoDangerousThing` doit être rendu privée, et l’accès à ce dernier doit être via une méthode publique sécurisée par une demande de sécurité, comme illustré par le `DoWork` (méthode).  
  
 [!code-csharp[FxCop.Security.TypeInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_3.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>   
 [Instructions de codage sécurisé](/dotnet/standard/security/secure-coding-guidelines)   
 [Données et modélisation](/dotnet/framework/data/index)  
 [Demandes de liaison](/dotnet/framework/misc/link-demands)  
  