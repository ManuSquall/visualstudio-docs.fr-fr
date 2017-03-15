---
title: "CA2117 : Les types APTCA doivent uniquement &#233;tendre des types de base APTCA | Microsoft Docs"
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
  - "CA2117"
  - "AptcaTypesShouldOnlyExtendAptcaBaseTypes"
helpviewer_keywords: 
  - "AptcaTypesShouldOnlyExtendAptcaBaseTypes"
  - "CA2117"
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2117 : Les types APTCA doivent uniquement &#233;tendre des types de base APTCA
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|  
|CheckId|CA2117|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un type public ou protégé dans un assembly doté de l'attribut <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> hérite d'un type déclaré présent dans un assembly dépourvu de l'attribut.  
  
## Description de la règle  
 Par défaut, des types publics ou protégés placés dans des assemblys présentant des noms forts sont implicitement protégés par un [Inheritance Demands](http://msdn.microsoft.com/fr-fr/28b9adbb-8f08-4f10-b856-dbf59eb932d9) dans le cadre confiance totale.  Les assemblys dotés de noms forts marqués de l'attribut <xref:System.Security.AllowPartiallyTrustedCallersAttribute> \(APTCA\) n'ont pas cette protection.  L'attribut désactive la demande d'héritage.  Les types exposés sont alors déclarés dans l'assembly pouvant être hérité par des types dépourvus de confiance totale.  
  
 Lorsque l'attribut APTCA est présent sur un assembly doté d'une confiance totale et lorsqu'un type présent dans l'assembly hérite d'un type qui n'autorise pas les appelants partiellement approuvés, une exploitation de la sécurité devient possible.  Si deux types `T1` et `T2` satisfont les conditions suivantes, des appelants malveillants peuvent utiliser le type `T1` pour contourner la demande d'héritage de confiance totale implicite qui protège le type `T2` :  
  
-   `T1` est un type public déclaré dans un assembly doté d'une confiance totale et de l'attribut APTCA.  
  
-   `T1` hérite d'un type `T2` présent hors de son assembly.  
  
-   L'assembly de `T2` est dépourvu d'attribut APTCA ; par conséquent, les types présents dans des assemblys dotés d'une confiance partielle ne doivent pas pouvoir en hériter.  
  
 Un type `X` doté d'une confiance partielle peut hériter de `T1`, qui lui donne alors accès aux membres hérités déclarés dans `T2`.  Sachant que `T2` est dépourvu d'attribut APTCA, son type dérivé immédiat \(`T1`\) doit satisfaire une demande d'héritage pour la confiance totale ; `T1` dispose d'une confiance totale et, par conséquent, satisfait ce contrôle.  En termes de sécurité, le problème tient dans ce que `X` ne contribue pas à satisfaire la demande d'héritage qui protège `T2` d'un sous\-classement non approuvé.  Pour cette raison, les types dotés de l'attribut APTCA ne doivent étendre aucun type dépourvu de l'attribut.  
  
 Un autre problème de sécurité, probablement plus répandu, tient dans ce que le type dérivé \(`T1`\) peut, par le biais d'une erreur du programmeur, exposer des membres protégés du type qui requiert la confiance totale \(`T2`\).  Lorsque cette situation se produit, les appelants non approuvés ont accès à des informations qui ne doivent être disponibles qu'aux types dotés d'une confiance totale.  
  
## Comment corriger les violations  
 Si le type rapporté par l'infraction se trouve dans un assembly qui ne requiert pas l'attribut APTCA, supprimez\-le.  
  
 Si l'attribut APTCA est requis, ajoutez au type une demande d'héritage pour la confiance totale.  Ce procédé permet de se protéger contre l'héritage par les types non approuvés.  
  
 Il est possible de corriger une infraction en ajoutant l'attribut APTCA aux assemblys des types de base rapportés par celle\-ci.  Ne le faites pas sans procéder en premier lieu à une révision scrupuleuse de la sécurité de l'ensemble du code des assemblys et tout code qui dépend de ces derniers.  
  
## Quand supprimer les avertissements  
 Pour supprimer sans risque un avertissement de cette règle, vous devez vous assurer que les membres protégés exposés par votre type ne donnent pas, directement ou indirectement, à des appelants non approuvés un accès à des informations, des opérations ou des ressources sensibles, susceptibles d'être utilisées de façon destructrice.  
  
## Exemple  
 L'exemple suivant utilise deux assemblys et une application de test pour illustrer la faille de sécurité détectée par cette règle.  Le premier assembly ne dispose pas de l'attribut APTCA et ne doit pas pouvoir être hérité par des types dotés d'une confiance partielle \(représentés par `T2` dans l'exposé précédent\).  
  
 [!code-cs[FxCop.Security.NoAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_1.cs)]  
  
## Exemple  
 Le second assembly, représenté par `T1` dans l'exposé précédent, est doté d'une confiance totale et autorise des appelants partiellement approuvés.  
  
 [!CODE [FxCop.Security.YesAptcaInherit#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptcaInherit#1)]  
  
## Exemple  
 Le type de test, représenté par `X` dans l'exposé précédent, se trouve dans un assembly doté d'une confiance partielle.  
  
 [!CODE [FxCop.Security.TestAptcaInherit#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaInherit#1)]  
  
 Cet exemple génère la sortie suivante.  
  
  **Meet at the shady glen 2\/22\/2003 12:00:00 AM\!**  
**From Test: sunny meadow**  
**Meet at the sunny meadow 2\/22\/2003 12:00:00 AM\!**   
## Règles connexes  
 [CA2116 : Les méthodes APTCA doivent uniquement appeler des méthodes APTCA](../Topic/CA2116:%20APTCA%20methods%20should%20only%20call%20APTCA%20methods.md)  
  
## Voir aussi  
 [Instructions de codage sécurisé](../Topic/Secure%20Coding%20Guidelines.md)   
 [.NET Framework Assemblies Callable by Partially Trusted Code](http://msdn.microsoft.com/fr-fr/a417fcd4-d3ca-4884-a308-3a1a080eac8d)   
 [Utilisation de bibliothèques à partir de code d'un niveau de confiance partiel](../Topic/Using%20Libraries%20from%20Partially%20Trusted%20Code.md)   
 [Inheritance Demands](http://msdn.microsoft.com/fr-fr/28b9adbb-8f08-4f10-b856-dbf59eb932d9)