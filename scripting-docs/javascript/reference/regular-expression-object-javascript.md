---
title: "Regular Expression, objet (JavaScript) | Microsoft Docs"
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
  - "RegularExpression_JavaScript"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "RegExp (objet), vue d'ensemble"
  - "Regular Expression (objet)"
  - "expressions régulières, RegExp (objet)"
ms.assetid: 346aa83e-a045-47ea-acae-b42c7b121534
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# Regular Expression, objet (JavaScript)
Objet qui contient un modèle d'expression régulière ainsi que des indicateurs permettant de déterminer comment appliquer le modèle.  
  
## Syntaxe  
  
```  
re = /pattern/[flags]  
```  
  
## Syntaxe  
  
```  
re = new RegExp("pattern"[,"flags"])   
```  
  
## Paramètres  
 *re*  
 Obligatoire.  Nom de la variable à laquelle le modèle d'expression régulière est affecté.  
  
 *pattern*  
 Obligatoire.  Modèle d'expression régulière à utiliser.  Si vous utilisez la syntaxe 1, délimitez le modèle par des caractères « \/ ».  Si vous utilisez la syntaxe 2, placez le modèle entre des guillemets.  
  
 `flags`  
 Facultatif.  Placez l'indicateur entre des guillemets si vous utilisez la syntaxe 2.  Les indicateurs disponibles, qui peuvent être combinés, sont :  
  
-   g \(recherche globale de toutes les occurrences de *modèle*\)  
  
-   i \(ignorer la casse\)  
  
-   m \(recherche multiligne\)  
  
-   u \(unicode\), active les [fonctionnalités Unicode](../../javascript/advanced/special-characters-javascript.md) EcmaScript 6.  Pris en charge seulement dans [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)].  
  
-   y \(correspondance permanente\), recherche les correspondances au niveau de la propriété `lastIndex` de l'expression régulière \(et ne recherche pas au niveau des index postérieurs\).  Pris en charge dans [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)].  
  
## Notes  
 L'objet **Expression régulière** ne doit pas être confondu avec l'objet `RegExp` global.  Même s'ils peuvent sembler identiques, ils sont séparés et distincts.  Les propriétés de l'objet **Expression régulière** contiennent seulement des informations sur une instance **Expression régulière** particulière, alors que les propriétés de l'objet `RegExp` global contiennent des informations mises à jour en permanence sur chaque correspondance quand elle se produit.  
  
 Les objets **Expression régulière** stockent des modèles utilisés lors de la recherche de chaînes pour des combinaisons de caractères.  Une fois l'objet **Expression régulière** créé, il est passé à une méthode de chaîne ou bien une chaîne est passée à une des méthodes d'expression régulière.  Les informations sur la recherche la plus récente sont stockées dans l'objet `RegExp` global.  
  
 Utilisez la syntaxe 1 quand vous connaissez la chaîne de recherche à l'avance.  Utilisez la syntaxe 2 quand la chaîne de recherche change fréquemment ou si elle est inconnue, comme les chaînes provenant d'une entrée de l'utilisateur.  
  
 L'argument *pattern* est compilé dans un format interne avant d'être utilisé.  Pour la syntaxe 1, *pattern* est compilé au chargement du script.  Pour la syntaxe 2, *pattern* est compilé immédiatement avant d'être utilisé ou quand la méthode **compile** est appelée.  
  
## Exemple  
 L'exemple suivant montre l'utilisation de l'objet **Expression régulière** en créant un objet \(re\) contenant un modèle d'expression régulière avec ses indicateurs associés.  Dans ce cas, l'objet **Expression régulière** résultant est ensuite utilisé par la méthode `match` :  
  
```javascript  
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
  
## Exemple  
 L'exemple suivant met à jour le modèle d'expression régulière pour rechercher plusieurs instances.  
  
```javascript  
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
  
## Exemple  
 Quand vous utilisez l'indicateur \/y, si une correspondance est établie, il met à jour la propriété `lastindex` vers l'index du caractère suivant après la dernière correspondance.  Si la correspondance échoue, la propriété `lastindex` est réinitialisée à 0.  
  
 L'exemple suivant recherche une correspondance à un index spécifique en utilisant l'indicateur \/y et la propriété `lastIndex`.  
  
```javascript  
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
## Propriétés  
 [Propriété global](../../javascript/reference/global-property-regular-expression-javascript.md) &#124; [Propriété ignoreCase](../../javascript/reference/ignorecase-property-regular-expression-javascript.md) &#124; [Propriété multiline](../../javascript/reference/multiline-property-regular-expression-javascript.md) &#124; [Propriété source](../../javascript/reference/source-property-regular-expression-javascript.md)  
  
<a name="js56jsobjregexpressionmeth"></a>   
## Méthodes  
 [Méthode compile](../../javascript/reference/compile-method-regular-expression-javascript.md) &#124; [Méthode exec](../../javascript/reference/exec-method-regular-expression-javascript.md) &#124; [Méthode test](../../javascript/reference/test-method-regular-expression-javascript.md)  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 L'indicateur u est pris en charge dans [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)].  
  
 L'indicateur y est pris en charge dans [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)].  
  
## Voir aussi  
 [RegExp, objet](../../javascript/reference/regexp-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/fr-fr/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [String, objet](../../javascript/reference/string-object-javascript.md)