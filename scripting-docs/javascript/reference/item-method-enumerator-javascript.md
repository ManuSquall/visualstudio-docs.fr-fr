---
title: "item, m&#233;thode (Enumerator) (JavaScript) | Microsoft Docs"
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
  - "item"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Item (méthode)"
ms.assetid: a88e93f2-42df-4578-a4f9-0760bd074185
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# item, m&#233;thode (Enumerator) (JavaScript)
Retourne l’élément actuel de la collection.  
  
> [!WARNING]
>  Cet objet est pris en charge uniquement dans Internet Explorer.  
  
## Syntaxe  
  
```  
  
enumObj.item()  
```  
  
## Notes  
 La référence *enumObj* obligatoire est tout objet `Enumerator`.  
  
 La méthode **item** retourne l’élément actuel. Si la collection est vide ou si l’élément actuel n’est pas défini, elle retourne **undefined**.  
  
## Exemple  
 Dans le code suivant, la méthode **élément** est utilisée pour retourner un membre de la collection `Drives`.  
  
```javascript  
function ShowDrives()  
{  
    var s = "";  
    var bytesPerGB = 1024 * 1024 * 1024;  
  
    var fso = new ActiveXObject("Scripting.FileSystemObject");  
    var e = new Enumerator(fso.Drives);  
  
    e.moveFirst();  
    while (e.atEnd() == false)  
    {  
        var drv = e.item();  
  
        s += drv.Path + " - ";  
  
        if (drv.IsReady)  
        {  
            var freeGB = drv.FreeSpace / bytesPerGB;  
            var totalGB = drv.TotalSize / bytesPerGB;  
  
            s += freeGB.toFixed(3) + " GB free of ";  
            s += totalGB.toFixed(3) + " GB";  
        }  
        else  
        {  
            s += "Not Ready";  
        }  
  
        s += "<br />";  
  
        e.moveNext();  
    }  
    return(s);  
}  
```  
  
## Configuration requise  
 Pris en charge dans les modes de document suivants : Quirks, Internet Explorer 6 \(mode standard\), Internet Explorer 7 \(mode standard\), Internet Explorer 8 \(mode standard\), Internet Explorer 9 \(mode standard\) et Internet Explorer 10 \(mode standard\). Non pris en charge dans les applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. Voir [Informations de version](../../javascript/reference/javascript-version-information.md).  
  
 **S'applique à** : [Objet Enumerator](../../javascript/reference/enumerator-object-javascript.md)  
  
## Voir aussi  
 [atEnd, méthode \(Enumerator\)](../../javascript/reference/atend-method-enumerator-javascript.md)   
 [moveFirst, méthode \(Enumerator\)](../../javascript/reference/movefirst-method-enumerator-javascript.md)   
 [moveNext, méthode \(Enumerator\)](../../javascript/reference/movenext-method-enumerator-javascript.md)