---
title: "ubound, m&#233;thode (VBArray) (JavaScript) | Microsoft Docs"
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
  - "ubound"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ubound (méthode)"
ms.assetid: 761811c5-9a3d-4cb3-bfe0-0a8749f34496
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# ubound, m&#233;thode (VBArray) (JavaScript)
Retourne la valeur d’index la plus élevée dans la dimension spécifiée de l’objet VBArray.  
  
## Syntaxe  
  
```  
  
safeArray.ubound(dimension)  
```  
  
## Paramètres  
 *safeArray*  
 Obligatoire. Objet VBArray.  
  
 `dimension`  
 Facultatif. Dimension de l’objet VBArray pour laquelle l’index lié le plus élevé est demandé. S’il est omis, `ubound` se comporte comme si la valeur 1 était passée.  
  
## Notes  
 Si l’objet VBArray est vide, la méthode `ubound` retourne la valeur correspondant à « non défini » \(undefined\). Si `dim` est supérieur au nombre de dimensions de l’objet VBArray ou s’il est négatif, la méthode génère une erreur « Indice hors limites ».  
  
## Exemple  
 L’exemple suivant se compose de trois parties. La première partie est le code VBScript destiné à créer un tableau sécurisé Visual Basic. La deuxième partie est le code [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] qui détermine le nombre de dimensions dans le tableau sécurisé et la limite supérieure de chaque dimension. Ces deux parties prennent place dans la section \<HEAD\> d’une page HTML. La troisième partie est le code [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] qui s’intègre dans la section \<BODY\> pour exécuter les deux autres parties.  
  
```javascript  
<head>  
<script type="text/vbscript">  
<!--  
Function CreateVBArray()  
   Dim i, j, k  
   Dim a(2, 2)  
   k = 1  
   For i = 0 To 2  
      For j = 0 To 2  
         a(j, i) = k  
         k = k + 1  
      Next  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
  
<script type="text/javascript">  
<!--  
function VBArrayTest(vba)  
{  
   var i;  
   var a = new VBArray(vba);  
   var s = "";  
   for (i = 1; i <= a.dimensions(); i++)  
   {  
      s += "The upper bound of dimension ";  
      s += i + " is ";  
      s += a.ubound(i);  
      s += ".<br />";  
   }  
   return (s);  
}  
-->  
</script>  
</head>  
  
<body>  
<script type="text/javascript">  
   document.write(VBArrayTest(CreateVBArray()));  
</script>  
</body>  
```  
  
## Configuration requise  
 Pris en charge dans les modes de document suivants : Quirks, Internet Explorer 6 \(mode standard\), Internet Explorer 7 \(mode standard\), Internet Explorer 8 \(mode standard\), Internet Explorer 9 \(mode standard\) et Internet Explorer 10 \(mode standard\). Non pris en charge dans les applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. Voir [Informations de version](../../javascript/reference/javascript-version-information.md).  
  
 **S'applique à** : [Objet VBArray](../../javascript/reference/vbarray-object-javascript.md)  
  
## Voir aussi  
 [dimensions, méthode \(VBArray\)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [getItem, méthode \(VBArray\)](../../javascript/reference/getitem-method-vbarray-javascript.md)   
 [lbound, méthode \(VBArray\)](../../javascript/reference/lbound-method-vbarray-javascript.md)   
 [toArray, méthode \(VBArray\)](../../javascript/reference/toarray-method-vbarray-javascript.md)