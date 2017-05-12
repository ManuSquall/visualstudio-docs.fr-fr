---
title: "ScriptEngineMajorVersion, fonction (JavaScript) | Microsoft Docs"
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
  - "ScriptEngineMajorVersion"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ScriptEngineMajorVersion (fonction)"
ms.assetid: 3e251bce-1e14-4cb5-b79f-53845d1920fd
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# ScriptEngineMajorVersion, fonction (JavaScript)
Obtient le numéro de version principale du moteur de script employé.  
  
## Syntaxe  
  
```  
ScriptEngineMajorVersion()  
```  
  
## Notes  
 La valeur de retour correspond directement aux informations de version contenues dans la bibliothèque de liens dynamiques \(DLL\) du langage de script utilisé.  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de la fonction `ScriptEngineMajorVersion` :  
  
```javascript  
if (window.ScriptEngineMajorVersion) {  
    console.log(window.ScriptEngine());   
}  
  
Output: <current major version>  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## Voir aussi  
 [ScriptEngine, fonction](../../javascript/reference/scriptengine-function-javascript.md)   
 [ScriptEngineBuildVersion, fonction](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [ScriptEngineMinorVersion, fonction](../../javascript/reference/scriptengineminorversion-function-javascript.md)