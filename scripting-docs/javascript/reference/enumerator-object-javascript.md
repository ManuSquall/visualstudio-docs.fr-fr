---
title: Enumerator, objet (JavaScript) | Documents Microsoft
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
- Enumerator
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Enumerator object
ms.assetid: 63f03c21-d58c-47db-a728-4d8d88b0a422
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 50b1ebfb6e24ed734f008b3c05f10a1687c4aff5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636599"
---
# <a name="enumerator-object-javascript"></a>Enumerator, objet (JavaScript)
Permet l’énumération des éléments dans une collection.  
  
> [!WARNING]
>  Cet objet est pris en charge dans Internet Explorer uniquement, pas dans les applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
enumObj = new Enumerator([collection])   
```  
  
## <a name="parameters"></a>Paramètres  
 `enumObj`  
 Obligatoire. Nom de la variable à laquelle l'objet `Enumerator` est assigné.  
  
 `collection`  
 Facultatif. Tout objet Collection.  
  
## <a name="remarks"></a>Remarques  
 Les collections diffèrent des tableaux en ceci que les membres d’une collection ne sont pas directement accessibles. Au lieu d’utiliser des index, comme vous le feriez avec des tableaux, vous pouvez déplacer le pointeur de l’élément actuel seulement au premier élément ou à l’élément suivant d’une collection.  
  
 L’objet `Enumerator` permet d’accéder aux membres d’une collection et se comporte de la même façon que l’instruction `For...Each` dans VBScript.  
  
## <a name="example"></a>Exemple  
 Le code ci-dessous montre l’utilisation de l’objet `Enumerator` :  
  
```JavaScript  
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
  
## <a name="properties"></a>Propriétés  
 L’objet `Enumerator` n’a pas de propriétés.  
  
## <a name="methods"></a>Méthodes  
 [atEnd, méthode](../../javascript/reference/atend-method-enumerator-javascript.md) &#124; [item, méthode](../../javascript/reference/item-method-enumerator-javascript.md) &#124; [MoveFirst, méthode](../../javascript/reference/movefirst-method-enumerator-javascript.md) &#124; [moveNext, méthode](../../javascript/reference/movenext-method-enumerator-javascript.md)  
  
## <a name="requirements"></a>Spécifications  
 Pris en charge dans les modes de document suivants : Quirks, Internet Explorer 6 (mode standard), Internet Explorer 7 (mode standard), Internet Explorer 8 (mode standard), Internet Explorer 9 (mode standard) et Internet Explorer 10 (mode standard). Non pris en charge dans les applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] . Voir [Informations de version](../../javascript/reference/javascript-version-information.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Objet Boolean](../../javascript/reference/boolean-object-javascript.md)