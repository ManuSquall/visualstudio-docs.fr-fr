---
title: "CA2112&#160;: Les types s&#233;curis&#233;s ne doivent pas exposer de champs | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2112"
  - "SecuredTypesShouldNotExposeFields"
helpviewer_keywords: 
  - "CA2112"
  - "SecuredTypesShouldNotExposeFields"
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2112&#160;: Les types s&#233;curis&#233;s ne doivent pas exposer de champs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SecuredTypesShouldNotExposeFields|  
|CheckId|CA2112|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un type public ou protégé contient des champs publics et est sécurisé par un [Demandes de liaison](../Topic/Link%20Demands.md).  
  
## Description de la règle  
 Si un code a accès à une instance d'un type sécurisé par une demande de liaison, ce code n'a pas besoin de satisfaire la demande de liaison pour accéder aux champs du type.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, rendez les champs non publics et ajoutez des propriétés ou des méthodes publiques qui retournent les données du champ.  Les vérifications de la sécurité LinkDemand appliquées à des types protègent l'accès aux propriétés et aux méthodes de ce type.  Toutefois, la sécurité d'accès du code ne s'applique pas aux champs.  
  
## Quand supprimer les avertissements  
 Pour des questions de sécurité et de design dans les règles de l'art, vous devez corriger les violations en rendant les champs publics non publics.  Vous pouvez supprimer un avertissement de cette règle si le champ ne contient pas d'informations qui doivent rester sécurisées, et si vous ne fondez aucune opération sur le contenu du champ.  
  
## Exemple  
 L'exemple suivant est composé d'un type \(`SecuredTypeWithFields`\) de bibliothèque doté de champs non sécurisés ; d'un type \(`Distributor`\) qui peut créer des instances du type de la bibliothèque et qui passe par erreur des instances à des types qui n'ont pas l'autorisation de les créer, et d'un code d'application qui peut lire les champs d'une instance bien qu'il ne dispose pas de l'autorisation qui sécurise le type.  
  
 Le code de bibliothèque suivant enfreint la règle.  
  
 [!code-cs[FxCop.Security.LinkDemandOnField#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_1.cs)]  
  
## Exemple  
 L'application ne peut pas créer d'instance à cause de la demande de liaison qui protège le type sécurisé.  La classe suivante permet à l'application d'obtenir une instance du type sécurisé.  
  
 [!CODE [FxCop.Security.LDOnFieldsDistributor#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Security.LDOnFieldsDistributor#1)]  
  
## Exemple  
 L'application suivante montre comment, sans autorisation d'accès aux méthodes du type sécurisé, le code peut accéder à ses champs.  
  
 [!code-cs[FxCop.Security.TestLinkDemandOnFields#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_2.cs)]  
  
 Cet exemple génère la sortie suivante.  
  
  **Création d'une instance de SecuredTypeWithFields.**  
**Secured type fields: 22, 33**  
**Modification du champ du type sécurisé…**  
**Champs d'objet mis en cache : 99, 33**   
## Règles connexes  
 [CA1051 : Ne pas déclarer de champs d'instances visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)  
  
## Voir aussi  
 [Demandes de liaison](../Topic/Link%20Demands.md)   
 [Données et modélisation](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)