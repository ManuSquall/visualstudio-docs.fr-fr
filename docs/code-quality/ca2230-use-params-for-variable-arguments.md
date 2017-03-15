---
title: "CA2230&#160;: Utilisez le mot cl&#233; params pour les arguments de variables | Microsoft Docs"
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
  - "UseParamsForVariableArguments"
  - "CA2230"
helpviewer_keywords: 
  - "CA2230"
  - "UseParamsForVariableArguments"
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2230&#160;: Utilisez le mot cl&#233; params pour les arguments de variables
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseParamsForVariableArguments|  
|CheckId|CA2230|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un type public ou protégé contient une méthode publique ou protégée qui utilise la convention d'appel `VarArgs`.  
  
## Description de la règle  
 La convention d'appel `VarArgs` est utilisée avec certaines définitions de méthode qui acceptent un nombre variable de paramètres.  Une méthode qui utilise la convention d'appel `VarArgs` n'est pas conforme CLS et peut ne pas être accessible à l'échelle de plusieurs langages de programmation.  
  
 En C\#, la convention d'appel `VarArgs` est utilisée lorsque la liste des paramètres d'une méthode se termine par le mot clé `__arglist`.  Visual Basic ne prend pas en charge la convention d'appel `VarArgs`, et Visual C\+\+ autorise uniquement son utilisation dans un code non managé qui utilise la notation elliptique `...`.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle en C\#, utilisez le mot clé [params](/dotnet/csharp/language-reference/keywords/params) au lieu de `__arglist`.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Exemple  
 L'exemple suivant présente deux méthodes ; une qui enfreint la règle et une autre qui la satisfait.  
  
 [!code-cs[FxCop.Usage.UseParams#1](../code-quality/codesnippet/CSharp/ca2230-use-params-for-variable-arguments_1.cs)]  
  
## Voir aussi  
 <xref:System.Reflection.CallingConventions?displayProperty=fullName>   
 [Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)