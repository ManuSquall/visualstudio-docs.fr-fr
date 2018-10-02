---
title: 'CA2132 : Les constructeurs par défaut doivent être au moins aussi critiques que les constructeurs par défaut de type de base | Microsoft Docs'
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
- CA2132
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ecf78792e18df4956fa0147754879fb2e80648bc
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47590311"
---
# <a name="ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors"></a>CA2132 : Les constructeurs par défaut doivent être au moins aussi critiques que les constructeurs par défaut de type de base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA2132 : les constructeurs par défaut doivent être au moins aussi critiques que les constructeurs par défaut de type de base](https://docs.microsoft.com/visualstudio/code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors).

|||
|-|-|
|TypeName|DefaultConstructorsMustHaveConsistentTransparency|
|CheckId|CA2132|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

> [!NOTE]
>  Cet avertissement est appliqué uniquement au code qui est en cours d’exécution CoreCLR (la version du CLR qui est spécifique aux applications Silverlight Web).

## <a name="cause"></a>Cause
 L’attribut de transparence du constructeur par défaut d’une classe dérivée n’est pas aussi critique que la transparence de la classe de base.

## <a name="rule-description"></a>Description de la règle
 Types et membres qui ont le <xref:System.Security.SecurityCriticalAttribute> ne peut pas être utilisé par le code d’application Silverlight. Les types et membres critiques de sécurité (security-critical) peuvent être uniquement utilisés par le code de confiance dans la bibliothèque de classes .NET Framework pour Silverlight. Dans la mesure où une construction publique ou protégée dans une classe dérivée doit avoir la même transparence ou une transparence supérieure à sa classe de base, une classe dans une application ne peut pas être dérivée d’une classe marquée SecurityCritical.

 Pour le code de plateforme CoreCLR, si un type de base a un constructeur public ou protégé non transparent par défaut puis le type dérivé doit respecter les règles d’héritage de constructeur par défaut. Le type dérivé doit également être un constructeur par défaut et ce constructeur doit être au moins en tant que constructeur critiques par défaut du type de base.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger la violation, supprimez le type ou ne dérivent pas de type non transparent de sécurité.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas les avertissements de cette règle. Les violations de cette règle par code d’application provoquent le refus de CoreCLR de charger le type avec un <xref:System.TypeLoadException>.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2132.defaultconstructorsmusthaveconsistenttransparency/cs/ca2132 - defaultconstructorsmusthaveconsistenttransparency.cs#1)]

### <a name="comments"></a>Commentaires



