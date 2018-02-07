---
title: "Utilisation de la méthode Bind (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- bind method [JavaScript]
- this object [JavaScript]
ms.assetid: f608f95b-3b9d-437a-a67a-5a4ef8f6c07f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d185801cc5bba355751147edb79b9c47d21f8eed
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/05/2018
---
# <a name="using-the-bind-method-javascript"></a>Utilisation de la méthode Bind (JavaScript)
La méthode JavaScript `bind` a plusieurs utilisations. En général, elle est utilisée pour conserver le contexte d'exécution d'une fonction qui s'exécute dans un autre contexte. `bind` crée une fonction qui a le même corps que la fonction d'origine. Le premier argument passé à `bind` spécifie la valeur du mot clé `this` dans la fonction liée. Vous pouvez également transmettre des arguments facultatifs supplémentaires à `bind`. Pour obtenir des exemples d’autres utilisations, consultez la [bind, méthode (Fonction)](../../javascript/reference/bind-method-function-javascript.md). Pour obtenir un exemple de l’utilisation de `bind` pour appliquer ces fonctions partiellement, consultez [Modèles et conseils de programmation asynchrone dans Hilo JavaScript (Windows Store)](http://msdn.microsoft.com/library/windows/apps/jj649740.aspx).  
  
## <a name="preserving-the-execution-context-using-bind"></a>Conserver le contexte d'exécution à l'aide de liaison  
 La fonction `bind` est souvent utilisée lors de l'ajout d'écouteurs d'événements. Dans l'exemple de code suivant, `bind` permet de conserver le contexte de l'objet actuel (`DataObject`). L'objet de données est passé à `bind` à l'aide du mot clé `this`, qui permet d'accéder aux propriétés de l'objet de données et fonctionne lorsque le gestionnaire d'événements (`dataReadyHandler`) s'exécute. Pour illustrer le mode de fonctionnement de `bind`, ce code crée un événement personnalisé.  
  
```JavaScript  
var data;  
  
var dataReadyEvent = document.createEvent("Event");  
dataReadyEvent.initEvent("dataReady", true, false);  
  
function DataObject() {  
    this.name = "Data Object";  
    this.data = function () {  
        return data;  
    }  
    this.onDataCompleted = dataReadyHandler;  
    document.addEventListener('dataReady', this.onDataCompleted.bind(this));  
    // To see the result of not using bind, comment out the preceding line,   
    // and uncomment the following line of code.  
    // document.addEventListener('dataReady', this.onDataCompleted);  
}  
function dataReadyHandler() {  
    if (console && console.log) {  
        console.log("Data object property value: " + this.name);  
        console.log("Data object property value: " + this.data());  
    }  
}  
  
setTimeout(function () {  
    data = [0, 1, 2, 3];  
    document.dispatchEvent(dataReadyEvent);  
    }, 5000);
  
var dataObj = new DataObject();  
  
// Output:  
// Data Object  
// 0,1,2,3  
  
```  
  
 Si vous commentez la ligne de code qui utilise `bind`, annulez les marques de commentaire de la ligne de code qui appelle `addEventListener` sans `bind`, puis réexécutez le code, `dataReadyHandler` ne fonctionnera pas. Par exemple, dans `dataReadyHandler`, `this.name` n'est pas défini, et `this.data()` génère une erreur car l'objet `this` ne fait plus référence à l'objet de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode bind (Function)](../../javascript/reference/bind-method-function-javascript.md)
