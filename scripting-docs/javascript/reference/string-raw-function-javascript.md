---
title: "String.raw, fonction (JavaScript) | Microsoft Docs"
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
ms.assetid: b1038b73-3944-4645-b075-3a674b313762
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# String.raw, fonction (JavaScript)
Retourne la chaîne brute d'une chaîne modèle.  
  
## Syntaxe  
  
```  
String.raw`templateStr`;  
String.raw(obj, ...substitutions);  
```  
  
#### Paramètres  
 `templateStr`  
 Obligatoire.  Chaîne de modèle.  
  
 `obj`  
 Obligatoire.  Objet correct spécifié à l'aide de notation littérale d'objet, telle que {raw: 'value'}.  
  
 `...substitutions`  
 Facultatif.  Un tableau \([paramètre rest](../../javascript/functions-javascript.md)\) consistant en une ou plusieurs valeurs de substitution.  
  
## Notes  
 La fonction `String.raw` est destinée à être utilisée avec les [chaînes modèles](../../javascript/advanced/template-strings-javascript.md).  La chaîne brute inclut les caractères d'échappement et les barres obliques inverses qui sont présents dans la chaîne.  
  
 Une erreur est levée si `obj` n'est pas un objet bien formé.  
  
## Exemple  
  
```  
function log(arg) {  
    if(console && console.log) {  
        console.log(arg);  
    }  
};  
  
var name = "bob";  
  
log(`hello \t${name}`);  
log(String.raw`hello \t${name}`);  
// The following usage for String.raw is supported but  
// is not typical.  
log(String.raw({ raw: 'fred'}, 'F', 'R', 'E'));  
  
// Output:  
// hello   bob  
// hello \tbob  
// fFrReEd  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]