---
title: RegExp, objet (JavaScript) | Documents Microsoft
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
- RegExp
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- RegExp object, overview
- RegExp object
ms.assetid: 7f6b1073-8cbb-49ed-94b6-56833ba663c5
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7319e4556721bcfd397061ce525acfb3278c6b9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640779"
---
# <a name="regexp-object-javascript"></a>RegExp, objet (JavaScript)
Un objet global intrinsèque qui stocke des informations sur les résultats du modèle d’expression régulière correspond à.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RegExp.property   
```  
  
## <a name="remarks"></a>Remarques  
 Requis *propriété* argument peut prendre l’une de le `RegExp` propriétés de l’objet.  
  
 Le `RegExp` objet ne peut pas être créé directement, mais il est toujours disponible pour utilisation. Jusqu'à ce qu’une recherche d’expression régulière réussie a été effectuée, les valeurs initiales des propriétés différentes de la `RegExp` objet sont les suivantes :  
  
|Propriété|Forme abrégée|Valeur initiale|  
|--------------|---------------|-------------------|  
|index||-1|  
|entrée|$_|Chaîne vide.|  
|propriété lastIndex||-1|  
|lastMatch|$&|Chaîne vide.|  
|lastParen|$+|Chaîne vide.|  
|leftContext|$`|Chaîne vide.|  
|rightContext|$'|Chaîne vide.|  
|$1 - $9|$1 - $9|Chaîne vide.|  
  
 Ses propriétés ont non défini en tant que leur valeur jusqu'à ce qu’une recherche d’expression régulière réussie a été effectuée.  
  
 Global `RegExp` objet ne doit pas être confondu avec le **Expression régulière** objet. Même s’ils peuvent sembler comme la même chose, ils sont séparés et distincts. Les propriétés de l’élément global `RegExp` objet contiennent des informations continuellement mises à jour sur chaque correspondance lorsqu’il se produit, les propriétés de la **Expression régulière** objet contiennent uniquement des informations sur les correspondances qui se produisent avec cette instance de la **Expression régulière**.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant effectue une recherche d’expression régulière. Il affiche des correspondances et submatches à partir du global `RegExp` objet et à partir du tableau retourné par la `exec` (méthode).  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
<a name="js56jsobjregexpprop"></a>   
## <a name="properties"></a>Propriétés  
 [$1... $9, propriétés](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md) &#124; [index, propriété](../../javascript/reference/index-property-regexp-javascript.md) &#124; [input, propriété](../../javascript/reference/input-property-dollar-regexp-javascript.md) &#124; [lastIndex, propriété](../../javascript/reference/lastindex-property-regexp-javascript.md) &#124; [lastMatch, propriété](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md) &#124; [lastParen, propriété](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md) &#124; [leftContext, propriété](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md) &#124; [rightContext, propriété](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)  
  
## <a name="methods"></a>Méthodes  
 Le `RegExp` objet ne possède pas de méthodes.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Objet d’Expression régulière](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntaxe d’Expression régulière (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Objet String](../../javascript/reference/string-object-javascript.md)