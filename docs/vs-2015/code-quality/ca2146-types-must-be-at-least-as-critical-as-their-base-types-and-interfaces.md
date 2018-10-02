---
title: 'CA2146 : Les Types doivent être au moins aussi critiques que leurs types de base et les interfaces | Microsoft Docs'
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
- CA2146
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 09b6c1ca57582ee17f048220bbb73f7605883df7
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589663"
---
# <a name="ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces"></a>CA2146 : Les types doivent être au moins aussi critiques que les types de base et les interfaces
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA2146 : les Types doivent être au moins aussi critiques que leurs types de base et les interfaces](https://docs.microsoft.com/visualstudio/code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces).

|||
|-|-|
|TypeName|TypesMustBeAtLeastAsCriticalAsBaseTypes|
|CheckId|CA2146|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type transparent est dérivé d’un type qui est marqué avec le <xref:System.Security.SecuritySafeCriticalAttribute> ou <xref:System.Security.SecurityCriticalAttribute>, ou un type qui est marqué avec le <xref:System.Security.SecuritySafeCriticalAttribute> attribut est dérivé d’un type qui est marqué avec le <xref:System.Security.SecurityCriticalAttribute> attribut.

## <a name="rule-description"></a>Description de la règle
 Cette règle se déclenche lorsqu’un type dérivé a un attribut de transparence de sécurité qui n’est pas aussi critique que son type de base ou l’interface implémentée. Seuls les types critiques peuvent dériver des types de base critiques ou implémenter des interfaces critiques, et seuls les types critiques ou critiques sécurisés peuvent dériver des types de base critiques sécurisés ou implémenter des interfaces critiques sécurisées. Les violations de cette règle dans la transparence de niveau 2 provoquent un <xref:System.TypeLoadException> pour le type dérivé.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour résoudre cette violation, marquez le type dérivé ou d’implémentation avec un attribut de transparence est au moins aussi critique que le type de base ou interface.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 [!code-csharp[FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2146.typesmustbeatleastascriticalasbasetypes/cs/ca2146 - typesmustbeatleastascriticalasbasetypes.cs#1)]



