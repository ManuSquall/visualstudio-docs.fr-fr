---
title: "DataView, objet | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 250ec067-7505-4ee0-82ab-bfd3c2820afa
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# DataView, objet
Vous pouvez utiliser un objet DataView pour lire et écrire les différents types de données binaires à n'importe quel emplacement dans ArrayBuffer.  
  
## Syntaxe  
  
```  
  
dataView = new DataView(buffer, byteOffset, byteLength);  
```  
  
## Paramètres  
 `dataView`  
 Requis.  Nom de la variable à laquelle l'objet **DataView** est assigné.  
  
 `buffer`  
 ArrayBuffer que le DataView représente.  
  
 `byteOffset`  
 Optionnel.  Spécifie l'offset en octets à partir du début de la mémoire tampon auquel l'objet DataView doit commencer.  
  
 `byteLength`  
 Optionnel.  Spécifie la longueur \(en octets\) de la section de la mémoire tampon que l'objet DataView doit représenter.  
  
## Notes  
 Si les valeurs byteOffset et byteLength sont omises, l'objet DataView couvre l'intégralité de la plage d'ArrayBuffer.  Si la valeur byteLength est omise, l'objet DataView s'étend du byteOffset donné jusqu'à la fin d'ArrayBuffer.  Si les valeurs byteOffset et byteLength données référencent une zone au\-delà de la fin d'ArrayBuffer, une exception est levée.  
  
## Propriétés  
 Le tableau suivant répertorie les propriétés de l'objet `DataView`.  
  
|Propriété|Description|  
|---------------|-----------------|  
|[buffer, propriété](../../javascript/reference/buffer-property-dataview.md)|Lecture seule.  Obtient l'ArrayBuffer référencé par cette vue.|  
|[Propriété byteLength](../../javascript/reference/bytelength-property-dataview.md)|Lecture seule.  Longueur en octets de cette vue à partir du début de son ArrayBuffer, telle qu'elle est résolue au moment de la construction.|  
|[byteOffset, propriété](../../javascript/reference/byteoffset-property-dataview.md)|Lecture seule.  Offset en octets de cette vue à partir du début de son ArrayBuffer, telle qu'elle est résolue au moment de la construction.|  
  
## Méthodes  
 Le tableau suivant répertorie les méthodes de l'objet `DataView`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[Méthode getInt8](../../javascript/reference/getint8-method-dataview.md)|Obtient la valeur Int8 au niveau de l'offset d'octet spécifié à partir du début de la vue.|  
|[getUint8, méthode \(DataView\)](../../javascript/reference/getuint8-method-dataview.md)|Obtient la valeur Uint8 au niveau de l'offset d'octet spécifié à partir du début de la vue.|  
|[getInt16, méthode \(DataView\)](../../javascript/reference/getint16-method-dataview.md)|Obtient la valeur Int16 au niveau de l'offset d'octet spécifié à partir du début de la vue.|  
|[getUint16, méthode \(DataView\)](../../javascript/reference/getuint16-method-dataview.md)|Obtient la valeur Uint16 au niveau de l'offset d'octet spécifié à partir du début de la vue.|  
|[getInt32, méthode \(DataView\)](../../javascript/reference/getint32-method-dataview.md)|Obtient la valeur Int32 au niveau de l'offset d'octet spécifié à partir du début de la vue.|  
|[getUint32, méthode \(DataView\)](../../javascript/reference/getuint32-method-dataview.md)|Obtient la valeur Uint32 au niveau de l'offset d'octet spécifié à partir du début de la vue.|  
|[getFloat32, méthode \(DataView\)](../../javascript/reference/getfloat32-method-dataview.md)|Obtient la valeur Float32 au niveau de l'offset d'octet spécifié à partir du début de la vue.|  
|[getFloat64, méthode \(DataView\)](../../javascript/reference/getfloat64-method-dataview.md)|Obtient la valeur Float64 au niveau de l'offset d'octet spécifié à partir du début de la vue.|  
|[setInt8, méthode \(DataView\)](../../javascript/reference/setint8-method-dataview.md)|Stocke une valeur Int8 au niveau de l'offset d'octet spécifié à partir du début de la vue.|  
|[setUint8, méthode \(DataView\)](../../javascript/reference/setuint8-method-dataview.md)|Stocke une valeur Uint8 au niveau de l'offset d'octet spécifié à partir du début de la vue.|  
|[setInt16, méthode \(DataView\)](../../javascript/reference/setint16-method-dataview.md)|Stocke une valeur Int16 au niveau de l'offset d'octet spécifié à partir du début de la vue.|  
|[setUint16, méthode \(DataView\)](../../javascript/reference/setuint16-method-dataview.md)|Stocke une valeur Uint16 au niveau de l'offset d'octet spécifié à partir du début de la vue.|  
|[setInt32, méthode \(DataView\)](../../javascript/reference/setint32-method-dataview.md)|Stocke une valeur Int32 au niveau de l'offset d'octet spécifié à partir du début de la vue.|  
|[setUint32, méthode \(DataView\)](../../javascript/reference/setuint32-method-dataview.md)|Stocke une valeur Uint32 au niveau de l'offset d'octet spécifié à partir du début de la vue.|  
|[setFloat32, méthode \(DataView\)](../../javascript/reference/setfloat32-method-dataview.md)|Stocke une valeur Float32 au niveau de l'offset d'octet spécifié à partir du début de la vue.|  
|[setFloat64, méthode \(DataView\)](../../javascript/reference/setfloat64-method-dataview.md)|Stocke une valeur Float64 au niveau de l'offset d'octet spécifié à partir du début de la vue.|  
  
## Exemple  
 L'exemple suivant montre comment utiliser un objet DataView pour traiter les données binaires acquises via un XmlHttpRequest :  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var ints = new Int32Array(dataView.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]