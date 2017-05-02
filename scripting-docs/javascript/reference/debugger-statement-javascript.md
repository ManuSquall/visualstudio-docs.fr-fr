---
title: "debugger, instruction (JavaScript) | Microsoft Docs"
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
  - "debugger_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "debugger (instruction)"
ms.assetid: c6d2e193-c1f7-4fb3-8a4e-cc9823174ae4
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# debugger, instruction (JavaScript)
Interrompt l'exécution.  
  
## Syntaxe  
  
```  
debugger  
```  
  
## Notes  
 Placez des instructions `debugger` n'importe où dans les procédures afin d'en interrompre l'exécution.  Utiliser l'instruction `debugger` revient à placer un point d'arrêt dans le code.  
  
 L'instruction `debugger` interrompt l'exécution, mais elle ne ferme aucun fichier et n'efface aucune variable.  
  
> [!NOTE]
>  L'instruction `debugger` n'a aucun effet sauf si le script est en cours de débogage.  
  
## Exemple  
 Cet exemple utilise l'instruction `debugger` pour interrompre l'exécution à chaque itération de la boucle `for`.  
  
> [!NOTE]
>  Pour la mise en pratique de cet exemple, vous devez installer un débogueur de script et le script doit s'exécuter en mode débogage.  
>   
>  Le débogueur [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] est inclus dans Internet Explorer 8.0.  Si vous utilisez une version antérieure d'Internet Explorer, consultez la rubrique [Comment : activer et lancer le débogage de script à partir d'Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
```javascript  
for(i = 1; i<5; i++) {  
   // Print i to the Output window.  
   Debug.write("loop index is " + i);  
   // Wait for user to resume.  
   debugger  
}  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## Voir aussi  
 [JavaScript, instructions](../../javascript/reference/javascript-statements.md)   
 [Compilation conditionnelle](../../javascript/advanced/conditional-compilation-javascript.md)