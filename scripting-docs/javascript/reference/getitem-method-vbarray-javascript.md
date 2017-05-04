---
title: "getItem, m&#233;thode (VBArray) (JavaScript) | Microsoft Docs"
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
  - "getItem"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "getItem (méthode)"
  - "Élément de propriété"
ms.assetid: f62964ad-8b2f-4596-95d0-b20e587ecea5
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# getItem, m&#233;thode (VBArray) (JavaScript)
Retourne l’élément situé à l’emplacement spécifié.  
  
## Syntaxe  
  
```  
  
safeArray.getItem(dimension1[, dimension2, ...], dimensionN)  
```  
  
## Paramètres  
 *safeArray*  
 Obligatoire. Objet VBArray.  
  
 *dimension1,..., dimensionN*  
 Spécifie l’emplacement exact de l’élément souhaité de l’objet VBArray.*n* est égal au nombre de dimensions dans l’objet VBArray.  
  
## Exemple  
 L’exemple suivant se compose de trois parties. La première partie est le code VBScript destiné à créer un tableau sécurisé Visual Basic. La deuxième partie est le code [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] qui itère le tableau sécurisé Visual Basic et imprime le contenu de chaque élément. Ces deux parties prennent place dans la section \<HEAD\> d’une page HTML. La troisième partie est le code [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] qui s’intègre dans la section \<BODY\> pour exécuter les deux autres parties.  
  
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
         a(i, j) = k  
         document.writeln(k)  
         k = k + 1  
      Next  
      document.writeln("<BR>")  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
<script type="text/javascript">  
<!--  
function GetItemTest(vbarray)  
{  
   var i, j;  
   var a = new VBArray(vbarray);  
   for (i = 0; i <= 2; i++)  
   {  
      for (j =0; j <= 2; j++)  
      {  
         document.writeln(a.getItem(i, j));  
      }  
   }  
}  
-->  
</script>  
</head>  
<body>  
<script type="text/javascript">  
<!--  
   GetItemTest(CreateVBArray());  
-->  
</script>  
</body>  
```  
  
## Configuration requise  
 Pris en charge dans les modes de document suivants : Quirks, Internet Explorer 6 \(mode standard\), Internet Explorer 7 \(mode standard\), Internet Explorer 8 \(mode standard\), Internet Explorer 9 \(mode standard\) et Internet Explorer 10 \(mode standard\). Non pris en charge dans les applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. Voir [Informations de version](../../javascript/reference/javascript-version-information.md).  
  
 **S'applique à** : [Objet VBArray](../../javascript/reference/vbarray-object-javascript.md)  
  
## Voir aussi  
 [dimensions, méthode \(VBArray\)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [lbound, méthode \(VBArray\)](../../javascript/reference/lbound-method-vbarray-javascript.md)   
 [toArray, méthode \(VBArray\)](../../javascript/reference/toarray-method-vbarray-javascript.md)   
 [ubound, méthode \(VBArray\)](../../javascript/reference/ubound-method-vbarray-javascript.md)