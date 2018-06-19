---
title: toArray, méthode (VBArray) (JavaScript) | Documents Microsoft
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
- toArray
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toArray method
ms.assetid: 664de44c-2039-4289-82f6-948e9d744d80
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eeee8acad04125eb942089b4d8dacef6f0f5e6fb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641769"
---
# <a name="toarray-method-vbarray-javascript"></a>toArray, méthode (VBArray) (JavaScript)
Retourne un tableau [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] standard converti à partir d’un objet VBArray.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
safeArray.toArray( )   
```  
  
## <a name="remarks"></a>Remarques  
 La référence *safeArray* nécessaire est un objet VBArray.  
  
 La conversion traduit l’objet VBArray multidimensionnel en tableau [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] unidimensionnel. Chaque dimension successive est ajoutée à la fin de la précédente. Par exemple, un objet VBArray à trois dimensions et trois éléments dans chaque dimension est converti en tableau [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] comme suit :  
  
 Supposons que l’objet VBArray contient (1, 2, 3), (4, 5, 6), (7, 8, 9). Après conversion, voici ce que le tableau [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] contient : 1, 2, 3, 4, 5, 6, 7, 8, 9.  
  
 Il n’existe pour l’heure aucun moyen de convertir un tableau [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] en objet VBArray.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant se compose de trois parties. La première partie est le code VBScript destiné à créer un tableau sécurisé Visual Basic. La deuxième partie est le code [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] qui convertit le tableau sécurisé Visual Basic en tableau [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] . Ces deux éléments aller dans le \<HEAD > section d’une page HTML. La troisième partie est le [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] code qui s’intègre dans le \<corps > pour exécuter les deux autres parties.  
  
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
  
## <a name="requirements"></a>Spécifications  
 Pris en charge dans les modes de document suivants : Quirks, Internet Explorer 6 (mode standard), Internet Explorer 7 (mode standard), Internet Explorer 8 (mode standard), Internet Explorer 9 (mode standard) et Internet Explorer 10 (mode standard). Non pris en charge dans les applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] . Voir [Informations de version](../../javascript/reference/javascript-version-information.md).  
  
 **S'applique à**: [VBArray Object](../../javascript/reference/vbarray-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [dimensions, méthode (VBArray)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [GetItem, méthode (VBArray)](../../javascript/reference/getitem-method-vbarray-javascript.md)   
 [LBound, méthode (VBArray)](../../javascript/reference/lbound-method-vbarray-javascript.md)   
 [Méthode ubound (VBArray)](../../javascript/reference/ubound-method-vbarray-javascript.md)