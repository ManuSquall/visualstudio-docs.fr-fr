---
title: "Gestion des &#233;v&#233;nements Windows Runtime dans JavaScript | Microsoft Docs"
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
  - "JavaScript, Événements Windows Runtime"
  - "Événements Windows Runtime (JavaScript)"
ms.assetid: d9436aff-2c30-4846-b8df-eaa3e63fd75c
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Gestion des &#233;v&#233;nements Windows Runtime dans JavaScript
Les événements Windows Runtime ne sont pas représentés de la même manière en JavaScript qu'en C\+\+ ou dans .NET Framework.  Ce ne sont pas des propriétés de classe, mais ils sont représentés plutôt en tant qu'identificateurs de chaînes qui sont passés aux méthodes `addEventListener` et `removeEventListener` de la classe.  Par exemple, vous pouvez ajouter un gestionnaire d'événements pour l'événement [Geolocator.PositionChanged](http://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.geolocation.geolocator.positionchanged.aspx) en passant la chaîne "positionchanged" à la méthode `Geolocator.addEventListener` :  
  
```javascript  
var locator =  new Windows.Devices.Geolocation.Geolocator();  
locator.addEventListener(  
    "positionchanged",   
     function (ev) {  
        console.log("Got event");  
    });  
```  
  
 Vous pouvez également définir la propriété `locator.onpositionchanged`.  
  
```  
locator.onpositionchanged =    
    function (ev) {  
        console.log("Got event");  
    };  
```  
  
 En JavaScript, les arguments d'événement Windows Runtime sont représentés en tant qu'objet d'événement unique.  Dans l'exemple suivant d'une méthode de gestionnaire d'événements, le paramètre `ev` est un objet qui contient à la fois l'expéditeur \(la propriété cible\) et les autres arguments d'événement.  Les arguments d'événement sont ceux documentés pour chaque événement.  
  
```javascript  
function (ev) {  
    console.log("Target: " + ev.target);  
    console.log("Position: " +  
        ev.position.latitude + "," +  
        ev.position.longitude);  
};  
  
```  
  
> [!IMPORTANT]
>  Les fonctionnalités Windows Runtime ne sont pas disponibles pour les applications qui s'exécutent dans Internet Explorer.  
  
## Voir aussi  
 [Utilisation de Windows Runtime dans JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)