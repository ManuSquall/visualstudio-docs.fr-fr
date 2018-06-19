---
title: moveNext, méthode (Enumerator) (JavaScript) | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- moveNext
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- MoveNext method
ms.assetid: 59aa339b-f375-450a-8276-37896a55a824
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab9b07a9a9c4640407cff0eaf21a6e8cd65dac11
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639769"
---
# <a name="movenext-method-enumerator-javascript"></a>moveNext, méthode (Enumerator) (JavaScript)
Déplace l’élément actuel à l’élément suivant dans la collection.  
  
> [!WARNING]
>  Cet objet est pris en charge uniquement dans Internet Explorer.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
enumObj.moveNext( )   
```  
  
## <a name="remarks"></a>Remarques  
 La référence *enumObj* obligatoire est tout objet `Enumerator` .  
  
 Si l’énumérateur se trouve à la fin de la collection ou si la collection est vide, l’élément actuel devient non défini.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, la méthode **moveNext** est utilisée pour passer au lecteur suivant dans la collection `Drives` :  
  
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
 [atEnd, méthode (Enumerator)](../../javascript/reference/atend-method-enumerator-javascript.md)   
 [Item, méthode (Enumerator)](../../javascript/reference/item-method-enumerator-javascript.md)   
 [Méthode moveFirst (Enumerator)](../../javascript/reference/movefirst-method-enumerator-javascript.md)