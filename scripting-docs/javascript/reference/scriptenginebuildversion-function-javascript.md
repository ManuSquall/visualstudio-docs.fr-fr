---
title: "ScriptEngineBuildVersion, fonction (JavaScript) | Microsoft Docs"
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
  - "ScriptEngineBuildVersion"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ScriptEngineBuildVersion (fonction)"
ms.assetid: 7e255030-b0a3-420b-9c96-bb3e93c9333f
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# ScriptEngineBuildVersion, fonction (JavaScript)
Obtient le numéro de version du moteur de script employé.  
  
## Syntaxe  
  
```  
ScriptEngineBuildVersion()  
```  
  
## Notes  
 La valeur de retour correspond directement aux informations de version contenues dans la bibliothèque de liens dynamiques \(DLL\) du langage de script utilisé.  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de la fonction `ScriptEngineBuildVersion` :  
  
```javascript  
if(window.ScriptEngineBuildVersion) {  
    console.log(window.ScriptEngineBuildVersion());  
}  
  
// Output: <current build version>  
```  
  
## Configuration requise  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## Voir aussi  
 [ScriptEngine, fonction](../../javascript/reference/scriptengine-function-javascript.md)   
 [ScriptEngineMajorVersion, fonction](../../javascript/reference/scriptenginemajorversion-function-javascript.md)   
 [ScriptEngineMinorVersion, fonction](../../javascript/reference/scriptengineminorversion-function-javascript.md)