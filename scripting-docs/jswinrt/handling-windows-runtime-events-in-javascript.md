---
title: Gestion des événements Windows Runtime dans JavaScript | Microsoft Docs
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
- JavaScript, Windows Runtime events
- Windows Runtime events [JavaScript]
ms.assetid: d9436aff-2c30-4846-b8df-eaa3e63fd75c
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7e5780a2462e8980c22c474ae6236c87aee599b
ms.sourcegitcommit: 498e39e89a89ad7bf9dcb0617424fff999b1c3b2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2018
ms.locfileid: "36302807"
---
# <a name="handling-windows-runtime-events-in-javascript"></a>Gestion des événements Windows Runtime dans JavaScript
Les événements Windows Runtime ne sont pas représentés de la même manière en JavaScript qu'en C++ ou dans .NET Framework. Ce ne sont pas des propriétés de classe, mais ils sont représentés plutôt en tant qu’identificateurs de chaînes (en minuscules) qui sont passés aux méthodes `addEventListener` et `removeEventListener` de la classe. Par exemple, vous pouvez ajouter un gestionnaire d’événements pour l’événement [Geolocator.PositionChanged](https://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.geolocation.geolocator.positionchanged.aspx) en passant la chaîne « positionchanged » à la méthode `Geolocator.addEventListener` :  
  
```JavaScript  
var locator = new Windows.Devices.Geolocation.Geolocator();  
locator.addEventListener(  
    "positionchanged",   
     function (ev) {  
        console.log("Got event");  
    });  
```  
  
 Vous pouvez également définir la propriété `locator.onpositionchanged` :  
  
```JavaScript  
locator.onpositionchanged =    
    function (ev) {  
        console.log("Got event");  
    };  
```  
  
Une autre différence entre .NET/C++ et JavaScript est le nombre de paramètres pris par un gestionnaire d’événements. Dans .NET/C++, un gestionnaire en prend deux : l’émetteur d’événement et les données d’événement. Dans JavaScript, les deux sont regroupés en tant qu’objet `Event` unique. Dans l’exemple suivant, le paramètre `ev` contient à la fois l’émetteur d’événement (propriété `target`) et les propriétés des données d’événement (ici, uniquement `position`). Les propriétés des données d’événement sont celles documentées pour chaque événement.
  
```JavaScript  
function (ev) {  
    console.log("Sender: " + ev.target);  
    console.log("Position: " +  
        ev.position.latitude + "," +  
        ev.position.longitude);  
};  
```  
  
> [!IMPORTANT]
>  Les fonctionnalités Windows Runtime ne sont pas disponibles pour les applications qui s'exécutent dans Internet Explorer.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de Windows Runtime dans JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)
