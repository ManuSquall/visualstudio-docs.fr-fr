---
title: "Objet d’Expression régulière (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: RegularExpression_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Regular Expression object
- regular expressions, RegExp object
- RegExp object, overview
ms.assetid: 346aa83e-a045-47ea-acae-b42c7b121534
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df2d07e3b47e315ec804e5a7f20024dc2184eef0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="regular-expression-object-javascript"></a>Regular Expression, objet (JavaScript)
Objet qui contient un modèle d’expression régulière ainsi que des indicateurs permettant de déterminer comment appliquer le modèle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
re = /pattern/[flags]  
```  
  
## <a name="syntax"></a>Syntaxe  
  
```  
re = new RegExp("pattern"[,"flags"])   
```  
  
## <a name="parameters"></a>Paramètres  
 *RE*  
 Obligatoire. Nom de la variable à laquelle le modèle d’expression régulière est affecté.  
  
 *modèle*  
 Obligatoire. Modèle d'expression régulière à utiliser. Si vous utilisez la syntaxe 1, délimitez le modèle par des caractères « / ». Si vous utilisez la syntaxe 2, placez le modèle entre des guillemets.  
  
 `flags`  
 Facultatif. Placez l'indicateur entre des guillemets si vous utilisez la syntaxe 2. Les indicateurs disponibles, qui peuvent être combinés, sont :  
  
-   g (recherche globale de toutes les occurrences de *modèle*)  
  
-   i (ignorer la casse)  
  
-   m (recherche multiligne)  
  
-   u (unicode), Active EcmaScript 6 [fonctionnalités Unicode](../../javascript/advanced/special-characters-javascript.md). Pris en charge seulement dans [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)].  
  
-   y (correspondance permanente), recherche les correspondances au niveau de la propriété `lastIndex` de l'expression régulière (et ne recherche pas au niveau des index postérieurs). Pris en charge dans [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)].  
  
## <a name="remarks"></a>Remarques  
 Le **Expression régulière** objet ne doit pas être confondu avec global `RegExp` objet. Même s'ils peuvent sembler identiques, ils sont séparés et distincts. Les propriétés de la **Expression régulière** objet contiennent uniquement des informations sur donné **Expression régulière** les propriétés de l’instance `RegExp` contiennent des objets continuellement mis à jour plus d’informations sur chaque correspondance lorsqu’elle a lieu.  
  
 **Expression régulière** objets stockent les modèles utilisés lors de la recherche de chaînes pour les combinaisons de caractères. Après le **Expression régulière** objet est créé, il est passé à une méthode de chaîne ou une chaîne est passée à une des méthodes d’expression régulière. Les informations sur la recherche la plus récente sont stockées dans l'objet `RegExp` global.  
  
 Utilisez la syntaxe 1 quand vous connaissez la chaîne de recherche à l'avance. Utilisez la syntaxe 2 quand la chaîne de recherche change fréquemment ou si elle est inconnue, comme les chaînes provenant d'une entrée de l'utilisateur.  
  
 Le *modèle* argument est compilé dans un format interne avant son utilisation. Pour la syntaxe 1, *modèle* est compilé au chargement du script. Pour la syntaxe 2, *modèle* est compilé immédiatement avant son emploi, ou lorsque le **compiler** méthode est appelée.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la **Expression régulière** objet en créant un objet (re) contenant un modèle d’expression régulière avec ses indicateurs associés. Dans ce cas, résultant **Expression régulière** objet est ensuite utilisé par le `match` méthode :  
  
```JavaScript  
var s = "through the pages of the book";  
  
// Create regular expression pattern.  
var re = new RegExp("the", "i");  
  
// Attempt match on search string.  
var r = s.match(re);     
  
// Return first occurrence of "the".  
if(console && console.log) {  
    console.log(r);  
}  
  
// Output:  
//   
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant met à jour le modèle d’expression régulière pour rechercher plusieurs instances.  
  
```JavaScript  
// Create regular expression pattern using the i and g flags.  
var re = new RegExp("the", "ig");  
  
// Attempt match on search string.  
var r = s.match(re);     
  
// Return the two occurrences of "the".  
if(console && console.log) {  
    console.log(r.length);  
    console.log(r);  
}  
  
// Output:  
// 2  
// [object Array] ["the", "the"]  
```  
  
## <a name="example"></a>Exemple  
 Quand vous utilisez l'indicateur /y, si une correspondance est établie, il met à jour la propriété `lastindex` vers l'index du caractère suivant après la dernière correspondance. Si la correspondance échoue, la propriété `lastindex` est réinitialisée à 0.  
  
 L'exemple suivant recherche une correspondance à un index spécifique en utilisant l'indicateur /y et la propriété `lastIndex`.  
  
```JavaScript  
// Create regular expression pattern using the i and y flags.  
var re = new RegExp("the", "iy");  
  
// Set the lastIndex property and attempt a match  
// at the specified index.  
re.lastIndex = 20;  
var r = s.match(re);     
  
// No matches returned.  
if(console && console.log) {  
    console.log(r);  
}  
// Reset the lastIndex property and attempt a match.  
re.lastIndex = 21;  
var r = s.match(re);  
  
// Return occurrence of "the" starting at index 21.  
if(console && console.log) {  
    console.log(r);  
}  
  
// Output:  
// null  
// [object Array] ["the"]  
```  
  
<a name="js56jsobjregexpressionprop"></a>   
## <a name="properties"></a>Propriétés  
 [Propriété globale](../../javascript/reference/global-property-regular-expression-javascript.md) &#124; [IgnoreCase, propriété](../../javascript/reference/ignorecase-property-regular-expression-javascript.md) &#124; [multiline, propriété](../../javascript/reference/multiline-property-regular-expression-javascript.md) &#124; [source, propriété](../../javascript/reference/source-property-regular-expression-javascript.md)  
  
<a name="js56jsobjregexpressionmeth"></a>   
## <a name="methods"></a>Méthodes  
 [Compile, méthode](../../javascript/reference/compile-method-regular-expression-javascript.md) &#124; [exec, méthode](../../javascript/reference/exec-method-regular-expression-javascript.md) &#124; [test, méthode](../../javascript/reference/test-method-regular-expression-javascript.md)  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 L'indicateur u est pris en charge dans [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)].  
  
 L'indicateur y est pris en charge dans [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [RegExp (objet)](../../javascript/reference/regexp-object-javascript.md)   
 [Syntaxe d’Expression régulière (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Objet String](../../javascript/reference/string-object-javascript.md)