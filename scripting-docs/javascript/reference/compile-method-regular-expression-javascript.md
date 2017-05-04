---
title: "compile, m&#233;thode (Regular Expression) (JavaScript) | Microsoft Docs"
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
  - "compile"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Compile (méthode)"
  - "compiler le code source, expressions régulières"
  - "expressions régulières, compiler"
ms.assetid: dc28cae3-478d-49b5-b5ea-203e5edfe195
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# compile, m&#233;thode (Regular Expression) (JavaScript)
Compile une expression régulière en un format interne en vue d'une exécution plus rapide.  
  
## Syntaxe  
  
```  
  
rgExp.compile(pattern, [flags])   
```  
  
## Paramètres  
 `rgExp`  
 Obligatoire.  Instance d'un objet **Regular Expression**.  Peut être un nom de variable ou un littéral.  
  
 *pattern*  
 Obligatoire.  Expression de chaîne contenant un modèle d'expression régulière à compiler.  
  
 `flags`  
 Facultatif.  Les indicateurs disponibles sont les suivants \(toute combinaison est possible\) :  
  
-   g \(recherche globale de toutes les occurrences de *pattern*\)  
  
-   i \(ignorer la casse\)  
  
-   m \(recherche multiligne\)  
  
## Notes  
 La méthode **compile** convertit le modèle *pattern* en un format interne en vue d'une exécution plus rapide.  Ceci accroît l'efficacité des expressions régulières utilisées dans les boucles, par exemple.  L'utilisation d'une expression régulière compilée permet de gagner du temps lorsque vous utilisez la même expression de manière répétée.  En revanche, cette méthode ne présente pas d'intérêt si l'expression régulière doit être modifiée.  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de la méthode **compile** :  
  
```javascript  
function CompileDemo(){  
   var rs;  
   var s = "AaBbCcDdEeFfGgHhIiJjKkLlMmNnOoPp"  
   // Create regular expression for uppercase only.  
   var r = new RegExp("[A-Z]", "g");  
   var a1 = s.match(r)              // Find matches.  
   // Compile the regular expression for lowercase only.  
   r.compile("[a-z]", "g");  
// Find matches.  
   var a2 = s.match(r)                
   return(a1 + "\n" + a2);  
}  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à** : [Objet Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)  
  
## Voir aussi  
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/fr-fr/ab0766e1-7037-45ed-aa23-706f58358c0e)