---
title: "CA2107 : Passez en revue l'utilisation des méthodes Deny et PermitOnly"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2107
- ReviewDenyAndPermitOnlyUsage
helpviewer_keywords:
- ReviewDenyAndPermitOnlyUsage
- CA2107
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c251b9fbf8327369acf20ef6acea0518e2b16913
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55910284"
---
# <a name="ca2107-review-deny-and-permit-only-usage"></a>CA2107 : Passez en revue l'utilisation des méthodes Deny et PermitOnly

|||
|-|-|
|TypeName|ReviewDenyAndPermitOnlyUsage|
|CheckId|CA2107|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une méthode contient une vérification de sécurité qui spécifie l’action de sécurité PermitOnly ou Deny.

## <a name="rule-description"></a>Description de la règle
 Le <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> action de sécurité doit être utilisée uniquement par les utilisateurs qui ont une connaissance avancée de la sécurité .NET Framework. Le code qui utilise ces actions de sécurité doit subir une révision de sécurité.

 Refuser modifie le comportement par défaut de la pile qui se produit en réponse à une demande de sécurité. Il vous permet de spécifier des autorisations qui ne doivent pas être accordées sur la durée de la méthode de refus, indépendamment des autorisations réelles des appelants dans la pile des appels. Si le parcours de pile détecte une méthode sécurisée par Deny, et si l’autorisation demandée est incluse dans les autorisations refusées, le parcours de pile échoue. PermitOnly modifie également le comportement par défaut de la pile. Il permet au code de spécifier uniquement les autorisations qui peuvent être accordées, quelles que soient les autorisations des appelants. Si le parcours de pile détecte une méthode sécurisée par PermitOnly, et si l’autorisation demandée n’est pas incluse dans les autorisations qui sont spécifiées par l’action PermitOnly, le parcours de pile échoue.

 Code qui s’appuie sur ces actions doit être évaluation minutieuse des vulnérabilités de sécurité en raison de leur utilité limitée et leur comportement subtile. Considérez ce qui suit :

- [Demandes de liaison](/dotnet/framework/misc/link-demands) ne sont pas affectés par Deny ou PermitOnly.

- Si Deny ou PermitOnly se produit dans le même frame de pile en tant que la demande qui déclenche le parcours de pile, les actions de sécurité n’ont aucun effet.

- Les valeurs qui sont utilisés pour construire des autorisations basées sur le chemin d’accès peuvent généralement être spécifiés de plusieurs façons. Refuser l’accès à une forme de chemin d’accès ne pas refuse l’accès à toutes les formes. Par exemple, si un partage de fichiers \\\Server\Share est mappé à un lecteur réseau x, pour refuser l’accès à un fichier sur le partage, vous devez refuser \\\Server\Share\File, X:\File et chaque autre chemin d’accès qui accède au fichier.

- Un <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> peut mettre fin à un parcours de pile avant que Deny ou PermitOnly soit atteinte.

- Si une instruction Deny a un effet, à savoir, quand un appelant dispose d’une autorisation qui est bloquée par le refus, l’appelant peut accéder directement, la ressource protégée en contournant la refuser. De même, si l’appelant n’a pas l’autorisation refusée, le parcours de pile échoue sans la refuser.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Toute utilisation de ces actions de sécurité entraîne une violation. Pour corriger une violation, n’utilisez pas ces actions de sécurité.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimer un avertissement de cette règle uniquement après avoir effectué une révision de sécurité.

## <a name="example-1"></a>Exemple 1
 L’exemple suivant illustre certaines limitations de Deny.

 La bibliothèque suivante contient une classe qui possède deux méthodes qui sont identiques à l’exception des demandes de sécurité qui les protègent.

 [!code-csharp[FxCop.Security.PermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_1.cs)]

## <a name="example-2"></a>Exemple 2
 L’application suivante montre les effets de Deny sur les méthodes sécurisées à partir de la bibliothèque.

 [!code-csharp[FxCop.Security.TestPermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_2.cs)]

Cet exemple génère la sortie suivante :

```txt
Demand: Caller's Deny has no effect on Demand with the asserted permission.
LinkDemand: Caller's Deny has no effect on LinkDemand with the asserted permission.
LinkDemand: Caller's Deny has no effect with LinkDemand-protected code.
LinkDemand: This Deny has no effect with LinkDemand-protected code.
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName>
- <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
- <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>
- <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>
- [Instructions de codage sécurisé](/dotnet/standard/security/secure-coding-guidelines)