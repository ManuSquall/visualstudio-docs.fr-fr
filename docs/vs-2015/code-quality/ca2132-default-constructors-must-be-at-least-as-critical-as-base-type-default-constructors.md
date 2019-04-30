---
title: 'CA2132 : Les constructeurs par défaut doivent être au moins aussi critiques que les constructeurs par défaut de type de base | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2132
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8287fdf4c767e6fc2a41f014f724ab9a7fe61249
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63385829"
---
# <a name="ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors"></a>CA2132 : Les constructeurs par défaut doivent être au moins aussi critiques que les constructeurs par défaut de type de base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DefaultConstructorsMustHaveConsistentTransparency|
|CheckId|CA2132|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

> [!NOTE]
> Cet avertissement est appliqué uniquement au code qui est en cours d’exécution CoreCLR (la version du CLR qui est spécifique aux applications Silverlight Web).

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
