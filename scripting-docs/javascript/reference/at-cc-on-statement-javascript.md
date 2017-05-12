---
title: "@cc_on, instruction (JavaScript) | Microsoft Docs"
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
  - "@cc_on_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "@cc_on (instruction)"
  - "@if (instruction)"
  - "@set (instruction)"
  - "compilation conditionnelle, activer"
ms.assetid: fdeda7ee-b9f4-4e52-8aa2-21c90c02a332
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# @cc_on, instruction (JavaScript)
Active la prise en charge de la compilation conditionnelle dans les commentaires d'un script.  
  
> [!WARNING]
>  La compilation conditionnelle n'est prise en charge ni par le mode standard d'Internet Explorer 11, ni par les applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  La compilation conditionnelle est prise en charge par le mode standard d'Internet Explorer 10 et toutes les versions antérieures.  
  
## Syntaxe  
  
```  
@cc_on   
```  
  
## Notes  
 L'instruction `@cc_on` active la prise en charge de la compilation conditionnelle dans les commentaires d'un script.  
  
 En revanche, elles sont peu employées dans des scripts écrits pour des pages ASP ou ASP.NET, ou des programmes en ligne de commande, car les fonctionnalités des compilateurs peuvent être déterminées par d'autres méthodes.  
  
 Lorsque vous écrivez un script pour une page Web, placez toujours le code de compilation conditionnelle dans des commentaires.  Dès lors, les hôtes qui ne prennent pas en charge la compilation conditionnelle peuvent l'ignorer.  
  
 Il est fortement recommandé d'utiliser l'instruction `@cc_on` dans un commentaire, afin que les navigateurs qui ne prennent pas en charge la compilation conditionnelle acceptent votre script comme une syntaxe valide :  
  
 Une instruction `@if` ou `@set` placée en dehors d'un commentaire active également la compilation conditionnelle.  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de l'instruction `@cc_on`.  
  
```javascript  
/*@cc_on @*/  
/*@  
    document.write("JavaScript version: " + @_jscript_version + ".");  
    document.write("<br />");  
    @if (@_win32)  
        document.write("Running on the 32-bit version of Windows.");  
    @elif (@_win16)  
        document.write("Running on the 16-bit version of Windows.");  
    @else  
        document.write("Running on a different operating system.");  
    @end  
@*/  
```  
  
## Configuration requise  
 Prise en charge dans toutes les versions d'Internet Explorer, mais pas dans les applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
## Voir aussi  
 [Compilation conditionnelle](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variables de compilation conditionnelle](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@if, instruction](../../javascript/reference/at-if-statement-javascript.md)   
 [@set, instruction](../../javascript/reference/at-set-statement-javascript.md)