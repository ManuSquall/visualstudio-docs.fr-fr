---
title: "CA2106 : Assertions s&#233;curis&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2106"
  - "SecureAsserts"
helpviewer_keywords: 
  - "CA2106"
  - "SecureAsserts"
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2106 : Assertions s&#233;curis&#233;es
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SecureAsserts|  
|CheckId|CA2106|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Oui|  
  
## Cause  
 Une méthode déclare une autorisation et aucune vérification de sécurité n'est exécutée sur l'appelant.  
  
## Description de la règle  
 L'assertion d'une autorisation de sécurité effectuée sans vérification de sécurité peut rendre votre code vulnérable et facile à exploiter.  Un parcours de pile de la sécurité s'arrête lorsqu'une autorisation de sécurité est déclarée.  Si vous déclarez une autorisation sans soumettre l'appelant à aucune vérification, celui\-ci pourrait exécuter indirectement le code en se servant de vos autorisations.  Les assertions sans vérification de la sécurité sont autorisées seulement quand vous êtes sûrs que l'assertion ne peut pas être utilisée de façon préjudiciable.  Une assertion ne peut pas nuire si le code que vous appelez ne présente aucun danger ou que les utilisateurs ne peuvent pas transmettre des informations arbitraires au code que vous appelez.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, ajoutez une demande de sécurité à la méthode ou à son type déclarant.  
  
## Quand supprimer les avertissements  
 Supprimez un avertissement de cette règle uniquement après un examen minutieux de la sécurité.  
  
## Voir aussi  
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>   
 [Instructions de codage sécurisé](../Topic/Secure%20Coding%20Guidelines.md)