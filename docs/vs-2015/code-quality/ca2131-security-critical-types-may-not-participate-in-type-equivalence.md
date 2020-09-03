---
title: 'Ca2131 : les types critiques de sécurité ne peuvent pas participer à l’équivalence des types | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2131
ms.assetid: 4170f3b1-6086-430d-8fba-837d5538c573
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ccd556a5929e56597de678ad4ad8ea6c101b7c7f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535887"
---
# <a name="ca2131-security-critical-types-may-not-participate-in-type-equivalence"></a>CA2131 : Les types critiques de sécurité ne peuvent pas participer à l'équivalence des types
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|CriticalTypesMustNotParticipateInTypeEquivalence|
|CheckId|CA2131|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause :
 Un type participe à l’équivalence de type et un type lui-même, ou un membre ou champ du type, est marqué avec l' <xref:System.Security.SecurityCriticalAttribute> attribut.

## <a name="rule-description"></a>Description de la règle
 Cette règle se déclenche sur tout type ou type critique contenant des méthodes critiques ou des champs qui participent à l’équivalence de type. Lorsque le CLR détecte un tel type, il ne peut pas le charger avec un <xref:System.TypeLoadException> au moment de l’exécution. En général, cette règle se déclenche uniquement lorsque les utilisateurs implémentent l’équivalence de type manuellement plutôt qu’en comptant sur tlbimp et les compilateurs pour faire l’équivalence de type.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, supprimez l’attribut SecurityCritical.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 Les exemples suivants illustrent une interface, une méthode et un champ qui entraîne le déclenchement de cette règle.

 [!code-csharp[FxCop.Security.CA2131.CriticalTypesMustNotParticipateInTypeEquivalence#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2131.criticaltypesmustnotparticipateintypeequivalence/cs/ca2131 - criticaltypesmustnotparticipateintypeequivalence.cs#1)]

## <a name="see-also"></a>Voir aussi
 [Code transparent de sécurité, niveau 2](https://msdn.microsoft.com/library/4d05610a-0da6-4f08-acea-d54c9d6143c0)
