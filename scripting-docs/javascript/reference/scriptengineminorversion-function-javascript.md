---
title: "ScriptEngineMinorVersion, fonction (JavaScript) | Microsoft Docs"
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
  - "ScriptEngineMinorVersion"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ScriptEngineMinorVersion (fonction)"
ms.assetid: caa506a5-e61d-4b2a-8b83-83d56a2f26cd
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# ScriptEngineMinorVersion, fonction (JavaScript)
Obtient le numéro de version secondaire du moteur de script employé.  
  
## Syntaxe  
  
```  
ScriptEngineMinorVersion()  
```  
  
## Notes  
 La valeur de retour correspond directement aux informations de version contenues dans la bibliothèque de liens dynamiques \(DLL\) du langage de script utilisé.  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de la fonction `ScriptEngineMinorVersion`.  
  
```javascript  
if (window.ScriptEngineMinorVersion) {  
    console.log(window.ScriptEngineMinorVersion());  
}  
  
//Output: <current minor version>  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## Voir aussi  
 [ScriptEngine, fonction](../../javascript/reference/scriptengine-function-javascript.md)   
 [ScriptEngineBuildVersion, fonction](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [ScriptEngineMajorVersion, fonction](../../javascript/reference/scriptenginemajorversion-function-javascript.md)