---
title: "Enumerator, objet (JavaScript) | Microsoft Docs"
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
  - "Enumerator"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Enumerator (objet)"
ms.assetid: 63f03c21-d58c-47db-a728-4d8d88b0a422
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# Enumerator, objet (JavaScript)
Permet l’énumération des éléments dans une collection.  
  
> [!WARNING]
>  Cet objet est pris en charge dans Internet Explorer uniquement, pas dans les applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
## Syntaxe  
  
```  
  
enumObj = new Enumerator([collection])   
```  
  
## Paramètres  
 `enumObj`  
 Obligatoire. Nom de la variable à laquelle l'objet `Enumerator` est assigné.  
  
 `collection`  
 Facultatif. Tout objet Collection.  
  
## Notes  
 Les collections diffèrent des tableaux en ceci que les membres d’une collection ne sont pas directement accessibles. Au lieu d’utiliser des index, comme vous le feriez avec des tableaux, vous pouvez déplacer le pointeur de l’élément actuel seulement au premier élément ou à l’élément suivant d’une collection.  
  
 L’objet `Enumerator` permet d’accéder aux membres d’une collection et se comporte de la même façon que l’instruction `For...Each` dans VBScript.  
  
## Exemple  
 Le code ci\-dessous montre l’utilisation de l’objet `Enumerator` :  
  
```javascript  
var bytesPerGB = 1024 * 1024 * 1024;  
  
var fso = new ActiveXObject("Scripting.FileSystemObject");  
  
document.write(fso.Drives);  
var e = new Enumerator(fso.Drives);  
  
var driveString = "";  
  
e.moveFirst();  
while (e.atEnd() == false)  
{  
    var drv = e.item();  
  
    driveString += drv.Path + " - ";  
  
    if (drv.IsReady){  
        var freeGB = drv.FreeSpace / bytesPerGB;  
        var totalGB = drv.TotalSize / bytesPerGB;  
  
        driveString += freeGB.toFixed(3) + " GB free of ";  
        driveString += totalGB.toFixed(3) + " GB";  
    }  
    else{  
        driveString += "Not Ready";  
    }  
  
    driveString += "<br />";;  
  
    e.moveNext();  
}  
document.write(driveString);  
  
// Output: <drive information  
  
```  
  
## Propriétés  
 L’objet `Enumerator` n’a pas de propriétés.  
  
## Méthodes  
 [Méthode atEnd](../../javascript/reference/atend-method-enumerator-javascript.md) &#124; [Méthode item](../../javascript/reference/item-method-enumerator-javascript.md) &#124; [Méthode moveFirst](../../javascript/reference/movefirst-method-enumerator-javascript.md) &#124; [Méthode moveNext](../../javascript/reference/movenext-method-enumerator-javascript.md)  
  
## Configuration requise  
 Pris en charge dans les modes de document suivants : Quirks, Internet Explorer 6 \(mode standard\), Internet Explorer 7 \(mode standard\), Internet Explorer 8 \(mode standard\), Internet Explorer 9 \(mode standard\) et Internet Explorer 10 \(mode standard\). Non pris en charge dans les applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. Voir [Informations de version](../../javascript/reference/javascript-version-information.md).  
  
## Voir aussi  
 [Boolean, objet](../../javascript/reference/boolean-object-javascript.md)