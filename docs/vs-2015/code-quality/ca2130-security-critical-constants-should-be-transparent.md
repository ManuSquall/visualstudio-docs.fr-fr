---
title: 'CA2130 : les constantes critiques de sécurité doivent être transparentes | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2130
ms.assetid: 344c7f7b-9130-4675-ae7f-9fa260cc9789
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e505075efc0c80f8dc4cbc43075b0bc2bc4caa1d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72643438"
---
# <a name="ca2130-security-critical-constants-should-be-transparent"></a>CA2130 : Les constantes critiques de sécurité doivent être transparentes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ConstantsShouldBeTransparent|
|CheckId|CA2130|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un champ de constante ou un membre de l’énumération est marqué avec le <xref:System.Security.SecurityCriticalAttribute>.

## <a name="rule-description"></a>Description de la règle
 La mise en application de la transparence n’est pas effectuée pour les valeurs de constante car les compilateurs alignent les valeurs de constante afin qu’aucune recherche ne soit requise au moment de l’exécution. Les champs constants doivent être transparents de sécurité (security-transparent) afin que les relecteurs de code ne supposent pas que le code transparent ne peut pas accéder à la constante.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, supprimez l’attribut SecurityCritical du champ ou de la valeur.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 Dans les exemples suivants, la valeur d’énumération `EnumWithCriticalValues.CriticalEnumValue` et la constante `CriticalConstant` déclenchent cet avertissement. Pour résoudre les problèmes, supprimez l’attribut [`SecurityCritical`] afin de le rendre transparent de sécurité.

 [!code-csharp[FxCop.Security.CA2130.ConstantsShouldBeTransparent#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2130.constantsshouldbetransparent/cs/ca2130 - constantsshouldbetransparent.cs#1)]
