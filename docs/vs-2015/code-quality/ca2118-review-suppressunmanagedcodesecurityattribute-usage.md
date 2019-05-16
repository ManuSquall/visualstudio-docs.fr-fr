---
title: 'CA2118 : Passez en revue l’utilisation de SuppressUnmanagedCodeSecurityAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2118
- ReviewSuppressUnmanagedCodeSecurityUsage
helpviewer_keywords:
- ReviewSuppressUnmanagedCodeSecurityUsage
- CA2118
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4fdbf84cc981dfe9e7cee73fba06867250d2fc33
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687284"
---
# <a name="ca2118-review-suppressunmanagedcodesecurityattribute-usage"></a>CA2118 : Vérifier l'utilisation de SuppressUnmanagedCodeSecurityAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|
|CheckId|CA2118|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type public ou protégé ou un membre a le <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> attribut.

## <a name="rule-description"></a>Description de la règle
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> modifie le comportement par défaut du système de sécurité pour les membres qui exécutent du code non managé à l’aide de COM interop ou plateforme de l’appel. En général, le système effectue une [données et modélisation](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) pour l’autorisation de code non managé. Cette demande se produit au moment de l’exécution pour chaque appel du membre et vérifie chaque appelant dans la pile des appels pour l’autorisation. Lorsque l’attribut est présent, le système effectue une [demandes de liaison](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) pour l’autorisation : les autorisations de l’appelant immédiat sont vérifiées lorsque l’appelant est compilé par JIT.

 Cet attribut est essentiellement utilisé pour accroître les performances ; toutefois, les gains de performance s’accompagnent de risques substantiels pour la sécurité. Si vous placez l’attribut sur des membres publics qui appellent des méthodes natives, les appelants de la pile des appels (autre que l’appelant immédiat) n’avez pas besoin d’autorisation de code non managé pour exécuter du code non managé. En fonction de gestion des entrées et actions du membre public, il peut autoriser des appelants non fiables pour accéder aux fonctionnalités normalement restreintes à du code fiable.

 Le [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] s’appuie sur les vérifications de sécurité pour empêcher des appelants d’obtenir un accès direct à l’espace d’adressage du processus actuel. Étant donné que cet attribut contourne la sécurité normale, votre code constitue une menace sérieuse s’il peut être utilisé pour lire ou écrire dans la mémoire du processus. Notez que le risque n’est pas limité aux méthodes qui conçus pour fournir des accès pour traiter la mémoire ; Il est également présent dans tout scénario où un code malveillant peut obtenir un accès par tout moyen, par exemple, en fournissant l’entrée surprenante, incorrecte ou non valide.

 La stratégie de sécurité par défaut n’accorde pas l’autorisation de code non managé à un assembly, sauf si elle s’exécute à partir de l’ordinateur local, soit un membre d’un des groupes suivants :

- Mon groupe de codes de Zone ordinateur

- Groupe de codes de nom fort Microsoft

- Groupe de codes de nom fort ECMA

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Examinez soigneusement votre code pour vous assurer que cet attribut est absolument nécessaire. Si vous n’êtes pas familiarisé avec la sécurité du code managé, ou que vous ne comprenez pas les implications de sécurité de l’utilisation de cet attribut, supprimez-le de votre code. Si l’attribut est requis, vous devez vous assurer que les appelants ne peuvent pas utiliser votre code à des fins malveillantes. Si votre code n’a pas l’autorisation d’exécution de code non managé, cet attribut n’a aucun effet et doit être supprimé.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Pour supprimer sans risque un avertissement de cette règle, vous devez vous assurer que votre code ne fournit pas les appelants accès aux opérations natives ou les ressources qui peuvent être utilisées dans une action destructrice.

## <a name="example"></a>Exemple
 L’exemple suivant enfreint la règle.

 [!code-csharp[FxCop.Security.TypesDoNotSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypesDoNotSuppress/cs/FxCop.Security.TypesDoNotSuppress.cs#1)]

## <a name="example"></a>Exemple
 Dans l’exemple suivant, le `DoWork` méthode fournit un chemin d’accès de code publiquement accessible à la méthode d’appel de plateforme `FormatHardDisk`.

 [!code-csharp[FxCop.Security.PInvokeAndSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PInvokeAndSuppress/cs/FxCop.Security.PInvokeAndSuppress.cs#1)]

## <a name="example"></a>Exemple
 Dans l’exemple suivant, la méthode publique `DoDangerousThing` entraîne une violation. Pour résoudre la violation, `DoDangerousThing` doit être rendu privé et l’accès à ce dernier doit se faire par une méthode publique sécurisée par une demande de sécurité, comme illustré par la `DoWork` (méthode).

 [!code-csharp[FxCop.Security.TypeInvokeAndSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypeInvokeAndSuppress/cs/FxCop.Security.TypeInvokeAndSuppress.cs#1)]

## <a name="see-also"></a>Voir aussi
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> [Instructions de codage sécurisé](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [optimisations de la sécurité](https://msdn.microsoft.com/cf255069-d85d-4de3-914a-e4625215a7c0) [données et modélisation](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) [demandes de liaison](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)
