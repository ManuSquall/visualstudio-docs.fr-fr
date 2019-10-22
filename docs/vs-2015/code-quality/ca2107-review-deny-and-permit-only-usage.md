---
title: 'CA2107 : passez en revue l’utilisation de Deny et autoriser uniquement | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2107
- ReviewDenyAndPermitOnlyUsage
helpviewer_keywords:
- ReviewDenyAndPermitOnlyUsage
- CA2107
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 32339852d67d4f3f28fedd204a056440ad49e075
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665964"
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
 L' [utilisation de la méthode PermitOnly](https://msdn.microsoft.com/8c7bdb7f-882f-45b7-908c-6cbaa1767649) et <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> actions de sécurité doivent être utilisées uniquement par les personnes qui ont une connaissance approfondie de la sécurité [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Le code qui utilise ces actions de sécurité doit subir une révision de sécurité.

 Deny modifie le comportement par défaut du parcours de la pile qui se produit en réponse à une demande de sécurité. Elle vous permet de spécifier les autorisations qui ne doivent pas être accordées pour la durée de la méthode de refus, indépendamment des autorisations réelles des appelants dans la pile des appels. Si le parcours de la pile détecte une méthode qui est sécurisée par Deny et si l’autorisation demandée est incluse dans les autorisations refusées, le parcours de la pile échoue. PermitOnly modifie également le comportement par défaut du parcours de la pile. Il permet au code de spécifier uniquement les autorisations qui peuvent être accordées, quelles que soient les autorisations des appelants. Si le parcours de la pile détecte une méthode qui est sécurisée par PermitOnly et si l’autorisation demandée n’est pas incluse dans les autorisations spécifiées par PermitOnly, le parcours de la pile échoue.

 Le code qui s’appuie sur ces actions doit être soigneusement évalué pour les vulnérabilités de sécurité en raison de leur utilité limitée et de son comportement subtil. Considérez les points suivants :

- Les [demandes de liaison](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) ne sont pas affectées par Deny ou PermitOnly.

- Si Deny ou PermitOnly se produit dans le même frame de pile que la demande qui provoque le parcours de la pile, les actions de sécurité n’ont aucun effet.

- Les valeurs utilisées pour construire des autorisations basées sur le chemin d’accès peuvent généralement être spécifiées de plusieurs façons. Le refus de l’accès à une forme du chemin d’accès ne refuse pas l’accès à tous les formulaires. Par exemple, si un partage de fichiers \\ \Server\Share est mappé sur un lecteur réseau X :, pour refuser l’accès à un fichier sur le partage, vous devez refuser \\ \Serveur\partage\fichier, X:\File et tout autre chemin d’accès qui accède au fichier.

- Une <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> peut mettre fin à un parcours de la pile avant que Deny ou PermitOnly soit atteint.

- Si un refus a un effet, à savoir, lorsqu’un appelant a une autorisation qui est bloquée par le refus, l’appelant peut accéder directement à la ressource protégée, en ignorant le refus. De même, si l’appelant n’a pas l’autorisation refusée, le parcours de pile échoue sans le refus.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Toute utilisation de ces actions de sécurité entraîne une violation. Pour corriger une violation, n’utilisez pas ces actions de sécurité.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimez un avertissement de cette règle uniquement après avoir effectué une révision de sécurité.

## <a name="example"></a>Exemple
 L’exemple suivant illustre certaines limitations de Deny.

 La bibliothèque suivante contient une classe qui a deux méthodes identiques, à l’exception des demandes de sécurité qui les protègent.

 [!code-csharp[FxCop.Security.PermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PermitAndDeny/cs/FxCop.Security.PermitAndDeny.cs#1)]

## <a name="example"></a>Exemple
 L’application suivante montre les effets de Deny sur les méthodes sécurisées de la bibliothèque.

 [!code-csharp[FxCop.Security.TestPermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestPermitAndDeny/cs/FxCop.Security.TestPermitAndDeny.cs#1)]

 Cet exemple produit la sortie suivante.

 **Demand : le refus de l’appelant n’a aucun effet sur la demande avec l’autorisation déclarée.** 
**LinkDemand : le refus de l’appelant n’a aucun effet sur LinkDemand avec l’autorisation déclarée.** 
**LinkDemand : le refus de l’appelant n’a aucun effet avec le code protégé par LinkDemand.** 
**LinkDemand : ce refus n’a aucun effet avec Code protégé par LinkDemand.**
## <a name="see-also"></a>Voir aussi
 <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName> <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>
 <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>
 [Instructions de codage sécurisé](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [substitution des vérifications de sécurité](https://msdn.microsoft.com/4acdeff5-fc05-41bf-8505-7387cdbfca28) [à l’aide de la méthode PermitOnly](https://msdn.microsoft.com/8c7bdb7f-882f-45b7-908c-6cbaa1767649)
