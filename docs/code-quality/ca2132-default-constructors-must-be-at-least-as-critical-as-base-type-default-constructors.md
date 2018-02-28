---
title: "CA2132 : Les constructeurs par défaut doivent être au moins aussi critiques que les constructeurs par défaut de type de base | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2132
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 752103825a25c4352ccc21730b8d2b7265f8f41b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors"></a>CA2132 : Les constructeurs par défaut doivent être au moins aussi critiques que les constructeurs par défaut de type de base
|||  
|-|-|  
|TypeName|DefaultConstructorsMustHaveConsistentTransparency|  
|CheckId|CA2132|  
|Category|Microsoft.Security|  
|Modification avec rupture|Rupture|  
  
> [!NOTE]
>  Cet avertissement est appliqué uniquement au code qui est en cours d’exécution (la version du CLR qui est spécifique aux applications Silverlight Web) CoreCLR.  
  
## <a name="cause"></a>Cause  
 L’attribut de transparence du constructeur par défaut d’une classe dérivée n’est pas aussi critique que la transparence de la classe de base.  
  
## <a name="rule-description"></a>Description de la règle  
 Types et membres qui ont le <xref:System.Security.SecurityCriticalAttribute> ne peut pas être utilisé par le code d’application Silverlight. Les types et membres critiques de sécurité (security-critical) peuvent être uniquement utilisés par le code de confiance dans la bibliothèque de classes .NET Framework pour Silverlight. Dans la mesure où une construction publique ou protégée dans une classe dérivée doit avoir la même transparence ou une transparence supérieure à sa classe de base, une classe dans une application ne peut pas être dérivée d’une classe marquée SecurityCritical.  
  
 Pour le code de plateforme CoreCLR, si un type de base a un constructeur public ou protégé non transparent par défaut puis le type dérivé doit respecter les règles d’héritage du constructeur par défaut. Le type dérivé doit avoir également un constructeur par défaut, et ce constructeur doit être au moins au constructeur par défaut critique du type de base.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger la violation, supprimez le type ou ne dérivent pas de type non transparent de sécurité.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle. Les violations de cette règle par le code d’application provoquent le refus de CoreCLR de charger le type avec un <xref:System.TypeLoadException>.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors_1.cs)]  
  
### <a name="comments"></a>Commentaires