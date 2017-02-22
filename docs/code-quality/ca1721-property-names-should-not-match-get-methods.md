---
title: "CA1721&#160;: Les noms des propri&#233;t&#233;s ne doivent pas &#234;tre identiques &#224; ceux des m&#233;thodes Get | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1721"
  - "PropertyNamesShouldNotMatchGetMethods"
helpviewer_keywords: 
  - "CA1721"
  - "PropertyNamesShouldNotMatchGetMethods"
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1721&#160;: Les noms des propri&#233;t&#233;s ne doivent pas &#234;tre identiques &#224; ceux des m&#233;thodes Get
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PropertyNamesShouldNotMatchGetMethods|  
|CheckId|CA1721|  
|Catégorie|Microsoft.Naming|  
|Modification avec rupture|Oui|  
  
## Cause  
 Le nom d'un membre public ou protégé commence par 'Get'. Sinon, il correspond au nom d'une propriété publique ou protégée.  Par exemple, un type qui contient une méthode nommée 'GetColor' et une propriété nommée 'Color' enfreint cette règle.  
  
## Description de la règle  
 Les méthodes et propriétés Get doivent porter des noms distinguant clairement leur fonction.  
  
 Les conventions d'affectation des noms confèrent un aspect commun aux bibliothèques qui ciblent le Common Language Runtime.  Elles réduisent le temps nécessaire pour apprendre une nouvelle bibliothèque de logiciels et confirment au client que la bibliothèque a été développée par une personne compétente en matière de développement de code managé.  
  
## Comment corriger les violations  
 Modifiez le nom afin qu'il ne corresponde pas au nom d'une méthode ayant 'Get' pour préfixe.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
> [!NOTE]
>  Cet avertissement peut être exclu si la méthode Get est causée par l'implémentation de l'interface IExtenderProvider.  
  
## Exemple  
 L'exemple suivant contient une méthode et une propriété qui enfreignent cette règle.  
  
 [!CODE [FxCop.Naming.GetMethod#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Naming.GetMethod#1)]  
  
## Règles connexes  
 [CA1024 : Utiliser les propriétés lorsque cela est approprié](../code-quality/ca1024-use-properties-where-appropriate.md)