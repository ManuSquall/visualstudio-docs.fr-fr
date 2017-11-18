---
title: Debug, objet (JavaScript) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: debug
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Debug object
- Debug object, about Debug object
ms.assetid: 42a367ec-beb1-4e59-8342-34c326eca042
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6286e5db853daa97e43f36a1467abe90cbced5c8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="debug-object-javascript"></a>Debug, objet (JavaScript)
Un objet global intrinsèque qui envoie la sortie vers un débogueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Debug.function  
```  
  
## <a name="remarks"></a>Remarques  
 Vous n’instanciez pas l’objet Debug. Vous pouvez accéder à toutes ses propriétés et méthodes en appelant `function`.  
  
 Il existe différentes façons de déboguer les applications Internet Explorer et [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] . Dans les applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] , les fonctions `write` et `writeln` de l’objet `Debug` affichent des chaînes dans la fenêtre **Sortie** de Visual Studio lors de l’exécution. Pour plus d’informations sur le débogage [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] applications, consultez [déboguer les applications universelles Windows dans Visual Studio](/visualstudio/debugger/debugging-windows-store-and-windows-universal-apps.md).  
  
 Pour déboguer des scripts Internet Explorer, vous devez disposer d’un débogueur de script installé et le script doit être exécuté en mode débogage. Internet Explorer 8 et ses versions ultérieures incluent le débogueur [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] . Si vous utilisez une version antérieure d’Internet Explorer, consultez [Procédure : activation et démarrage du débogage des scripts à partir d’Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
 Si le script n’est pas en cours de débogage, les fonctions n’ont aucun effet.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise la fonction `write` pour afficher la valeur de la variable.  
  
```JavaScript  
var counter = 42;  
Debug.write("The value of counter is " + counter);  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="constants"></a>Constantes  
 [Constantes Debug](../../javascript/reference/debug-constants.md)  
  
## <a name="properties"></a>Propriétés  
 [Debug.debuggerenabled, propriété](../../javascript/reference/debug-debuggerenabled-property.md) &#124; [Debug.setnonusercodeexceptions, propriété](../../javascript/reference/debug-setnonusercodeexceptions-property.md)  
  
## <a name="functions"></a>Fonctions  
 [Fonction Debug.msTraceAsyncCallbackStarting](../../javascript/reference/debug-mstraceasynccallbackstarting-function.md) &#124; [Fonction Debug.msTraceAsyncCallbackCompleted](../../javascript/reference/debug-mstraceasynccallbackcompleted-function.md) &#124; [Fonction Debug.msTraceAsyncOperationCompleted](../../javascript/reference/debug-mstraceasyncoperationcompleted-function.md) &#124; [Fonction Debug.msTraceAsyncOperationStarting](../../javascript/reference/debug-mstraceasyncoperationstarting-function.md) &#124; [Fonction Debug.msUpdateAsyncCallbackRelation](../../javascript/reference/debug-msupdateasynccallbackrelation-function.md) &#124; [Debug.Write, fonction](../../javascript/reference/debug-write-function-javascript.md) &#124; [Debug.writeln, fonction](../../javascript/reference/debug-writeln-function-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Instruction debugger](../../javascript/reference/debugger-statement-javascript.md)