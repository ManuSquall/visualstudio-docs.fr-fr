---
title: "getYear, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "getYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "dates, retourner l’année"
  - "getYear (méthode)"
ms.assetid: 0e23e832-acd4-49a9-a175-515d0094f172
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# getYear, m&#233;thode (Date) (JavaScript)
Obtient l'année d'un objet d' `Date` .  
  
## Syntaxe  
  
```  
  
dateObj.getYear()   
```  
  
#### Paramètres  
 La référence requise pour `dateObj` est un objet d' `Date` .  
  
## Valeur de retour  
 Retourne l'année.  
  
## Notes  
  
> [!IMPORTANT]
>  Cette méthode est obsolète, et est fournie pour la compatibilité descendante uniquement.  Employez plutôt la méthode `getFullYear`.  
  
 Dans [!INCLUDE[jsv1textspecific](../../javascript/reference/includes/jsv1textspecific-md.md)], puis dans les versions d'Internet Explorer en commençant par [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)], la valeur retournée est l'année stockée moins 1900.  Par exemple, pour l'année 1899 la valeur retournée est \-1 et pour l'année 2000 la valeur retournée est 100.  
  
 Dans [!INCLUDE[jsv3textspecific](../../javascript/reference/includes/jsv3textspecific-md.md)] via [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)], la formule dépend de l'année.  Pendant les années 1900 jusqu'en 1999, la valeur retournée est une valeur à 2 chiffres qui est l'année stockée moins 1900.  Pour l'extérieur de dates qui s'étendent, l'année à 4 chiffres est retournée.  Par exemple, 1996 est retourné comme 96, mais 1825 et 2025 sont retournés comme est.  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Applies To**: [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [getFullYear, méthode \(Date\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear, méthode \(Date\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setFullYear, méthode \(Date\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear, méthode \(Date\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)   
 [setYear, méthode \(Date\)](../../javascript/reference/setyear-method-date-javascript.md)