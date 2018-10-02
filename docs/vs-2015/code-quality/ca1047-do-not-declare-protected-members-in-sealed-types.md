---
title: 'CA1047 : Ne déclarez pas des membres protégés dans les types sealed | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DoNotDeclareProtectedMembersInSealedTypes
- CA1047
helpviewer_keywords:
- CA1047
- DoNotDeclareProtectedMembersInSealedTypes
ms.assetid: 829033b5-a9d8-4f26-a719-45494c9dd035
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8a9c61d3910a550f957b9940c1280f4fd2c17bdc
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588134"
---
# <a name="ca1047-do-not-declare-protected-members-in-sealed-types"></a>CA1047 : Ne pas déclarer les membres protégés dans les types sealed
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA1047 : ne déclarez pas de membres protégés dans les types sealed](https://docs.microsoft.com/visualstudio/code-quality/ca1047-do-not-declare-protected-members-in-sealed-types).

|||
|-|-|
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|
|CheckId|CA1047|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Est un type public `sealed` (`NotInheritable` en Visual basic) et déclare un membre protégé ou un type imbriqué protégé. Cette règle ne signale pas de violations pour <xref:System.Object.Finalize%2A> méthodes, qui doivent respecter ce modèle.

## <a name="rule-description"></a>Description de la règle
 Les types déclarent des membres protégés afin que des types qui héritent puissent accéder au membre ou le substituer. Par définition, vous ne peut pas hériter d’un type sealed, ce qui signifie que protégés des méthodes sur les types sealed ne peut pas être appelée.

 Le compilateur c# émet un avertissement pour cette erreur.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, modifier le niveau d’accès du membre privé ou rendez le type héritable.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle. Laisser le type dans son état actuel peut entraîner des problèmes de maintenance et ne fournit pas d’avantages.

## <a name="example"></a>Exemple
 L’exemple suivant illustre un type qui enfreint cette règle.

 [!code-csharp[FxCop.Design.SealedNoProtected#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.SealedNoProtected/cs/FxCop.Design.SealedNoProtected.cs#1)]
 [!code-vb[FxCop.Design.SealedNoProtected#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.SealedNoProtected/vb/FxCop.Design.SealedNoProtected.vb#1)]



