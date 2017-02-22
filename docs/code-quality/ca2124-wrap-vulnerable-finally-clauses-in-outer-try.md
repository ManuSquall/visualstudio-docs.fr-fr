---
title: "CA2124&#160;: Incluez dans un wrapper les clauses finally vuln&#233;rables dans un bloc try externe | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2124"
  - "WrapVulnerableFinallyClausesInOuterTry"
helpviewer_keywords: 
  - "CA2124"
  - "WrapVulnerableFinallyClausesInOuterTry"
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 20
---
# CA2124&#160;: Incluez dans un wrapper les clauses finally vuln&#233;rables dans un bloc try externe
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|WrapVulnerableFinallyClausesInOuterTry|  
|CheckId|CA2124|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Dans les versions 1.0 et 1.1 de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], une méthode publique ou protégée contient un bloc `try`\/`catch`\/`finally`.  Le bloc `finally` semble réinitialiser l'état de sécurité et n'est intégré à aucun bloc `finally`.  
  
## Description de la règle  
 Cette règle localise des blocs `try`\/`finally` dans le code qui cible les versions 1.0 et 1.1 de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] susceptibles de présenter une vulnérabilité aux filtres d'exception malveillants présents dans la pile des appels.  Si des opérations sensibles, telles que l'emprunt d'identité, se produisent dans le bloc try et qu'une exception est levée, le filtre peut s'exécuter avant le bloc `finally`.  Pour l'exemple d'emprunt d'identité, cela signifie que le filtre s'exécuterait comme l'utilisateur personnifié.  Actuellement, les filtres sont uniquement applicables en Visual Basic.  
  
> [!WARNING]
>  **Remarque** Dans les versions 2.0 et ultérieures de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], le runtime protège automatiquement un bloc `try`\/`catch`\/ `finally` contre des filtres d'exceptions malveillants, si la réinitialisation se produit directement dans la méthode qui contient le bloc d'exception.  
  
## Comment corriger les violations  
 Placez le bloc `try`\/`finally` désencapsulé dans un bloc try externe.  Consultez le deuxième exemple qui suit.  Cela force l'exécution du bloc `finally` avant le code de filtre.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Exemple de pseudo\-code  
  
### Description  
 Le pseudo\-code suivant illustre le schéma détecté par cette règle.  
  
### Code  
  
```  
try {  
   // Do some work.  
   Impersonator imp = new Impersonator("John Doe");  
   imp.AddToCreditCardBalance(100);  
}  
finally {  
   // Reset security state.  
   imp.Revert();  
}  
```  
  
## Exemple  
 Le pseudo\-code suivant illustre le schéma que vous pouvez utiliser pour protéger votre code et satisfaire cette règle.  
  
```  
try {  
     try {  
        // Do some work.  
     }  
     finally {  
        // Reset security state.  
     }  
}  
catch()  
{  
    throw;  
}  
```