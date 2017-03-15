---
title: "CA2118 : R&#233;vision de l&#39;utilisation de SuppressUnmanagedCodeSecurityAttribute | Microsoft Docs"
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
  - "CA2118"
  - "ReviewSuppressUnmanagedCodeSecurityUsage"
helpviewer_keywords: 
  - "CA2118"
  - "ReviewSuppressUnmanagedCodeSecurityUsage"
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2118 : R&#233;vision de l&#39;utilisation de SuppressUnmanagedCodeSecurityAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|  
|CheckId|CA2118|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un type ou un membre public ou protégé dispose de l'attribut <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>.  
  
## Description de la règle  
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> modifie le comportement par défaut du système en matière de sécurité pour les membres qui exécutent le code non managé à l'aide de COM Interop ou de l'appel de code non managé.  En général, le système effectue un [Données et modélisation](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md) pour l'autorisation de code non managé.  Cette demande se produit au moment de l'exécution pour chaque appel au membre et vérifie l'autorisation de chaque appelant présent dans la pile des appels.  Lorsque l'attribut est présent, le système effectue un [Demandes de liaison](../Topic/Link%20Demands.md) pour l'autorisation : les autorisations de l'appelant immédiat sont vérifiées lorsque celui\-ci est traité par le compilateur JIT.  
  
 Cet attribut est essentiellement utilisé pour accroître les performances ; toutefois, les gains de performance s'accompagnent de risques substantiels pour la sécurité.  Si vous placez l'attribut sur des membres publics qui appellent des méthodes natives, les appelants présents dans la pile des appels \(autre que l'appelant immédiat\) n'ont pas besoin d'autorisation pour exécuter le code non managé.  Selon les actions du membre public et la gestion des entrées, les appelants non fiables de confiance peuvent accéder à des fonctionnalités normalement restreintes à un code fiable.  
  
 Le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] repose sur des vérifications de sécurité visant à empêcher des appelants d'obtenir un accès direct à l'espace d'adressage du processus actuel.  Sachant que cet attribut contourne la sécurité normale, votre code constitue une sérieuse menace s'il peut être utilisé pour effectuer des opérations de lecture ou d'écriture dans la mémoire du processus.  Notez que le risque ne se limite pas aux méthodes qui donnent intentionnellement accès à la mémoire d'un processus : il est également présent dans tout scénario où un code malveillant peut obtenir un accès par quelque moyen que ce soit ; par exemple, en fournissant des entrées déconcertantes, incorrectes ou non valides.  
  
 La stratégie de sécurité par défaut n'accorde à un code non managé aucune autorisation d'accès à un assembly, saut s'il s'exécute à partir de l'ordinateur local ou s'il est membre de l'un des groupes suivants :  
  
-   Groupe de code de la zone Poste de travail  
  
-   Groupe de code des noms forts Microsoft  
  
-   Groupe de code des noms forts ECMA  
  
## Comment corriger les violations  
 Passez méticuleusement en revue votre code pour vous assurer que cet attribut est absolument nécessaire.  Si vous êtes peu familiarisé avec la sécurité du code managé, ou si vous ne comprenez pas les implications en termes de sécurité de l'utilisation de cet attribut, supprimez\-le de votre code.  Si l'attribut est requis, vous devez vous assurer que les appelants ne peuvent pas utiliser votre code de manière néfaste.  Si votre code n'est pas autorisé à exécuter un code non managé, cet attribut n'a aucun effet et doit être supprimé.  
  
## Quand supprimer les avertissements  
 Pour supprimer sans risque un avertissement de cette règle, vous devez vous assurer que votre code ne donne aux appelants aucun accès à des opérations ou des ressources natives susceptibles d'être utilisées de façon néfaste.  
  
## Exemple  
 L'exemple suivant enfreint la règle.  
  
 [!code-cs[FxCop.Security.TypesDoNotSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_1.cs)]  
  
## Exemple  
 Dans l'exemple suivant, la méthode `DoWork` fournit un chemin d'accès de code publiquement accessible à la méthode d'appel de code non managé `FormatHardDisk`.  
  
 [!code-cs[FxCop.Security.PInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_2.cs)]  
  
## Exemple  
 Dans l'exemple suivant, la méthode publique `DoDangerousThing` entraîne une violation.  Pour corriger la violation, `DoDangerousThing` doit être rendu privée, et l'accès à celle\-ci doit se faire par le biais d'une méthode publique sécurisée par une demande de sécurité, comme illustré par la méthode `DoWork`.  
  
 [!CODE [FxCop.Security.TypeInvokeAndSuppress#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Security.TypeInvokeAndSuppress#1)]  
  
## Voir aussi  
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>   
 [Instructions de codage sécurisé](../Topic/Secure%20Coding%20Guidelines.md)   
 [Security Optimizations](http://msdn.microsoft.com/fr-fr/cf255069-d85d-4de3-914a-e4625215a7c0)   
 [Données et modélisation](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)   
 [Demandes de liaison](../Topic/Link%20Demands.md)