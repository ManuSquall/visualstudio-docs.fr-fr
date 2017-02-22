---
title: "CA2132&#160;: Les constructeurs par d&#233;faut doivent &#234;tre au moins aussi critiques que les constructeurs par d&#233;faut de type de base | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2132"
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2132&#160;: Les constructeurs par d&#233;faut doivent &#234;tre au moins aussi critiques que les constructeurs par d&#233;faut de type de base
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DefaultConstructorsMustHaveConsistentTransparency|  
|CheckId|CA2132|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Oui|  
  
> [!NOTE]
>  Cet avertissement est appliqué uniquement au code exécutant CoreCLR \(version du CLR qui est spécifique aux applications Web Silverlight\).  
  
## Cause  
 L'attribut de transparence du constructeur par défaut d'une classe dérivée n'est pas aussi critique que la transparence de la classe de base.  
  
## Description de la règle  
 Les types et les membres qui possèdent <xref:System.Security.SecurityCriticalAttribute> ne peuvent pas être utilisés par le code d'application Silverlight.  Les types et membres critiques de sécurité \(security\-critical\) peuvent être uniquement utilisés par le code de confiance dans la bibliothèque de classes .NET Framework pour Silverlight.  Dans la mesure où une construction publique ou protégée dans une classe dérivée doit avoir la même transparence ou une transparence supérieure à sa classe de base, une classe dans une application ne peut pas être dérivée d'une classe marquée SecurityCritical.  
  
 Pour le code de plateforme CoreCLR, si un type de base a ensuite un constructeur par défaut opaque protégé ou public le type dérivé doit obéir aux règles de l'héritage du constructeur par défaut.  Le type dérivé doit également avoir un constructeur par défaut et ce constructeur doit être au moins aussi critique que le constructeur par défaut du type de base.  
  
## Comment corriger les violations  
 Pour résoudre la violation, supprimez le type ou n'effectuez pas de dérivation à partir du type non transparent de sécurité.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  Les violations de cette règle par le code d'application provoquent le refus de CoreCLR de charger le type avec une <xref:System.TypeLoadException>.  
  
### Code  
 [!CODE [FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../CodeSnippet/VS_Snippets_CodeAnalysis/fxcop.security.ca2132.defaultconstructorsmusthaveconsistenttransparency#1)]  
  
### Commentaires