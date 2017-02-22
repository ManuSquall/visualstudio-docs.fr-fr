---
title: "CA1900&#160;: Les champs de type valeur doivent &#234;tre portables | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1900"
  - "ValueTypeFieldsShouldBePortable"
helpviewer_keywords: 
  - "ValueTypeFieldsShouldBePortable"
  - "CA1900"
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1900&#160;: Les champs de type valeur doivent &#234;tre portables
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ValueTypeFieldsShouldBePortable|  
|CheckId|CA1900|  
|Catégorie|Microsoft.Portability|  
|Modification avec rupture|Avec rupture \- Si le champ est visible à l'extérieur de l'assembly.<br /><br /> Sans rupture \- Si le champ n'est pas visible à l'extérieur de l'assembly.|  
  
## Cause  
 Cette règle vérifie que les structures déclarées avec une disposition explicite s'aligneront correctement lorsqu'elles seront marshalées pour le code non managé sur les systèmes d'exploitation 64 bits.  IA\-64 n'autorise pas les accès mémoire non alignés et le processus se bloquera si cette violation n'est pas corrigée.  
  
## Description de la règle  
 Les structures qui ont une topologie explicite qui contient des champs mal alignés provoquent des incidents sur les plateformes 64 bits.  
  
## Comment corriger les violations  
 Tous les champs qui sont plus petits que 8 octets doivent avoir des offsets qui sont multiples de leur taille, et les champs qui sont supérieurs ou égaux à 8 octets doivent avoir des offsets qui sont un multiple de 8.  Une autre solution est d'utiliser `LayoutKind.Sequential` au lieu de `LayoutKind.Explicit`, si raisonnable.  
  
## Quand supprimer les avertissements  
 Cet avertissement doit être supprimé uniquement s'il se produit par erreur.