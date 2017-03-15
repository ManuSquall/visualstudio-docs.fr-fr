---
title: "CA2107 : Passez en revue l&#39;utilisation des m&#233;thodes Deny et PermitOnly | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2107"
  - "ReviewDenyAndPermitOnlyUsage"
helpviewer_keywords: 
  - "ReviewDenyAndPermitOnlyUsage"
  - "CA2107"
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2107 : Passez en revue l&#39;utilisation des m&#233;thodes Deny et PermitOnly
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewDenyAndPermitOnlyUsage|  
|CheckId|CA2107|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Oui|  
  
## Cause  
 Une méthode contient une vérification de la sécurité. Celle\-ci spécifie l'action de sécurité PermitOnly ou Deny.  
  
## Description de la règle  
 Les actions de sécurité [Using the PermitOnly Method](http://msdn.microsoft.com/fr-fr/8c7bdb7f-882f-45b7-908c-6cbaa1767649) et <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> doivent être utilisées uniquement par des développeurs possédant une connaissance avancée de la sécurité du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Le code qui utilise ces actions de sécurité doit subir une révision de sécurité.  
  
 L'action de refus Deny modifie le comportement par défaut du parcours de la pile qui se produit en réponse à une demande de sécurité.  Elle vous permet de spécifier des autorisations qui ne doivent pas être accordées sur la durée de la méthode de refus, indépendamment des autorisations réelles des appelants dans la pile des appels.  Si le parcours de la pile détecte une méthode sécurisée par l'action Deny, et si l'autorisation demandée est intégrée aux autorisations refusées, le parcours de la pile échoue.  L'action PermitOnly modifie également le comportement par défaut du parcours de la pile.  Elle permet au code de spécifier uniquement les autorisations qui peuvent être accordées, indépendamment des autorisations dont disposent les appelants.  Si le parcours de la pile détecte une méthode sécurisée par PermitOnly, et si l'autorisation demandée n'est pas intégrée aux autorisations spécifiées par l'action PermitOnly, le parcours de la pile échoue.  
  
 Un code qui repose sur ces actions doit faire l'objet d'une évaluation minutieuse en termes de faille de sécurité du fait de son utilité limitée et de son comportement subtil.  Considérez ce qui suit :  
  
-   Les [Demandes de liaison](../Topic/Link%20Demands.md) ne sont pas affectés par les actions Deny ou PermitOnly.  
  
-   Si l'action Deny ou PermitOnly se produit dans le même frame de pile que la demande qui déclenche le parcours de la pile, les actions de sécurité n'ont aucun effet.  
  
-   Les valeurs utilisées pour construire des autorisations fondées sur un chemin d'accès peuvent en général être spécifiées de plusieurs manières.  Refuser l'accès à un des formulaires du chemin d'accès ne le refuse pas à tous les formulaires.  Par exemple, si un partage de fichiers \\\\Server\\Share est mappé à un lecteur réseau X:, pour refuser l'accès à un fichier de ce partage, vous devez le refuser à \\\\Server\\Share\\File, à X:\\File, ainsi qu'à chaque autre chemin d'accès qui mène à ce fichier.  
  
-   Un <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> peut mettre fin à un parcours de pile avant qu'une action Deny ou PermitOnly soit atteinte.  
  
-   Si une action Deny a un effet, à savoir, lorsqu'un appelant voit une autorisation bloquée par Deny, cet appelant peut accéder directement à la ressource protégée, en ignorant l'action Deny.  De même, si l'appelant ne dispose pas de l'autorisation refusée, le parcours de la pile échouera sans intervention de l'action Deny.  
  
## Comment corriger les violations  
 Toute utilisation de ces actions de sécurité provoquera une violation.  Pour corriger une violation, n'utilisez pas ces actions de sécurité.  
  
## Quand supprimer les avertissements  
 Supprimez uniquement un avertissement de cette règle après avoir effectué une révision de sécurité.  
  
## Exemple  
 L'exemple suivant présente quelques limitations de l'action Deny.  
  
 La bibliothèque suivante contient une classe dotée de deux méthodes identiques en tout point exception faite des demandes de sécurité qui les protègent.  
  
 [!CODE [FxCop.Security.PermitAndDeny#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Security.PermitAndDeny#1)]  
  
## Exemple  
 L'application suivante montre les effets de l'action Deny sur les méthodes sécurisées de la bibliothèque.  
  
 [!code-cs[FxCop.Security.TestPermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_1.cs)]  
  
 Cet exemple génère la sortie suivante.  
  
  **Demande : Le refus de l'appelant n'a aucun effet sur la demande avec l'autorisation déclarée.**  
**LinkDemand : Le refus de l'appelant n'a aucun effet sur LinkDemand avec l'autorisation déclarée.**  
**LinkDemand : Le refus de l'appelant n'a aucun effet avec le code protégé par LinkDemand.**  
**LinkDemand : Ce refus n'a aucun effet avec le code protégé par LinkDemand.**   
## Voir aussi  
 <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName>   
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>   
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>   
 <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>   
 [Instructions de codage sécurisé](../Topic/Secure%20Coding%20Guidelines.md)   
 [Overriding Security Checks](http://msdn.microsoft.com/fr-fr/4acdeff5-fc05-41bf-8505-7387cdbfca28)   
 [Using the PermitOnly Method](http://msdn.microsoft.com/fr-fr/8c7bdb7f-882f-45b7-908c-6cbaa1767649)