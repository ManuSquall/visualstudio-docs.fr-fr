---
title: "LBound, méthode (VBArray) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: lbound
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: lbound method
ms.assetid: 30ff5e8a-8165-494b-bce8-0a562ec2eec3
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b01adf424d42e9d24512d15b03ede6079a3da186
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="lbound-method-vbarray-javascript"></a>lbound, méthode (VBArray) (JavaScript)
Retourne la valeur d’index la plus basse dans la dimension spécifiée d’un objet VBArray.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
safeArray.lbound(dimension)   
```  
  
## <a name="parameters"></a>Paramètres  
 *safeArray*  
 Obligatoire. Objet VBArray.  
  
 `dimension`  
 Facultatif. La dimension de l’objet VBArray pour lequel l’index de la limite inférieure est demandée. S’il est omis, `lbound` se comporte comme si la valeur 1 était passée.  
  
## <a name="remarks"></a>Remarques  
 Si l’objet VBArray est vide, la méthode `lbound` retourne la valeur correspondant à « non défini » (undefined). Si `dimension` est supérieur au nombre de dimensions de l’objet VBArray ou s’il est négatif, la méthode génère une erreur « Indice hors limites ».  
  
## <a name="example"></a>Exemple  
 L’exemple suivant se compose de trois parties. La première partie est le code VBScript destiné à créer un tableau sécurisé Visual Basic. La deuxième partie est [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] code qui détermine le nombre de dimensions dans le tableau sécurisé et la limite inférieure de chaque dimension. Étant donné que le tableau sécurisé est créé dans VBScript plutôt que Visual Basic, la limite inférieure sera toujours zéro. Ces deux éléments aller dans le \<HEAD > section d’une page HTML. La troisième partie est le [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] code qui s’intègre dans le \<corps > pour exécuter les deux autres parties.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Spécifications  
 Pris en charge dans les modes de document suivants : Quirks, Internet Explorer 6 (mode standard), Internet Explorer 7 (mode standard), Internet Explorer 8 (mode standard), Internet Explorer 9 (mode standard) et Internet Explorer 10 (mode standard). Non pris en charge dans les applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] . Voir [Informations de version](../../javascript/reference/javascript-version-information.md).  
  
 **S'applique à**: [VBArray Object](../../javascript/reference/vbarray-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [dimensions, méthode (VBArray)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [GetItem, méthode (VBArray)](../../javascript/reference/getitem-method-vbarray-javascript.md)   
 [toArray, méthode (VBArray)](../../javascript/reference/toarray-method-vbarray-javascript.md)   
 [Méthode ubound (VBArray)](../../javascript/reference/ubound-method-vbarray-javascript.md)