---
title: "Tableaux typ&#233;s (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: fa82c562-0ebf-4559-aecc-166e59f7fb64
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Tableaux typ&#233;s (JavaScript)
Vous pouvez utiliser les tableaux typés pour gérer des données binaires de sources telles que les protocoles réseau, les formats de fichier binaire et les mémoires tampons de graphiques brutes.  Les tableaux typés peuvent également être utilisés pour gérer des données binaires en mémoire avec des dispositions d'octets connues.  
  
## Exemple  
 Le code suivant montre comment utiliser un [ArrayBuffer, objet](../../javascript/reference/arraybuffer-object.md) comme réponse d'un objet [XMLHttpRequest](http://msdn.microsoft.com/library/ie/ms535874\(v=vs.85\).aspx).  Vous pouvez manipuler les octets dans la réponse à l'aide des différentes méthodes de l'[DataView, objet](../../javascript/reference/dataview-object.md) ou en copiant les octets dans le tableau typé approprié.  
  
> [!TIP]
>  Pour plus d'informations sur l'utilisation de différents types de réponse avec un objet `XmlHttpRequest`, consultez  [XMLHttpRequest.responseType](http://msdn.microsoft.com/fr-fr/8d7738d1-4bfd-4cf1-8015-174def089556), [Améliorations de XMLHttpRequest](http://msdn.microsoft.com/fr-fr/be09137c-6546-441b-b953-dcbf72b77069) et [Téléchargement de différents types de contenu \(applications du Windows Store\)](http://msdn.microsoft.com/fr-fr/c0006bbd-17f9-4c6a-af81-2acaf109111d).  
  
```javascript  
...  
<div id="xhrDiv"></div>  
...  
var name = "http://www.microsoft.com";  
var xhrDiv = document.getElementById("xhrDiv");  
  
var req = new XMLHttpRequest();  
req.open("GET", name, true);  
req.responseType = "arraybuffer";  
req.onreadystatechange = function () {  
if (req.readyState == req.DONE) {  
    var arrayResponse = req.response;  
    var dataView = new DataView(arrayResponse);  
    var ints = new Uint32Array(dataView.byteLength / 4);  
  
    xhrDiv.style.backgroundColor = "#00FF00";  
    xhrDiv.innerText = "Array is " + ints.length + "uints long";  
    }  
}  
req.send();  
```  
  
## ArrayBuffer  
 Un [ArrayBuffer, objet](../../javascript/reference/arraybuffer-object.md) représente une mémoire tampon de données brutes utilisée pour stocker des données pour les différents tableaux typés.  Vous ne pouvez pas lire ni écrire dans un objet `ArrayBuffer`. Toutefois, vous pouvez le passer à un tableau typé ou à un objet [DataView, objet](../../javascript/reference/dataview-object.md) pour interpréter la mémoire tampon brute.  Vous pouvez utiliser un objet `ArrayBuffer` pour stocker n'importe quel type de données \(ou des types de données mixtes\).  
  
## DataView  
 Vous pouvez utiliser un [DataView, objet](../../javascript/reference/dataview-object.md) pour lire et écrire les différents types de données binaires à n'importe quel emplacement de l'objet `ArrayBuffer`.  
  
## Tableaux typés  
 Les types de tableaux typés représentent des vues d'un [ArrayBuffer, objet](../../javascript/reference/arraybuffer-object.md) pouvant être indexées et manipulées.  Tous les types tableau sont de longueur fixe.  
  
||||  
|-|-|-|  
|Nom|Taille \(en octets\)|Description|  
|[Int8Array, objet](../../javascript/reference/int8array-object.md)|1|Entier signé de 8 bits en complément à deux|  
|[Uint8Array, objet](../../javascript/reference/uint8array-object.md)|1|Entier non signé de 8 bits|  
|[Int16Array, objet](../../javascript/reference/int16array-object.md)|2|Entier signé de 16 bits en complément à deux|  
|[Uint16Array, objet](../../javascript/reference/uint16array-object.md)|2|Entier non signé de 16 bits|  
|[Int32Array, objet](../../javascript/reference/int32array-object.md)|4|Entier signé de 32 bits en complément à deux|  
|[Uint32Array, objet](../../javascript/reference/uint32array-object.md)|4|Entier non signé de 32 bits|  
|[Float32Array, objet](../../javascript/reference/float32array-object.md)|4|Virgule flottante IEEE 32 bits|  
|[Float64Array, objet](../../javascript/reference/float64array-object.md)|8|Virgule flottante IEEE 64 bits|