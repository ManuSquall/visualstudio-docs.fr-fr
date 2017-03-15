---
title: "CA1725&#160;: Les noms de param&#232;tres doivent correspondre &#224; la d&#233;claration de base | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ParameterNamesShouldMatchBaseDeclaration"
  - "CA1725"
helpviewer_keywords: 
  - "CA1725"
  - "ParameterNamesShouldMatchBaseDeclaration"
ms.assetid: 9b657ab0-fe81-4f4c-9481-ba746988c922
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA1725&#160;: Les noms de param&#232;tres doivent correspondre &#224; la d&#233;claration de base
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ParameterNamesShouldMatchBaseDeclaration|  
|CheckId|CA1725|  
|Catégorie|Microsoft.Naming|  
|Modification avec rupture|Oui|  
  
## Cause  
 Le nom d'un paramètre dans une substitution de méthode visible de l'extérieur ne correspond pas au nom du paramètre dans la déclaration de base de la méthode ou au nom du paramètre dans la déclaration d'interface de la méthode.  
  
## Description de la règle  
 La désignation cohérente des paramètres dans une hiérarchie de substitution augmente la facilité d'utilisation des substitutions de méthode.  Un nom de paramètre dans une méthode dérivée qui diffère du nom dans la déclaration de base peut créer une confusion pour déterminer si la méthode est une substitution de la méthode de base ou une nouvelle surcharge de la méthode.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, renommez le paramètre pour correspondre à la déclaration de base.  Le correctif est une modification avec rupture pour les méthodes visibles par COM.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle, sauf pour les méthodes visibles par COM dans les bibliothèques fournies antérieurement.