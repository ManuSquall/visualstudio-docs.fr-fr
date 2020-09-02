---
title: 'CA1806 : ne pas ignorer les résultats de la méthode | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1806
- DoNotIgnoreMethodResults
helpviewer_keywords:
- CA1806
- DoNotIgnoreMethodResults
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 726cde42eb08ee5508481887fae2e9d2b059256c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543869"
---
# <a name="ca1806-do-not-ignore-method-results"></a>CA1806 : N'ignorez pas les résultats des méthodes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|DoNotIgnoreMethodResults|
|CheckId|CA1806|
|Category|Microsoft. usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause :
 Il existe plusieurs raisons possibles pour cet avertissement :

- Un nouvel objet est créé, mais n’est jamais utilisé.

- Une méthode qui crée et retourne une nouvelle chaîne est appelée et la nouvelle chaîne n’est jamais utilisée.

- Méthode COM ou P/Invoke qui retourne un HRESULT ou un code d’erreur qui n’est jamais utilisé. Description de la règle

  La création d’objets inutiles et la garbage collection associée de l’objet inutilisé dégradent les performances.

  Les chaînes sont immuables et les méthodes telles que String. ToUpper retournent une nouvelle instance d’une chaîne au lieu de modifier l’instance de la chaîne dans la méthode d’appel.

  Si vous ignorez le code d’erreur ou HRESULT, vous risquez de provoquer un comportement inattendu des conditions d’erreur ou des conditions de ressources insuffisantes.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Si la méthode A crée une nouvelle instance de l’objet B qui n’est jamais utilisé, transmettez l’instance comme argument à une autre méthode ou assignez l’instance à une variable. Si la création de l’objet n’est pas nécessaire, supprimez-le.-ou-

 Si la méthode A appelle la méthode B, mais n’utilise pas la nouvelle instance de chaîne que la méthode B retourne. Transmettez l’instance comme argument à une autre méthode, assignez l’instance à une variable. Ou supprimez l’appel s’il n’est pas nécessaire.

 - ou -

 Si la méthode A appelle la méthode B, mais n’utilise pas le HRESULT ou le code d’erreur retourné par la méthode. Utilisez le résultat dans une instruction conditionnelle, assignez le résultat à une variable ou transmettez-le en tant qu’argument à une autre méthode.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas un avertissement de cette règle, sauf si le fait de créer l’objet a un but.

## <a name="example"></a>Exemple
 L’exemple suivant montre une classe qui ignore le résultat de l’appel de String. Trim.

<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults#1](FxCop.Usage.DoNotIgnoreMethodResults#1)]  -->

## <a name="example"></a>Exemple
 L’exemple suivant résout la violation précédente en affectant le résultat de String. Trim à la variable sur laquelle elle a été appelée.

<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults2#1](FxCop.Usage.DoNotIgnoreMethodResults2#1)]  -->

## <a name="example"></a>Exemple
 L’exemple suivant montre une méthode qui n’utilise pas un objet qu’elle crée.

> [!NOTE]
> Cette violation ne peut pas être reproduite dans Visual Basic.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cpp/FxCop.Usage.DoNotIgnoreMethodResults3.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cs/FxCop.Usage.DoNotIgnoreMethodResults3.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/vb/FxCop.Usage.DoNotIgnoreMethodResults3.vb#1)]

## <a name="example"></a>Exemple
 L’exemple suivant résout la violation précédente en supprimant la création inutile d’un objet.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cpp/FxCop.Usage.DoNotIgnoreMethodResults4.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cs/FxCop.Usage.DoNotIgnoreMethodResults4.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/vb/FxCop.Usage.DoNotIgnoreMethodResults4.vb#1)]

## <a name="example"></a>Exemple
 L’exemple suivant montre une méthode qui ignore le code d’erreur retourné par la méthode GetShortPathName native.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cpp/FxCop.Usage.DoNotIgnoreMethodResults5.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cs/FxCop.Usage.DoNotIgnoreMethodResults5.cs#1)]

## <a name="example"></a>Exemple
 L’exemple suivant résout la violation précédente en vérifiant le code d’erreur et en levant une exception lorsque l’appel échoue.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cpp/FxCop.Usage.DoNotIgnoreMethodResults6.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cs/FxCop.Usage.DoNotIgnoreMethodResults6.cs#1)]