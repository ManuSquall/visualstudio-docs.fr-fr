---
title: "Debug, objet (JavaScript) | Microsoft Docs"
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
  - "debug"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "objet Debug"
  - "Debug (objet), à propos de l’objet Debug"
ms.assetid: 42a367ec-beb1-4e59-8342-34c326eca042
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Debug, objet (JavaScript)
Un objet global intrinsèque qui envoie la sortie vers un débogueur.  
  
## Syntaxe  
  
```  
Debug.function  
```  
  
## Notes  
 Vous n’instanciez pas l’objet Debug. Vous pouvez accéder à toutes ses propriétés et méthodes en appelant `function`.  
  
 Il existe différentes façons de déboguer les applications Internet Explorer et [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. Dans les applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)], les fonctions `write` et `writeln` de l’objet `Debug` affichent des chaînes dans la fenêtre **Sortie** de Visual Studio lors de l’exécution. Pour plus d’informations sur le débogage des applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)], consultez [Déboguer des applications dans Visual Studio](~/debugger/debug-store-apps-in-visual-studio.md).  
  
 Pour déboguer des scripts Internet Explorer, vous devez disposer d’un débogueur de script installé et le script doit être exécuté en mode débogage. Internet Explorer 8 et ses versions ultérieures incluent le débogueur [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Si vous utilisez une version antérieure d’Internet Explorer, consultez [Procédure : activation et démarrage du débogage des scripts à partir d’Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
 Si le script n’est pas en cours de débogage, les fonctions n’ont aucun effet.  
  
## Exemple  
 Cet exemple utilise la fonction `write` pour afficher la valeur de la variable.  
  
```javascript  
var counter = 42; Debug.write("The value of counter is " + counter);  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## Constantes  
 [Constantes de débogage](../../javascript/reference/debug-constants.md)  
  
## Propriétés  
 [Debug.debuggerEnabled, propriété](../../javascript/reference/debug-debuggerenabled-property.md) &#124; [Debug.setNonUserCodeExceptions, propriété](../../javascript/reference/debug-setnonusercodeexceptions-property.md)  
  
## Fonctions  
 [Fonction Debug.msTraceAsyncCallbackStarting](../../javascript/reference/debug-mstraceasynccallbackstarting-function.md) &#124; [Fonction Debug.msTraceAsyncCallbackCompleted](../../javascript/reference/debug-mstraceasynccallbackcompleted-function.md) &#124; [Fonction Debug.msTraceAsyncOperationCompleted](../../javascript/reference/debug-mstraceasyncoperationcompleted-function.md) &#124; [Fonction Debug.msTraceAsyncOperationStarting](../../javascript/reference/debug-mstraceasyncoperationstarting-function.md) &#124; [Fonction Debug.msUpdateAsyncCallbackRelation](../../javascript/reference/debug-msupdateasynccallbackrelation-function.md) &#124; [Debug.write, fonction](../../javascript/reference/debug-write-function-javascript.md) &#124; [Debug.writeln, fonction](../../javascript/reference/debug-writeln-function-javascript.md)  
  
## Voir aussi  
 [debugger, instruction](../../javascript/reference/debugger-statement-javascript.md)