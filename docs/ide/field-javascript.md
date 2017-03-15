---
title: "&lt;field&gt; (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "<field>, balise XML JavaScript"
  - "field, balise XML JavaScript"
ms.assetid: c494bae0-3095-42a3-aa0a-4c415188c65c
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;field&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Spécifie les informations de documentation, notamment une description, pour le champ ou le membre définis sur un objet.  
  
## Syntaxe  
  
```  
<field name="fieldName" static="true|false"  
    type="FieldType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    helpKeyword="keyword" locid="descriptionID"  
    value="code">description  
</field>  
```  
  
#### Paramètres  
 `name`  
 Le nom du champ ou du membre.  Lorsque l'élément `<field>` est utilisé dans une fonction constructeur, `name` est obligatoire et définit le membre auquel la balise s'applique.  Lorsque l'élément `<field>` annote directement un champ, cet attribut est ignoré, et le nom utilisé par Visual Studio est le nom du champ réel dans le code source.  
  
 `static`  
 Optionnel.  Spécifie si le champ est membre de la fonction constructeur ou un membre de l'objet retourné par la fonction constructeur.  Défini à `true` pour traiter le champ comme membre de la fonction constructeur.  Défini à `false` pour traiter le champ comme membre de l'objet retourné par la fonction constructeur.  
  
 `type`  
 Optionnel.  Type de données du champ.  Le type peut être l'un des suivants :  
  
-   Un type de langage ECMAScript dans la spécification ECMAScript 5, par exemple `Number` ou `Object`.  
  
-   Un objet DOM, tel que `HTMLElement`, `Window`, ou `Document`.  
  
-   Une fonction constructeur JavaScript.  
  
 `integer`  
 Optionnel.  Si `type` est un `Number`, spécifie si le champ est un entier.  Affectez la valeur `true` pour indiquer que le champ est un entier ; sinon, affectez `false`.  Cet attribut n'est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
 `domElement`  
 Optionnel.  Cet attribut est déconseillé ; l'attribut `type` est prioritaire sur ce dernier.  Cet attribut spécifie si le champ documenté est un élément DOM.  Affectez la valeur `true` pour spécifier que le champ est un élément DOM ; sinon, affectez `false`.  Si l'attribut `type` n'est pas défini et `domElement` détient la valeur `true`, IntelliSense traite le champ documenté comme un `HTMLElement` lors de la saisie semi\-automatique des instructions.  
  
 `mayBeNull`  
 Optionnel.  Spécifie si le champ documenté peut être défini comme null.  Affectez la valeur `true` pour indiquer que le champ peut être défini comme null ; sinon, affectez `false`.  La valeur par défaut est `false`.  Cet attribut n'est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
 `elementType`  
 Optionnel.  Si l'attribut `type` est un `Array`, cet attribut précise le type des éléments dans le tableau.  
  
 `elementInteger`  
 Optionnel.  Si `type` est un `Array` et que `elementType` est un `Number`, cet attribut spécifie si les éléments du tableau sont des entiers.  Affectez la valeur `true` pour indiquer que les éléments du tableau sont des entiers ; sinon, affectez `false`.  Cet attribut n'est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
 `elementDomElement`  
 Optionnel.  Cet attribut est déconseillé ; l'attribut `elementType` est prioritaire sur ce dernier.  Si le `type` est un `Array`, cet attribut spécifie si les éléments du tableau sont des éléments DOM.  Affectez la valeur `true` pour spécifier que les éléments sont des éléments DOM ; sinon, affectez `false`.  Si l'attribut `elementType` n'est pas défini et `elementDomElement` détient la valeur `true`, IntelliSense traite chaque élément du tableau comme un `HTMLElement` lors de la saisie semi\-automatique des instructions.  
  
 `elementMayBeNull`  
 Optionnel.  Si le `type` est un `Array`, spécifie si les éléments du tableau peuvent être définis comme null.  Affectez la valeur `true` pour indiquer que les éléments du tableau peuvent être définis comme null ; sinon, affecte `false`.  La valeur par défaut est `false`.  Cet attribut n'est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
 `helpKeyword`  
 Optionnel.  Mot clé pour l'aide F1.  
  
 `locid`  
 Optionnel.  L'identificateur pour les informations de localisation sur le champ.  L'identificateur est soit un membre ID soit il correspond à la valeur d'attribut `name` dans un paquet de message défini par les métadonnées d'OpenAjax.  Le type d'identificateur dépend du format spécifié dans la balise [\<loc\>](../ide/loc-javascript.md).  
  
 `value`  
 Optionnel.  Spécifie le code qui doit être évaluée pour une utilisation par IntelliSense au lieu du code de la fonction lui\-même.  Pour `<field>`, cet attribut est pris en charge pour les fonctions constructeurs, mais n'est pas pris en charge pour les littéraux d'objet.  Il est possible d'utiliser cet attribut pour fournir les informations de type lorsque le type du champ n'est pas défini.  Par exemple, il est possible d'utiliser `value=’1’` pour traiter le type de champ comme un nombre.  
  
 `description`  
 Optionnel.  Description du champ  
  
## Notes  
 L'attribut `name` est requis lorsque vous documentez un champ dans une fonction constructeur.  Pour tous les autres scénarios, tous les attributs de l'élément `<field>` sont facultatifs.  
  
 Lorsque vous documentez une fonction constructeur, l'élément `<field>` doit apparaître immédiatement avant la déclaration de champ.  L'attribut `name` doit correspondre au nom de champ utilisé dans le code source.  Pour les membres d'objet, l'attribut `name` peut être omis si l'élément `<field>` apparaît immédiatement avant la déclaration de membre objet.  
  
## Exemple  
 L'exemple de code suivant montre comment utiliser l'élément `<field>`.  
  
```javascript  
// Use of <field> in an object definition.  
var Rectangle = {  
    /// <field type='Number'>The width of the rectangle.</field>  
    wid: 5,  
    /// <field type='Number'>The length of the rectangle.</field>  
    len: 0,  
    /// <field type='Number'>Returns the area of the rectangle.</field>  
    getArea: function (wid, len) {  
        return len * wid;  
    }  
}  
  
// Use of <field> in a constructor function.  
// The name attribute is required.  
function Engine() {  
    /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>  
    this.HorsePower = 150;  
}  
```  
  
## Exemple  
 L'exemple suivant montre comment utiliser l'élément `<field>` avec l'attribut `static` défini à `true`.  
  
```javascript  
function Engine() {  
    /// <field name='HorsePower' static='true' type='Number'>static field desc.</field>  
}  
  
Engine.HorsePower = 140;  
// IntelliSense on the field is available here.  
Engine.  
  
```  
  
## Exemple  
 L'exemple suivant montre comment utiliser l'élément `<field>` avec l'attribut `static` défini à `false`.  
  
```javascript  
function Engine() {  
    /// <field name='HorsePower' static='false' type='Number'>Non-static field desc.</field>  
}  
  
Engine.HorsePower = 140;  
var eng = new Engine();  
// IntelliSense on the field is available here.  
eng.  
  
```  
  
## Exemple  
 L'exemple suivant montre comment utiliser l'élément `<field>` avec l'attribut `value`.  
  
```javascript  
function calculator(a) {  
    /// <field name='f' value='1'/>  
}  
new calculator().f.   // Completion list for a Number.  
  
```  
  
## Voir aussi  
 [Commentaires sur la documentation XML](../ide/xml-documentation-comments-javascript.md)