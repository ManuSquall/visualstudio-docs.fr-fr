---
title: "Gestion des événements Windows Runtime dans JavaScript | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime events
- Windows Runtime events [JavaScript]
ms.assetid: d9436aff-2c30-4846-b8df-eaa3e63fd75c
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: e963472ee51f2439b50807a49425dcd7f6d8443a
ms.contentlocale: fr-fr
ms.lasthandoff: 08/11/2017

---
# <a name="handling-windows-runtime-events-in-javascript"></a>Gestion des événements Windows Runtime dans JavaScript
Les événements Windows Runtime ne sont pas représentés de la même manière en JavaScript qu'en C++ ou dans .NET Framework. Ce ne sont pas des propriétés de classe, mais ils sont représentés plutôt en tant qu'identificateurs de chaînes qui sont passés aux méthodes `addEventListener` et `removeEventListener` de la classe. Par exemple, vous pouvez ajouter un gestionnaire d’événements pour l’événement [Geolocator.PositionChanged](http://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.geolocation.geolocator.positionchanged.aspx) en passant la chaîne « positionchanged » à la méthode `Geolocator.addEventListener` :  
  
```JavaScript  
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
  
 En JavaScript, les arguments d'événement Windows Runtime sont représentés en tant qu'objet d'événement unique. Dans l'exemple suivant d'une méthode de gestionnaire d'événements, le paramètre `ev` est un objet qui contient à la fois l'expéditeur (la propriété cible) et les autres arguments d'événement. Les arguments d'événement sont ceux documentés pour chaque événement.  
  
```JavaScript  
function (ev) {  
    console.log("Target: " + ev.target);  
    console.log("Position: " +  
        ev.position.latitude + "," +  
        ev.position.longitude);  
};  
  
```  
  
> [!IMPORTANT]
>  Les fonctionnalités Windows Runtime ne sont pas disponibles pour les applications qui s’exécutent dans Internet Explorer.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de Windows Runtime dans JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)
