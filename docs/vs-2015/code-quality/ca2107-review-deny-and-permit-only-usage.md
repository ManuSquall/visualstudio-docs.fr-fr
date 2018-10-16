---
title: 'CA2107 : Révision refuser et autoriser uniquement l’utilisation | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2107
- ReviewDenyAndPermitOnlyUsage
helpviewer_keywords:
- ReviewDenyAndPermitOnlyUsage
- CA2107
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b317ddb69dea8241ead6bb70d50c3b99d96bd078
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49178644"
---
# <a name="ca2107-review-deny-and-permit-only-usage"></a>CA2107 : Passez en revue l'utilisation des méthodes Deny et PermitOnly
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|ReviewDenyAndPermitOnlyUsage|
|CheckId|CA2107|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une méthode contient une vérification de sécurité qui spécifie l’action de sécurité PermitOnly ou Deny.

## <a name="rule-description"></a>Description de la règle
 Le [à l’aide de la méthode PermitOnly](http://msdn.microsoft.com/en-us/8c7bdb7f-882f-45b7-908c-6cbaa1767649) et <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> actions de sécurité doivent être utilisées uniquement par les utilisateurs qui ont une connaissance avancée de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sécurité. Le code qui utilise ces actions de sécurité doit subir une révision de sécurité.

 Refuser modifie le comportement par défaut de la pile qui se produit en réponse à une demande de sécurité. Il vous permet de spécifier des autorisations qui ne doivent pas être accordées sur la durée de la méthode de refus, indépendamment des autorisations réelles des appelants dans la pile des appels. Si le parcours de pile détecte une méthode sécurisée par Deny, et si l’autorisation demandée est incluse dans les autorisations refusées, le parcours de pile échoue. PermitOnly modifie également le comportement par défaut de la pile. Il permet au code de spécifier uniquement les autorisations qui peuvent être accordées, quelles que soient les autorisations des appelants. Si le parcours de pile détecte une méthode sécurisée par PermitOnly, et si l’autorisation demandée n’est pas incluse dans les autorisations qui sont spécifiées par l’action PermitOnly, le parcours de pile échoue.

 Code qui s’appuie sur ces actions doit être évaluation minutieuse des vulnérabilités de sécurité en raison de leur utilité limitée et leur comportement subtile. Considérez ce qui suit :

-   [Demandes de liaison](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) ne sont pas affectés par Deny ou PermitOnly.

-   Si Deny ou PermitOnly se produit dans le même frame de pile en tant que la demande qui déclenche le parcours de pile, les actions de sécurité n’ont aucun effet.

-   Les valeurs qui sont utilisés pour construire des autorisations basées sur le chemin d’accès peuvent généralement être spécifiés de plusieurs façons. Refuser l’accès à une forme de chemin d’accès ne pas refuse l’accès à toutes les formes. Par exemple, si un partage de fichiers \\\Server\Share est mappé à un lecteur réseau x, pour refuser l’accès à un fichier sur le partage, vous devez refuser \\\Server\Share\File, X:\File et chaque autre chemin d’accès qui accède au fichier.

-   Un <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> peut mettre fin à un parcours de pile avant que Deny ou PermitOnly soit atteinte.

-   Si une instruction Deny a un effet, à savoir, quand un appelant dispose d’une autorisation qui est bloquée par le refus, l’appelant peut accéder directement, la ressource protégée en contournant la refuser. De même, si l’appelant n’a pas l’autorisation refusée, le parcours de pile échoue sans la refuser.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Toute utilisation de ces actions de sécurité entraîne une violation. Pour corriger une violation, n’utilisez pas ces actions de sécurité.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimer un avertissement de cette règle uniquement après avoir effectué une révision de sécurité.

## <a name="example"></a>Exemple
 L’exemple suivant illustre certaines limitations de Deny.

 La bibliothèque suivante contient une classe qui possède deux méthodes qui sont identiques à l’exception des demandes de sécurité qui les protègent.

 [!code-csharp[FxCop.Security.PermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PermitAndDeny/cs/FxCop.Security.PermitAndDeny.cs#1)]

## <a name="example"></a>Exemple
 L’application suivante montre les effets de Deny sur les méthodes sécurisées à partir de la bibliothèque.

 [!code-csharp[FxCop.Security.TestPermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestPermitAndDeny/cs/FxCop.Security.TestPermitAndDeny.cs#1)]

 Cet exemple produit la sortie suivante.

 **À la demande : Refus de l’appelant n’a aucun effet sur la demande avec l’autorisation déclarée. ** 
 **LinkDemand : refus de l’appelant n’a aucun effet sur LinkDemand avec l’autorisation déclarée.** 
 **LinkDemand : refus de l’appelant n’a aucun effet avec le code protégé par un LinkDemand.** 
 **LinkDemand : refuser cette n’a aucun effet avec le code protégé par un LinkDemand.**
## <a name="see-also"></a>Voir aussi
 <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName> <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>
 <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>
 [Instructions de codage sécurisé](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [substitution des vérifications de sécurité](http://msdn.microsoft.com/en-us/4acdeff5-fc05-41bf-8505-7387cdbfca28) [à l’aide de la méthode PermitOnly](http://msdn.microsoft.com/en-us/8c7bdb7f-882f-45b7-908c-6cbaa1767649)



