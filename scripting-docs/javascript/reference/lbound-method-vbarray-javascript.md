---
title: "lbound, m&#233;thode (VBArray) (JavaScript) | Microsoft Docs"
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
  - "lbound"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "lbound (méthode)"
ms.assetid: 30ff5e8a-8165-494b-bce8-0a562ec2eec3
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# lbound, m&#233;thode (VBArray) (JavaScript)
Retourne la valeur d'index la moins élevée dans la dimension spécifiée d'un objet VBArray.  
  
## Syntaxe  
  
```  
  
safeArray.lbound(dimension)   
```  
  
## Paramètres  
 *SafeArray\(*  
 Requis.  Objet VBArray.  
  
 `dimension`  
 Optionnel.  Dimension de l'objet VBArray dont on veut connaître la valeur d'index la moins élevée.  Si cet argument est omis, la méthode `lbound` considère que la valeur 1 a été passée.  
  
## Notes  
 Si l'objet VBArray est vide, la méthode `lbound` retourne la valeur undefined.  Si l'argument `dimension` est supérieur au nombre de dimensions contenues dans l'objet VBArray, ou s'il est négatif, la méthode retourne le message d'erreur « Indice hors limites ».  
  
## Exemple  
 L'exemple suivant est constitué de trois parties.  La première partie est écrite en code VBScript afin de créer un tableau Visual Basic sécurisé.  La deuxième partie correspond au code [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] qui détermine le nombre de dimensions dans le tableau sécurisé ainsi que la limite inférieure de chaque dimension.  Étant donné que le tableau sécurisé est créé dans VBScript et non pas dans Visual Basic, cette limite inférieure est toujours égale à zéro.  Ces deux parties sont incluses dans la section \<HEAD\> d'une page HTML.  La troisième partie correspond au code [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] à insérer dans la section \<BODY\> pour exécuter les deux autres parties.  
  
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
function VBArrayTest(vba){  
   var i;  
   var a = new VBArray(vba);  
   var s = "";  
   for (i = 1; i <= a.dimensions(); i++)  
   {  
      s += "The lower bound of dimension ";  
      s += i + " is ";  
      s += a.lbound(i);  
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
 Pris en charge dans les modes de document suivants : Quirks, Internet Explorer 6 \(mode standard\), Internet Explorer 7 \(mode standard\), Internet Explorer 8 \(mode standard\), Internet Explorer 9 \(mode standard\) et Internet Explorer 10 \(mode standard\).  Non pris en charge dans les applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  Consultez [Informations sur la version](../../javascript/reference/javascript-version-information.md).  
  
 **S'applique à** : [Objet VBArray](../../javascript/reference/vbarray-object-javascript.md)  
  
## Voir aussi  
 [dimensions, méthode \(VBArray\)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [getItem, méthode \(VBArray\)](../../javascript/reference/getitem-method-vbarray-javascript.md)   
 [toArray, méthode \(VBArray\)](../../javascript/reference/toarray-method-vbarray-javascript.md)   
 [ubound, méthode \(VBArray\)](../../javascript/reference/ubound-method-vbarray-javascript.md)