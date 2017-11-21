---
title: VBArray, objet (JavaScript) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: VBArray
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: VBArray object constant
ms.assetid: f0b767f1-ea8a-4726-962b-2708d4742518
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b86e261a0cef445f1e0e0ecd651d5eb283cffce1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="vbarray-object-javascript"></a>VBArray, objet (JavaScript)
Fournit l'accès aux tableaux de sécurité Visual Basic.  
  
> [!WARNING]
>  Cet objet est pris en charge dans Internet Explorer uniquement, pas dans les applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
varName = new VBArray(safeArray)   
```  
  
## <a name="parameters"></a>Paramètres  
 `varName`  
 Obligatoire. Nom de la variable à laquelle l’objet VBArray est assigné.  
  
 *safeArray*  
 Obligatoire. Valeur VBArray.  
  
## <a name="remarks"></a>Remarques  
 Les objets VBArray sont en lecture seule et ne peuvent pas être créés directement. L’argument *safeArray* doit avoir obtenu une valeur VBArray avant d’être passé au constructeur VBArray. Cela n’est possible qu’en récupérant la valeur à partir d’un objet ActiveX ou autre existant.  
  
 Les objets VBArray peuvent avoir plusieurs dimensions. Les index de chaque dimension peuvent être différents. La méthode **dimensions** récupère le nombre de dimensions du tableau ; les méthodes `lbound` et `ubound` récupèrent la plage d’index utilisée pour chaque dimension.  
  
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
      document.writeln("<br />")  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
  
<script type="text/javascript">  
<!--  
function VBArrayTest(vbarray){  
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
  
## <a name="properties"></a>Propriétés  
 L’objet `VBArray` n’a pas de propriétés.  
  
## <a name="methods"></a>Méthodes  
 [dimensions, méthode](../../javascript/reference/dimensions-method-vbarray-javascript.md) &#124; [GetItem, méthode](../../javascript/reference/getitem-method-vbarray-javascript.md) &#124; [LBound, méthode](../../javascript/reference/lbound-method-vbarray-javascript.md) &#124; [toArray, méthode](../../javascript/reference/toarray-method-vbarray-javascript.md) &#124; [UBound, méthode](../../javascript/reference/ubound-method-vbarray-javascript.md)  
  
## <a name="requirements"></a>Spécifications  
 Pris en charge dans les modes de document suivants : Quirks, Internet Explorer 6 (mode standard), Internet Explorer 7 (mode standard), Internet Explorer 8 (mode standard), Internet Explorer 9 (mode standard) et Internet Explorer 10 (mode standard). Non pris en charge dans les applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] . Voir [Informations de version](../../javascript/reference/javascript-version-information.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Objet Array](../../javascript/reference/array-object-javascript.md)