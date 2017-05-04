---
title: "trim, m&#233;thode (String) (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "trim (méthode)"
ms.assetid: 03d38c7e-25cd-4ede-b58e-1a10b5249bab
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# trim, m&#233;thode (String) (JavaScript)
Supprime les espaces blancs de début et de fin ainsi que les marques de fin de ligne d'une chaîne.  
  
## Syntaxe  
  
```  
  
stringObj.trim()  
```  
  
## Paramètres  
 `stringObj`  
 Obligatoire.  Objet `String` ou littéral de chaîne.  Cette chaîne n'est pas modifiée par la méthode `trim`.  
  
## Valeur de retour  
 Chaîne d'origine dans laquelle les espaces blancs de début et de fin et les caractères de fin de ligne sont supprimés.  
  
## Notes  
 Les caractères supprimés comprennent l'espace, la tabulation, le saut de page, le retour chariot et le saut de ligne.  Consultez [Caractères spéciaux](../../javascript/advanced/special-characters-javascript.md) pour obtenir la liste complète des espaces blancs et des caractères de fin de ligne.  
  
 Pour obtenir un exemple qui indique comment implémenter votre propre méthode Trim, consultez [Prototypes et héritage de prototypes](../../javascript/advanced/prototypes-and-prototype-inheritance.md).  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `trim`.  
  
```javascript  
var message = "    abc def     \r\n  ";  
  
document.write("[" + message.trim() + "]");  
document.write("<br/>");  
document.write("length: " + message.trim().length);  
  
// Output:  
//  [abc def]  
//  length: 7  
```  
  
## Configuration requise  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Voir aussi  
 [Caractères spéciaux](../../javascript/advanced/special-characters-javascript.md)   
 [String, objet](../../javascript/reference/string-object-javascript.md)   
 [Défilement, panoramique et zoom d'exemple d'application](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)