---
title: "toArray, m&#233;thode (VBArray) (JavaScript) | Microsoft Docs"
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
  - "toArray"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toArray (méthode)"
ms.assetid: 664de44c-2039-4289-82f6-948e9d744d80
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# toArray, m&#233;thode (VBArray) (JavaScript)
Retourne un tableau [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] standard converti à partir d’un objet VBArray.  
  
## Syntaxe  
  
```  
  
safeArray.toArray( )  
```  
  
## Notes  
 La référence *safeArray* nécessaire est un objet VBArray.  
  
 La conversion traduit l’objet VBArray multidimensionnel en tableau [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] unidimensionnel. Chaque dimension successive est ajoutée à la fin de la précédente. Par exemple, un objet VBArray à trois dimensions et trois éléments dans chaque dimension est converti en tableau [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] comme suit :  
  
 Supposons que l’objet VBArray contient \(1, 2, 3\), \(4, 5, 6\), \(7, 8, 9\). Après conversion, voici ce que le tableau [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] contient : 1, 2, 3, 4, 5, 6, 7, 8, 9.  
  
 Il n’existe pour l’heure aucun moyen de convertir un tableau [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] en objet VBArray.  
  
## Exemple  
 L’exemple suivant se compose de trois parties. La première partie est le code VBScript destiné à créer un tableau sécurisé Visual Basic. La deuxième partie est le code [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] qui convertit le tableau sécurisé Visual Basic en tableau [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Ces deux parties prennent place dans la section \<HEAD\> d’une page HTML. La troisième partie est le code [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] qui s’intègre dans la section \<BODY\> pour exécuter les deux autres parties.  
  
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
function VBArrayTest(vbarray)  
{  
   var a = new VBArray(vbarray);  
   var b = a.toArray();  
   var i;  
   for (i = 0; i < 9; i++)   
   {  
      document.writeln(b[i]);  
   }  
}  
-->  
</script>  
</head>  
  
<body>  
<script type="text/javascript">  
<!--  
   VBArrayTest(CreateVBArray());  
-->  
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
 [ubound, méthode \(VBArray\)](../../javascript/reference/ubound-method-vbarray-javascript.md)