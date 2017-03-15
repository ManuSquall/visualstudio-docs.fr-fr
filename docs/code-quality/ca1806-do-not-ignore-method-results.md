---
title: "CA1806 : Ne pas ignorer les r&#233;sultats de m&#233;thode | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1806"
  - "DoNotIgnoreMethodResults"
helpviewer_keywords: 
  - "CA1806"
  - "DoNotIgnoreMethodResults"
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1806 : Ne pas ignorer les r&#233;sultats de m&#233;thode
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotIgnoreMethodResults|  
|CheckId|CA1806|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Cet avertissement peut s'afficher pour plusieurs raisons :  
  
-   Un nouvel objet est créé mais n'est jamais utilisé.  
  
-   Une méthode qui crée et retourne une nouvelle chaîne est appelée et la nouvelle chaîne n'est jamais utilisée.  
  
-   Une méthode COM ou P\/Invoke qui retourne un HRESULT ou un code d'erreur qui n'est jamais utilisé.  Description de la règle  
  
 La création d'un objet inutile et le garbage collection associé de l'objet inutilisé diminuent les performances.  
  
 Les chaînes sont immuables et les méthodes telles que String.ToUpper retournent une nouvelle instance d'une chaîne au lieu de modifier l'instance de la chaîne dans la méthode d'appel.  
  
 Ignorer un HRESULT ou un code d'erreur peut entraîner un comportement inattendu dans les conditions d'erreur ou des situations de ressources limitées.  
  
## Comment corriger les violations  
 Si la méthode A crée une instance de l'objet B qui n'est jamais utilisée, passez l'instance en tant qu'argument à une autre méthode ou assignez\-la à une variable.  Si la création d'objet n'est pas nécessaire, supprimez\-la. – ou –  
  
 Si la méthode A appelle la méthode B, mais n'utilise pas la nouvelle instance de chaîne retournée par la méthode B.  Passez l'instance en tant qu'argument à une autre méthode, assignez l'instance à une variable.  Ou supprimez l'appel s'il n'est pas nécessaire.  
  
 ou  
  
 Si la méthode A appelle la méthode B, mais n'utilise pas le HRESULT ou le code d'erreur retourné par la méthode.  Utilisez le résultat dans une instruction conditionnelle, assignez le résultat à une variable ou passez\-le comme argument à une autre méthode.  
  
## Quand supprimer les avertissements  
 Ne supprimez pas d'avertissement de cette règle à moins que l'acte de la création de l'objet serve à un but quelconque.  
  
## Exemple  
 L'exemple suivant illustre une classe qui ignore le résultat de l'appel de String.Trim.  
  
 [!CODE [FxCop.Usage.DoNotIgnoreMethodResults#1](FxCop.Usage.DoNotIgnoreMethodResults#1)]  
  
## Exemple  
 L'exemple suivant résout la violation précédente en réassignant le résultat de String.Trim à la variable qui l'a appelé.  
  
 [!CODE [FxCop.Usage.DoNotIgnoreMethodResults2#1](FxCop.Usage.DoNotIgnoreMethodResults2#1)]  
  
## Exemple  
 L'exemple suivant présente une méthode qui n'utilise pas un objet qu'elle crée.  
  
> [!NOTE]
>  Cette violation ne peut pas être reproduite en Visual Basic.  
  
 [!code-cs[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_1.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_1.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_1.cpp)]  
  
## Exemple  
 L'exemple suivant résout la violation précédente en supprimant la création inutile d'un objet.  
  
 [!code-cs[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_2.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_2.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_2.cpp)]  
  
## Exemple  
 L'exemple suivant affiche une méthode qui ignore le code d'erreur retourné par la méthode GetShortPathName native.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_3.cpp)]
 [!code-cs[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_3.cs)]  
  
## Exemple  
 L'exemple suivant résout la violation précédente en vérifiant le code d'erreur et en levant une exception en cas d'échec de l'appel.  
  
 [!code-cs[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_4.cs)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_4.cpp)]