---
title: 'CA2118 : passez en revue l’utilisation de SuppressUnmanagedCodeSecurityAttribute | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: bb7404d9add159f182ae44b22444dded1aafca20
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658643"
---
# <a name="ca2118-review-suppressunmanagedcodesecurityattribute-usage"></a>CA2118 : Revue de l’utilisation de SuppressUnmanagedCodeSecurityAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|
|CheckId|CA2118|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type ou un membre public ou protégé a l’attribut <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Description de la règle
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> modifie le comportement par défaut du système de sécurité pour les membres qui exécutent du code non managé à l’aide d’COM Interop ou d’un appel de plateforme. En général, le système crée des [données et une modélisation](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) pour l’autorisation de code non managé. Cette demande se produit au moment de l’exécution pour chaque appel du membre et vérifie si chaque appelant dans la pile des appels a l’autorisation. Lorsque l’attribut est présent, le système effectue une [demande de liaison](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) pour l’autorisation : les autorisations de l’appelant immédiat sont vérifiées lorsque l’appelant est compilé juste-à-temps.

 Cet attribut est essentiellement utilisé pour accroître les performances ; toutefois, les gains de performance s’accompagnent de risques substantiels pour la sécurité. Si vous placez l’attribut sur des membres publics qui appellent des méthodes natives, les appelants dans la pile des appels (à l’exception de l’appelant immédiat) n’ont pas besoin de l’autorisation de code non managé pour exécuter du code non managé. En fonction des actions du membre public et de la gestion des entrées, il peut permettre aux appelants non fiables d’accéder aux fonctionnalités normalement limitées au code fiable.

 Le [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] s’appuie sur des vérifications de sécurité pour empêcher les appelants d’obtenir un accès direct à l’espace d’adressage du processus actuel. Étant donné que cet attribut ignore la sécurité normale, votre code pose une menace sérieuse s’il peut être utilisé pour lire ou écrire dans la mémoire du processus. Notez que le risque n’est pas limité aux méthodes qui fournissent intentionnellement un accès à la mémoire de processus ; Il est également présent dans tout scénario où du code malveillant peut atteindre un accès par n’importe quel moyen, par exemple en fournissant une entrée étonnante, mal formée ou non valide.

 La stratégie de sécurité par défaut n’accorde pas d’autorisation de code non managé à un assembly, sauf s’il s’exécute à partir de l’ordinateur local ou s’il est membre de l’un des groupes suivants :

- Groupe de codes de zone Poste de travail

- Groupe de codes Microsoft Strong Name

- Groupe de codes du nom fort ECMA

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Examinez attentivement votre code pour vous assurer que cet attribut est absolument nécessaire. Si vous n’êtes pas familiarisé avec la sécurité du code managé, ou si vous ne comprenez pas les implications en matière de sécurité de l’utilisation de cet attribut, supprimez-le de votre code. Si l’attribut est requis, vous devez vous assurer que les appelants ne peuvent pas utiliser votre code de manière malveillante. Si votre code n’est pas autorisé à exécuter du code non managé, cet attribut n’a aucun effet et doit être supprimé.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Pour supprimer sans risque un avertissement de cette règle, vous devez vous assurer que votre code ne permet pas aux appelants d’accéder aux opérations natives ou aux ressources qui peuvent être utilisées de manière destructrice.

## <a name="example"></a>Exemple
 L’exemple suivant enfreint la règle.

 [!code-csharp[FxCop.Security.TypesDoNotSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypesDoNotSuppress/cs/FxCop.Security.TypesDoNotSuppress.cs#1)]

## <a name="example"></a>Exemple
 Dans l’exemple suivant, la méthode `DoWork` fournit un chemin de code accessible publiquement à la méthode d’appel de la plateforme `FormatHardDisk`.

 [!code-csharp[FxCop.Security.PInvokeAndSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PInvokeAndSuppress/cs/FxCop.Security.PInvokeAndSuppress.cs#1)]

## <a name="example"></a>Exemple
 Dans l’exemple suivant, la méthode publique `DoDangerousThing` provoque une violation. Pour résoudre la violation, `DoDangerousThing` doit être rendu privé, et l’accès à celui-ci doit être effectué par le biais d’une méthode publique sécurisée par une demande de sécurité, comme l’illustre la méthode `DoWork`.

 [!code-csharp[FxCop.Security.TypeInvokeAndSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypeInvokeAndSuppress/cs/FxCop.Security.TypeInvokeAndSuppress.cs#1)]

## <a name="see-also"></a>Voir aussi
 [instructions de codage sécurisé <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> les](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) demandes de [liaison](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [de données et de modélisation de](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) [sécurité](https://msdn.microsoft.com/cf255069-d85d-4de3-914a-e4625215a7c0)
