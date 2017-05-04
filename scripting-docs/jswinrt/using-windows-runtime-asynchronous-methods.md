---
title: "Utilisation des m&#233;thodes Windows Runtime asynchrones | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JavaScript, méthodes asynchrones Windows Runtime"
ms.assetid: 70756833-44f7-4383-827f-2ac781558082
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Utilisation des m&#233;thodes Windows Runtime asynchrones
De nombreuses méthodes Windows Runtime sont asynchrones, notamment les méthodes susceptibles d'être longues à s'exécuter.  Ces méthodes retournent généralement une action ou une opération asynchrone \(par exemple, `Windows.Foundation.IAsyncAction`, `Windows.Foundation.IAsyncOperation`, `Windows.Foundation.IAsyncActionWithProgress` ou `Windows.Foundation.IAsyncOperationWithProgress`\).  Ces méthodes sont représentées dans JavaScript par le modèle [CommonJS\/Promises\/A](http://go.microsoft.com/fwlink/p/?LinkId=244434).  Ainsi, elles retournent un objet Promise qui possède une fonction [then](http://msdn.microsoft.com/fr-fr/c63904fc-465b-4fd5-a1d6-e4fb200248e7), pour laquelle vous devez fournir une fonction `completed` qui traite le résultat si l'opération réussit.  Si vous ne voulez pas fournir un gestionnaire d'erreur, vous devez utiliser la fonction [done](http://msdn.microsoft.com/fr-fr/9a5e6877-a2cf-421f-a91e-37d84ccb40da) à la place de la fonction [then](http://msdn.microsoft.com/fr-fr/c63904fc-465b-4fd5-a1d6-e4fb200248e7).  
  
> [!IMPORTANT]
>  Les fonctionnalités Windows Runtime ne sont pas disponibles pour les applications qui s'exécutent dans Internet Explorer.  
  
## Exemples de méthodes asynchrones  
 Dans l'exemple suivant, la fonction [then](http://msdn.microsoft.com/fr-fr/c63904fc-465b-4fd5-a1d6-e4fb200248e7) accepte un paramètre qui représente la valeur finale de la méthode `createResourceAsync`.  
  
```javascript  
client.createResourceAsync(uri, description, item)  
    // Success.  
    .then(function(newItem) {   
        console.log("New item is: " + newItem.id);  
            });  
```  
  
 Dans ce cas, si la méthode `createResourceAsync` échoue, elle retourne un objet Promise dans l'état d'erreur, mais ne lève pas d'exception.  Vous pouvez traiter une erreur en utilisant la fonction [then](http://msdn.microsoft.com/fr-fr/c63904fc-465b-4fd5-a1d6-e4fb200248e7) comme suit.  
  
```javascript  
client.createResourceAsync(uri, description, item)  
    // Success.  
    .then(function(newItem) {   
              console.log("New item is: " + newItem.id);  
          }  
          function(err) {  
              console.log("Got error: " + err.message);  
          });  
```  
  
 Si vous ne voulez pas traiter l'erreur explicitement, mais voulez lever une exception, vous pouvez utiliser la fonction [done](http://msdn.microsoft.com/fr-fr/9a5e6877-a2cf-421f-a91e-37d84ccb40da) à la place.  
  
```javascript  
client.createResourceAsync(uri, description, item)  
    // Success.  
      .done(function(newItem) {   
               console.log("New item is: " + newItem.id);  
            });  
```  
  
 Vous pouvez également afficher la progression en utilisant une troisième fonction.  
  
```javascript  
client.createResourceAsync(uri, description, item)  
    // Success.  
      .then(function(newItem) {   
               console.log("New item is: " + newItem.id);  
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
  
 Pour plus d'informations sur la programmation asynchrone, consultez [Asynchronous programming](http://msdn.microsoft.com/fr-fr/904ff97c-bb36-4ac5-9eda-a961e3639415).  
  
## Voir aussi  
 [Utilisation de Windows Runtime dans JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)