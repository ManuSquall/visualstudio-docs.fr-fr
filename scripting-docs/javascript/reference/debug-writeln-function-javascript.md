---
title: "Debug.writeln, fonction (JavaScript) | Microsoft Docs"
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
  - "writeln"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "writeIn (méthode)"
ms.assetid: c3aad0cd-0486-4161-9ba6-31d672da72af
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Debug.writeln, fonction (JavaScript)
Envoie des chaînes, suivies par un caractère de saut de ligne, au débogueur de script.  
  
## Syntaxe  
  
```  
  
Debug.writeln([str1 [, str2 [, ... [, strN]]]])  
```  
  
## Paramètres  
 *str1, str2, ... , strN*  
 Facultatif.  Chaînes à envoyer au débogueur de script.  
  
## Notes  
 La fonction `Debug.writeln` envoie des chaînes, suivies d'un caractère de saut de ligne, dans la fenêtre Exécution du Débogueur Microsoft Script au moment de l'exécution.  Si le script n'est pas en cours de débogage, la fonction `Debug.writeln` est sans effet.  
  
 La fonction `Debug.writeln` est presque identique à la fonction `Debug.write`.  La seule différence est que la fonction `Debug.write` n'envoie pas de caractère de saut de ligne après avoir envoyé les chaînes.  
  
## Exemple  
 Cet exemple utilise la fonction `Debug.writeln` pour afficher la valeur de la variable dans la fenêtre Exécution du Débogueur Microsoft Script.  
  
> [!NOTE]
>  Pour la mise en pratique de cet exemple, vous devez installer un débogueur de script et le script doit s'exécuter en mode débogage.  
>   
>  Le débogueur [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] est inclus dans Internet Explorer 8.0.  Si vous utilisez une version antérieure d'Internet Explorer, consultez la rubrique [Comment : activer et lancer le débogage de script à partir d'Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
```javascript  
var counter = 42;  
Debug.writeln("The value of counter is " + counter);  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à** : [Objet Debug](../../javascript/reference/debug-object-javascript.md)  
  
## Voir aussi  
 [Debug.write, fonction](../../javascript/reference/debug-write-function-javascript.md)