---
title: "dimensions, méthode (VBArray) (JavaScript) | Documents Microsoft"
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
- dimensions
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dimensions method
- VBArray object constant
ms.assetid: ac83589e-85d9-48cb-b28d-c579e65fd604
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9896a5beced00614a825b1921b6046b0ac8a396a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="dimensions-method-vbarray-javascript"></a>dimensions, méthode (VBArray) (JavaScript)
Retourne le nombre de dimensions d’un objet VBArray.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
array.dimensions( )   
```  
  
## <a name="remarks"></a>Remarques  
 Le *tableau* obligatoire est un objet VBArray.  
  
## <a name="example"></a>Exemple  
 La méthode **dimensions** fournit un moyen de récupérer le nombre de dimensions d’un objet VBArray spécifié.  
  
 L’exemple suivant se compose de trois parties. La première partie est le code VBScript destiné à créer un tableau sécurisé Visual Basic. La deuxième partie est le code [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] qui détermine le nombre de dimensions dans le tableau sécurisé et la limite supérieure de chaque dimension. Ces deux éléments aller dans le \<HEAD > section d’une page HTML. La troisième partie est le [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] code qui s’intègre dans le \<corps > pour exécuter les deux autres parties.  
  
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
   return(s);  
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
 [GetItem, méthode (VBArray)](../../javascript/reference/getitem-method-vbarray-javascript.md)   
 [LBound, méthode (VBArray)](../../javascript/reference/lbound-method-vbarray-javascript.md)   
 [toArray, méthode (VBArray)](../../javascript/reference/toarray-method-vbarray-javascript.md)   
 [Méthode ubound (VBArray)](../../javascript/reference/ubound-method-vbarray-javascript.md)