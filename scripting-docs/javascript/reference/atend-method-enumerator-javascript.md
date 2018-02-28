---
title: "atEnd, méthode (Enumerator) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- atEnd
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- atEnd method
ms.assetid: 326808fb-9a0f-428e-aff1-b11b237913f1
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7b5097d00c11ffafc314264f134aedda3981c8e2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="atend-method-enumerator-javascript"></a>atEnd, méthode (Enumerator) (JavaScript)
Retourne une valeur booléenne indiquant si l’énumérateur se trouve à la fin de la collection.  
  
> [!WARNING]
>  Cet objet est pris en charge uniquement dans Internet Explorer.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
myEnum.atEnd()  
```  
  
## <a name="remarks"></a>Remarques  
 La référence *myEnum* obligatoire est tout objet `Enumerator` .  
  
 La méthode `atEnd` retourne **true** si l’élément actuel est le dernier de la collection, si la collection est vide ou si l’élément actuel n’est pas défini. Sinon, elle retourne **False**.  
  
## <a name="example"></a>Exemple  
 Dans le code suivant, la méthode `atEnd` est utilisée pour déterminer si la fin d’une liste de lecteurs a été atteinte :  
  
```JavaScript  
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
  
## <a name="requirements"></a>Spécifications  
 Pris en charge dans les modes de document suivants : Quirks, Internet Explorer 6 (mode standard), Internet Explorer 7 (mode standard), Internet Explorer 8 (mode standard), Internet Explorer 9 (mode standard) et Internet Explorer 10 (mode standard). Non pris en charge dans les applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] . Voir [Informations de version](../../javascript/reference/javascript-version-information.md).  
  
 **S'applique à**: [Enumerator Object](../../javascript/reference/enumerator-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Item, méthode (Enumerator)](../../javascript/reference/item-method-enumerator-javascript.md)   
 [MoveFirst, méthode (Enumerator)](../../javascript/reference/movefirst-method-enumerator-javascript.md)   
 [moveNext, méthode (Enumerator)](../../javascript/reference/movenext-method-enumerator-javascript.md)   
 [Objet Enumerator](../../javascript/reference/enumerator-object-javascript.md)