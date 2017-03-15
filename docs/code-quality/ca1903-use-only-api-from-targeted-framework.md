---
title: "CA1903&#160;: Utiliser uniquement l&#39;API &#224; partir du Framework cible | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UseOnlyAPIFromTargetedFramework"
  - "CA1903"
helpviewer_keywords: 
  - "CA1903"
  - "UseOnlyApiFromTargetedFramework"
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 8
---
# CA1903&#160;: Utiliser uniquement l&#39;API &#224; partir du Framework cible
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseOnlyApiFromTargetedFramework|  
|CheckId|CA1903|  
|Catégorie|Microsoft.Portability|  
|Modification avec rupture|Avec rupture – En cas de déclenchement sur la signature d'un type ou d'un membre visible de l'extérieur.<br /><br /> Sans rupture – En cas de déclenchement sur le corps d'une méthode.|  
  
## Cause  
 Un membre ou un type utilise un membre ou un type qui a été introduit dans un Service Pack qui ne figurait pas dans le Framework cible du projet.  
  
## Description de la règle  
 De nouveaux membres et types ont été inclus dans .NET Framework 2.0 Service Pack 1 et 2, .NET Framework 3.0 Service Pack 1 et 2 et .NET Framework 3.5 Service Pack 1.  Les projets qui ciblent les versions principales du .NET Framework peuvent involontairement prendre des dépendances sur ces nouvelles API.  Pour empêcher toute dépendance, cette règle se déclenche en cas d'utilisation de nouveaux membres et types qui ne figurent pas par défaut dans la version cible de .Net Framework pour le projet.  
  
 **Version cible de .Net Framework et dépendances par rapport au Service Pack**  
  
|||  
|-|-|  
|Lorsque la version cible de .Net Framework est|Se déclenche en cas d'utilisation de membres introduits dans|  
|.NET Framework 2.0|.NET Framework 2.0 SP1, .NET Framework 2.0 SP2|  
|.NET Framework 3.0|.NET Framework 2.0 SP1, .NET Framework 2.0 SP2, .NET Framework 3.0 SP1, .NET Framework 3.0 SP2|  
|.NET Framework 3.5|.NET Framework 3.5 SP1|  
|.NET Framework 4|N\/A|  
  
 Pour modifier la version cible de .Net Framework d'un projet, consultez [Cibler une version spécifique du .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).  
  
## Comment corriger les violations  
 Pour supprimer la dépendance par rapport au Service Pack, supprimez toute utilisation du nouveau membre ou type.  S'il s'agit d'une dépendance délibérée, supprimez l'avertissement ou désactivez cette règle.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle lorsqu'il ne s'agit pas d'une dépendance délibérée par rapport au Service Pack spécifié.  Sinon, votre application risque de ne pas s'exécuter sur les systèmes si ce Service Pack n'y est pas installé.  Supprimez l'avertissement ou désactivez cette règle lorsqu'il s'agit d'une dépendance délibérée.  
  
## Exemple  
 L'exemple suivant affiche une classe qui utilise le type DateTimeOffset qui est uniquement disponible dans .NET 2.0 Service Pack 1.  Cet exemple requiert que .NET Framework 2.0 ait été sélectionné dans la liste déroulante Infrastructure cible dans les propriétés Projet.  
  
 [!code-cs[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_1.cs)]  
  
## Exemple  
 L'exemple suivant corrige la violation précédemment décrite en remplaçant les utilisations du type DateTimeOffset par le type DateTime.  
  
 [!code-cs[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_2.cs)]  
  
## Voir aussi  
 [Avertissements liés à la portabilité](../code-quality/portability-warnings.md)   
 [Cibler une version spécifique du .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)