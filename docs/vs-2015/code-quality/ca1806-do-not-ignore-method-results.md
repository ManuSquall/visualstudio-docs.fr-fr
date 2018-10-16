---
title: 'CA1806 : Ne pas ignorer les résultats de la méthode | Microsoft Docs'
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
- CA1806
- DoNotIgnoreMethodResults
helpviewer_keywords:
- CA1806
- DoNotIgnoreMethodResults
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5d28ca688bbad0054f7522034bfe309dcb1fe698
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49250105"
---
# <a name="ca1806-do-not-ignore-method-results"></a>CA1806 : Ne pas ignorer les résultats de méthode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotIgnoreMethodResults|  
|CheckId|CA1806|  
|Category|Microsoft.Usage|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Il existe plusieurs raisons possibles à cet avertissement :  
  
-   Un nouvel objet est créé mais jamais utilisé.  
  
-   Une méthode qui crée et retourne une nouvelle chaîne est appelée et la nouvelle chaîne n’est jamais utilisée.  
  
-   Une méthode COM ou P/Invoke qui retourne un HRESULT ou code d’erreur qui n’est jamais utilisée. Description de la règle  
  
 Création d’un objet inutile et le garbage collection associé de l’objet inutilisé dégrader les performances.  
  
 Les chaînes sont immuables et les méthodes telles que String.ToUpper retourne une nouvelle instance d’une chaîne au lieu de modifier l’instance de la chaîne dans la méthode d’appel.  
  
 Ignorer les HRESULT ou code d’erreur peut entraîner un comportement inattendu dans les conditions d’erreur ou à des conditions de ressources insuffisantes.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Si la méthode A crée une nouvelle instance de l’objet B qui n’est jamais utilisée, passez l’instance comme argument à une autre méthode ou assignez l’instance à une variable. Si la création de l’objet n’est pas nécessaire, supprimez-la.- ou -  
  
 Si la méthode A appelle la méthode B, mais n’utilise pas la nouvelle instance de chaîne retournée par la méthode B. Passez l’instance comme argument à une autre méthode, assignez l’instance à une variable. Ou supprimez l’appel s’il n’est pas nécessaire.  
  
 - ou -  
  
 Si la méthode A appelle la méthode B, mais n’utilise pas le HRESULT ou code d’erreur que la méthode retourne. Utiliser le résultat dans une instruction conditionnelle, assignez le résultat à une variable ou passez-le en tant qu’argument à une autre méthode.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez pas un avertissement de cette règle, sauf si l’opération de création de l’objet sert un but quelconque.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une classe qui ignore le résultat de l’appel de String.Trim.  
  
<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults#1](FxCop.Usage.DoNotIgnoreMethodResults#1)]  -->  
  
## <a name="example"></a>Exemple  
 L’exemple suivant résout la violation précédente en assignant le résultat de String.Trim à la variable que qui l’a appelé.  
  
<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults2#1](FxCop.Usage.DoNotIgnoreMethodResults2#1)]  -->  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une méthode qui n’utilise pas un objet qu’il crée.  
  
> [!NOTE]
>  Cette violation ne peut pas être reproduite dans Visual Basic.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cpp/FxCop.Usage.DoNotIgnoreMethodResults3.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cs/FxCop.Usage.DoNotIgnoreMethodResults3.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/vb/FxCop.Usage.DoNotIgnoreMethodResults3.vb#1)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant résout la violation précédente en supprimant la création inutile d’un objet.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cpp/FxCop.Usage.DoNotIgnoreMethodResults4.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cs/FxCop.Usage.DoNotIgnoreMethodResults4.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/vb/FxCop.Usage.DoNotIgnoreMethodResults4.vb#1)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une méthode qui ignore le code d’erreur retourné par la méthode native GetShortPathName.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cpp/FxCop.Usage.DoNotIgnoreMethodResults5.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cs/FxCop.Usage.DoNotIgnoreMethodResults5.cs#1)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant résout la violation précédente en vérifiant le code d’erreur et en levant une exception lorsque l’appel échoue.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cpp/FxCop.Usage.DoNotIgnoreMethodResults6.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cs/FxCop.Usage.DoNotIgnoreMethodResults6.cs#1)]