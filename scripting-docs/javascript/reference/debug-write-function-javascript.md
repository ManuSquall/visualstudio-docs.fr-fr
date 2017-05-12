---
title: "Debug.write, fonction (JavaScript) | Microsoft Docs"
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
  - "Write"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "write (méthode) (JavaScript)"
ms.assetid: fd1cfbb3-46cb-47cc-896c-a70d457dd413
caps.latest.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 22
---
# Debug.write, fonction (JavaScript)
Envoie des chaînes au débogueur de script.  
  
## Syntaxe  
  
```  
  
Debug.write([str1 [, str2 [, ... [, strN]]]])  
```  
  
## Paramètres  
 *str1, str2, ... , strN*  
 Facultatif.  Chaînes à envoyer au débogueur de script.  
  
## Notes  
 La fonction `Debug.write` envoie des chaînes à la fenêtre Exécution d'un débogueur de script au moment de l'exécution.  Si le script n'est pas en cours de débogage, la fonction `Debug.write` est sans effet.  
  
 La fonction `Debug.write` est presque identique à la fonction `Debug.writeln`.  La seule différence est que la fonction `Debug.writeln` envoie un caractère de saut de ligne après l'envoi des chaînes.  
  
## Exemple  
 Cet exemple utilise la fonction `Debug.write` pour afficher la valeur de la variable dans la fenêtre Exécution du débogueur de script.  
  
> [!NOTE]
>  Pour la mise en pratique de cet exemple, vous devez installer un débogueur de script et le script doit s'exécuter en mode débogage.  
>   
>  Le débogueur [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] est inclus dans Internet Explorer 8.0.  Si vous utilisez une version antérieure d'Internet Explorer, consultez la rubrique [Comment : activer et lancer le débogage de script à partir d'Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
```javascript  
var counter = 42;  
Debug.write("The value of counter is " + counter);  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à** : [Objet Debug](../../javascript/reference/debug-object-javascript.md)  
  
## Voir aussi  
 [Debug.writeln, fonction](../../javascript/reference/debug-writeln-function-javascript.md)