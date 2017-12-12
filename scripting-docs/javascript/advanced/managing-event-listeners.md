---
title: "Gestion des détecteurs d’événements | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 87717f5d-b0c6-4c8d-a293-476002b7bfcf
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a97c579716b9964b8dfb93db419e9a70160d33a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="managing-event-listeners"></a>Gestion des détecteurs d’événements
Si la durée de vie d’un élément ou d’un objet DOM est différente de la durée de vie de son détecteur d’événements associé, vous devrez peut-être utiliser la méthode [removeEventListener](http://msdn.microsoft.com/library/ie/ff975250\(v=vs.85\).aspx) pour éviter les fuites de mémoire.  
  
## <a name="event-listeners-and-object-scope"></a>Détecteurs d'événements et portée d'objet  
 L'exemple de code suivant montre du code qui peut provoquer une fuite de mémoire quand la fonction `dataObjFactory()` est appelée. Dans ce code, un détecteur d'événements est inscrit pour un objet de données chaque fois qu'un nouvel objet de données est créé. Pour que l’objet de données actif soit disponible dans le gestionnaire d’événements `dataReady()`, la [Méthode bind (Fonction)](../../javascript/reference/bind-method-function-javascript.md) est utilisée dans `addEventListener`.  
  
```JavaScript  
 var data;  
 var dataObj;  
  
 var dataReadyEvent = document.createEvent("Event");  
 dataReadyEvent.initEvent("dataReady", true, false);  
  
 function DataObject() {  
  
     this.name = "Data Object";  
     this.data = function () {  
         return data;  
     }  
     this.onDataCompleted = dataReady;  
     // this.handlerRef = this.onDataCompleted.bind(this);  
  
     // document.addEventListener('dataReady', this.handlerRef);  
     document.addEventListener('dataReady', this.onDataCompleted.bind(this));  
 }  
  
 // Runs when the data is available.  
 function dataReady() {  
     if (console && console.log) {  
         console.log("object value: " + this.name);  
         console.log("object value: " + this.data());  
     }  
 }  
  
setTimeout(function () {  
    // Generate data after a timeout period.  
    data = [0, 1, 2, 3];  
    document.dispatchEvent(dataReadyEvent);  
}, 10000);  
  
function dataObjFactory() {  
     for (var x = 0; x < 100; x++) {  
         if (dataObj) {  
             // The following line of code has no effect.  
             document.removeEventListener('dataReady', dataObj.onDataCompleted);  
             dataObj = null;  
         }  
         dataObj = new DataObject();  
     }  
 }  
  
 dataObjFactory();  
```  
  
 Le détecteur pour chaque objet de données est inscrit avec l'objet `document`, qui a une durée de vie différente de celle des objets de données. Le détecteur d'événements inscrit pour chaque objet de données l'empêche de faire l'objet d'un garbage collection tant que l'objet `document` reste dans la portée. (Dans certains modèles de conception JavaScript récents, l'objet document restera dans la portée pendant la durée de vie de l'application web.) Pour empêcher une fuite de mémoire, `removeEventListener` est appelé dans la fonction `dataObjFactory`. Cependant, ce code échoue car `removeEventListener` n’a pas été appelé dans la version liée du gestionnaire d’événements qui est retournée par la fonction `bind`.  
  
 Pour corriger ce code et pour que les objets soient disponibles pour le garbage collection, vous devez stocker une référence à la version liée du gestionnaire d'événements, comme indiqué dans ce code, puis passer la référence stockée à `addEventListener`. Voici le code corrigé pour `DataObject` :  
  
```JavaScript  
function DataObject() {  
  
    this.name = "Data Object";  
    this.data = function () {  
        return data;  
    }  
    this.onDataCompleted = dataReady;  
    this.handlerRef = this.onDataCompleted.bind(this);  
  
    document.addEventListener('dataReady', this.handlerRef);  
    // document.addEventListener('dataReady', this.onDataCompleted.bind(this));  
}  
  
```  
  
 Enfin, vous devez appeler `removeEventListener` dans la référence stockée (`handlerRef`) de la fonction liée. Voici le code corrigé pour `dataObjFactory` :  
  
```JavaScript  
function dataObjFactory() {  
     for (var x = 0; x < 100; x++) {  
         if (dataObj) {  
             document.removeEventListener('dataReady', dataObj.handlerRef);  
         }  
         dataObj = new DataObject();  
     }  
 }  
  
```  
  
 Désormais, l'appel à `removeEventListener` fonctionne et les objets de données non nécessaires peuvent faire l'objet d'un garbage collection même pendant que l'objet `document` reste dans la portée.