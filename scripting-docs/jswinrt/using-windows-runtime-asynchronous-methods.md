---
title: Utilisation de méthodes asynchrones Windows Runtime | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime asynchronous methods
ms.assetid: 70756833-44f7-4383-827f-2ac781558082
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 215a04a2f3f875743a7fbf910a3a565cf34fb558
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24571449"
---
# <a name="using-windows-runtime-asynchronous-methods"></a>Utilisation de méthodes asynchrones Windows Runtime
De nombreuses méthodes Windows Runtime sont asynchrones, notamment les méthodes susceptibles d'être longues à s'exécuter. Ces méthodes retournent généralement une action ou une opération asynchrone (par exemple, `Windows.Foundation.IAsyncAction`, `Windows.Foundation.IAsyncOperation`, `Windows.Foundation.IAsyncActionWithProgress` ou `Windows.Foundation.IAsyncOperationWithProgress`). Ces méthodes sont représentées dans JavaScript par le modèle [CommonJS/Promises/A](http://go.microsoft.com/fwlink/p/?LinkId=244434). Ainsi, elles retournent un objet Promise qui contient une fonction [then](https://msdn.microsoft.com/en-us/library/windows/apps/br229728.aspx), pour laquelle vous devez fournir une fonction `completed` qui traite le résultat si l’opération réussit. Si vous ne voulez pas fournir un gestionnaire d’erreur, vous devez utiliser la fonction [done](https://msdn.microsoft.com/en-us/library/windows/apps/hh701079.aspx) à la place de la fonction `then`.  
  
> [!IMPORTANT]
>  Les fonctionnalités Windows Runtime ne sont pas disponibles pour les applications qui s’exécutent dans Internet Explorer.  
  
## <a name="examples-of-asynchronous-methods"></a>Exemples de méthodes asynchrones  
 Dans l'exemple suivant, la fonction `then` accepte un paramètre qui représente la valeur finale de la méthode `createResourceAsync`.  
  
```JavaScript  
client.createResourceAsync(uri, description, item)  
    // Success.  
    .then(function(newItem) {   
        console.log("New item is: " + newItem.id);  
            });  
```  
  
 Dans ce cas, si la méthode `createResourceAsync` échoue, elle retourne un objet Promise dans l'état d'erreur, mais ne lève pas d'exception. Vous pouvez traiter une erreur en utilisant la fonction `then` comme suit.  
  
```JavaScript  
client.createResourceAsync(uri, description, item)  
    // Success.  
    .then(function(newItem) {   
              console.log("New item is: " + newItem.id);  
          }  
          function(err) {  
              console.log("Got error: " + err.message);  
          });  
```  
  
 Si vous ne voulez pas traiter l'erreur explicitement, mais voulez lever une exception, vous pouvez utiliser la fonction `done` à la place.  
  
```JavaScript  
client.createResourceAsync(uri, description, item)  
    // Success.  
      .done(function(newItem) {   
               console.log("New item is: " + newItem.id);  
            });  
```  
  
 Vous pouvez également afficher la progression en utilisant une troisième fonction.  
  
```JavaScript  
client.createResourceAsync(uri, description, item)  
    // Success.  
      .then(function(newItem) {   
               console.log("New item is: " + newItem.id);  
            },  
    // Error.  
            function(error) {   
               alert("Failed to create a resource.");  
            },  
    // Progress.  
            function(progress, resultSoFar) {   
               setProgressBar(progress);  
            });  
```  
  
 Pour plus d’informations sur la programmation asynchrone, consultez [Programmation asynchrone dans JavaScript](https://msdn.microsoft.com/en-us/library/windows/apps/hh700330.aspx).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de Windows Runtime dans JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)