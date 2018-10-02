---
title: 'CA2130 : Les constantes critiques de sécurité doivent être transparentes | Microsoft Docs'
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
- CA2130
ms.assetid: 344c7f7b-9130-4675-ae7f-9fa260cc9789
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a74d6fe3c0507914fa4bd9723a53579db230c467
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589594"
---
# <a name="ca2130-security-critical-constants-should-be-transparent"></a>CA2130 : Les constantes critiques de sécurité doivent être transparentes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA2130 : les constantes critiques de sécurité doivent être transparentes](https://docs.microsoft.com/visualstudio/code-quality/ca2130-security-critical-constants-should-be-transparent).

|||
|-|-|
|TypeName|ConstantsShouldBeTransparent|
|CheckId|CA2130|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un champ constant ou un membre d’énumération est marqué avec le <xref:System.Security.SecurityCriticalAttribute>.

## <a name="rule-description"></a>Description de la règle
 La mise en application de la transparence n’est pas effectuée pour les valeurs de constante car les compilateurs alignent les valeurs de constante afin qu’aucune recherche ne soit requise au moment de l’exécution. Les champs constants doivent être transparents de sécurité (security-transparent) afin que les relecteurs de code ne supposent pas que le code transparent ne peut pas accéder à la constante.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, supprimez l’attribut SecurityCritical à partir du champ ou une valeur.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 Dans les exemples suivants, la valeur enum `EnumWithCriticalValues.CriticalEnumValue` et la constante `CriticalConstant` déclenchent cet avertissement. Pour corriger les problèmes, supprimez le [`SecurityCritical`] attribut pour qu’elles soient transparentes de sécurité.

 [!code-csharp[FxCop.Security.CA2130.ConstantsShouldBeTransparent#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2130.constantsshouldbetransparent/cs/ca2130 - constantsshouldbetransparent.cs#1)]



