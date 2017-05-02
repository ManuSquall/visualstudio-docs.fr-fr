---
title: "toString, m&#233;thode (Date) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: d3037289-d805-409b-8781-045c59a2c404
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# toString, m&#233;thode (Date)
Retourne une représentation d'une date sous forme de chaîne.  Le format de la chaîne dépend des paramètres régionaux.  Pour l'anglais.. américain \(en\-us\), le format est le suivant :  
  
 *jour de la semaine* *mois* *jour* *heure* : *min* :*deuxième* *fuseau horaire* *année*  
  
## Syntaxe  
  
```  
  
date.toString()  
```  
  
## Paramètres  
 `date`  
 Requis.  La date à représenter sous forme de chaîne.  
  
## Valeur de retour  
 Retourne la représentation de la date sous forme de chaîne.  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de la méthode `toString` avec une date.  
  
```javascript  
var myDate = new Date();  
myDate.setFullYear(2100, 5, 5);  
var dateString = myDate.toString();  
document.write(dateString);  
  
// Output: <date>  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]