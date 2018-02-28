---
title: Informations de Version JavaScript | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- JavaScript, version information
ms.assetid: 440f4924-f7a9-48e0-873e-bd599a93b437
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b0503abb3d62e9fd61149b884a7b58a685fbc62c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="javascript-version-information"></a>Informations de version JavaScript
Les différentes versions de JavaScript prennent en charge différents ensembles d'éléments JavaScript. Les applications[!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] prennent en charge un ensemble de fonctionnalités légèrement différent par rapport à Internet Explorer.  
  
> [!IMPORTANT]
>  Une application du [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] est un nouveau type d'application qui s'exécute sur les périphériques [!INCLUDE[win8](../../javascript/includes/win8-md.md)] . Pour plus d’informations sur les applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] , consultez [What's a Windows Store app?](http://msdn.microsoft.com/en-us/231c1fba-9f87-468e-94aa-45dd57edcc70)  
  
 Le mode standard (le mode utilisé dans toutes les versions d'Internet Explorer jusqu'à Internet Explorer 11 en présence d'une directive `<!doctype>` ) prend en charge un autre ensemble d'éléments que le mode Quirks (utilisé en l'absence de directive `<!doctype>` ). Pour plus d’informations sur le contrôle de version, consultez [Définition de la compatibilité des documents](http://go.microsoft.com/fwlink/?LinkId=208537).  
  
 Le tableau suivant montre les modes de document Internet Explorer (et les applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] et [!INCLUDE[winphone_appname](../../javascript/reference/includes/winphone-appname-md.md)]) qui prennent en charge les éléments de langage spécifiques. Les modes de document qui prennent en charge un élément donné sont identifiés par la lettre **Y**et ceux qui ne prennent pas en charge un élément donné sont identifiés par la lettre **N**.  
  
> [!IMPORTANT]
>  Le [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)] (navigateur Edge dans Windows 10) n'inclut pas de prise en charge des modes de document hérités. La prise en charge des applications [!INCLUDE[winphone_appname](../../javascript/reference/includes/winphone-appname-md.md)] commence par Windows Phone 8.1. Fonctionnalités expérimentales (sur : flags) sont signalées par « Exp ».  
  
 Le tableau contient des informations résumées. Pour plus d'informations, consultez la documentation de l'élément de langage.  
  
|Élément du langage|Quirks, Internet Explorer 6 (mode standard) et Internet Explorer 7 (mode standard)|Internet Explorer 8 (mode standard)|Internet Explorer 9 (mode standard)|Internet Explorer 10 (mode standard)|Internet Explorer 11 (mode standard)|Microsoft Edge|Applications de Store|  
|----------------------|--------------------------------------------------------------------------|-----------------------------------|-----------------------------------|------------------------------------|------------------------------------|----------|----------------|  
|[__proto\_ \_ , propriété (objet)](../../javascript/reference/proto-property-object-javascript.md)|N|N|N|N|Y|Y|v8 (Win) : N<br />v8.1 (Win) : Y<br />v8.1 (Phone) : Y|  
|[Propriétés $1...$9 (RegExp)](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Propriété 0n](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction abs](../../javascript/reference/math-abs-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction acos](../../javascript/reference/math-acos-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[acosh, fonction](../../javascript/reference/math-acosh-function-javascript.md)|N|N|N|N|N|Y|v8.1 : N<br />v10 : Y|  
|[Objet ActiveXObject](../../javascript/reference/activexobject-object-javascript.md)|Y|Y|Y|Y|Y|Y|N|  
|[Opérateur d'assignation d'addition (+=)](../../javascript/reference/addition-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Opérateur d'addition (+)](../../javascript/reference/addition-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode apply](../../javascript/reference/apply-method-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Objet arguments](../../javascript/reference/arguments-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Propriété arguments](../../javascript/reference/arguments-property-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Objet Array](../../javascript/reference/array-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction Array.from (Array)](../../javascript/reference/array-from-function-array-javascript.md)|N|N|N|N|N|N|v8.1 : N<br />v10 : Y|  
|[Fonction Array.isArray](../../javascript/reference/array-isarray-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Fonction Array.of (Array)](../../javascript/reference/array-of-function-array-javascript.md)|N|N|N|N|N|N|v8.1 : N<br />v10 : Y|  
|[Objet ArrayBuffer](../../javascript/reference/arraybuffer-object.md)|N|N|N|Y|Y|Y|Y|  
|[Fonctions](../../javascript/functions-javascript.md)|N|N|N|N|N|N|v8.1 : N<br />v10 : Y|  
|[Fonction asin](../../javascript/reference/math-asin-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction Object.assign (Object)](../../javascript/reference/object-assign-function-object-javascript.md)|N|N|N|N|N|N|v8.1 : N<br />v10 : Y|  
|[Opérateur d'assignation (=)](../../javascript/reference/assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction atan](../../javascript/reference/math-atan-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction atan2](../../javascript/reference/math-atan2-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode atEnd](../../javascript/reference/atend-method-enumerator-javascript.md)|Y|Y|Y|Y|Y|Y|N|  
|[Méthode bind](../../javascript/reference/bind-method-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Opérateur d'assignation de bits AND (&=)](../../javascript/reference/bitwise-and-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[&, opérateur de bits AND](../../javascript/reference/bitwise-and-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Au niveau du bit opérateur Left Shift (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[~, opérateur de bits NOT](../../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Au niveau du bit ou opérateur d’assignation (&#124; =)](../../javascript/reference/bitwise-or-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Au niveau du bit OR (opérateur &#124;)](../../javascript/reference/bitwise-or-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[>> (décalage vers la droite), opérateur de bits](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[^=, opérateur d'assignation de bits YOR](../../javascript/reference/bitwise-xor-assignment-operator-decrement-hat-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[^, opérateur de bits YOR](../../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode blink](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode bold](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Objet Boolean](../../javascript/reference/boolean-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Instruction break](../../javascript/reference/break-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode call](../../javascript/reference/call-method-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Propriété callee](../../javascript/reference/callee-property-arguments-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Propriété caller](../../javascript/reference/caller-property-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[catch, instruction](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction ceil](../../javascript/reference/math-ceil-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode charAt](../../javascript/reference/charat-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode charCodeAt](../../javascript/reference/charcodeat-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Instruction class](../../javascript/reference/class-statement-javascript.md)|N|N|N|N|N|Exp.|v8.1 : N<br />v10 : Exp.|  
|[codePointAt, méthode (String)](../../javascript/reference/codepointat-method-string-javascript.md)|N|N|N|N|N|Y|v8.1 : N<br />v10 : Y|  
|[Opérateur virgule (,)](../../javascript/reference/comma-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[// (instruction de commentaire sur une seule ligne)](../../javascript/reference/comment-statements-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[/*.. \*/ (Instruction de commentaire multiligne)](../../javascript/reference/comment-statements-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Opérateurs de comparaison](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode compile](../../javascript/reference/compile-method-regular-expression-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode concat (tableau)](../../javascript/reference/concat-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode concat (Chaîne)](../../javascript/reference/concat-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Compilation conditionnelle](../../javascript/advanced/conditional-compilation-javascript.md)|Y|Y|Y|Y|N|N|N|  
|[Variables de compilation conditionnelle](../../javascript/advanced/conditional-compilation-variables-javascript.md)|Y|Y|Y|Y|N|N|N|  
|[?: (conditionnel ternaire), opérateur](../../javascript/reference/conditional-ternary-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[constructor, propriété](../../javascript/reference/constructor-property-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Instruction const](../../javascript/reference/const-statement-javascript.md)|N|N|N|N|Y|Y|v8 (Win) : N<br />v8.1 (Win) : Y<br />v8.1 (Phone) : Y|  
|[Instruction continue](../../javascript/reference/continue-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction cos](../../javascript/reference/math-cos-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction create](../../javascript/reference/object-create-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Objet DataView](../../javascript/reference/dataview-object.md)|N|N|N|Y|Y|Y|Y|  
|[Objet Date](../../javascript/reference/date-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Objet Debug](../../javascript/reference/debug-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Propriété Debug.setNonUserCodeExceptions](../../javascript/reference/debug-setnonusercodeexceptions-property.md)|N|N|N|Y|Y|Y|Y|  
|[Propriété Debug.setNonUserCodeExceptions](../../javascript/reference/debug-setnonusercodeexceptions-property.md)|N|N|N|Y|Y|Y|Y|  
|[Instruction debugger](../../javascript/reference/debugger-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction decodeURI](../../javascript/reference/decodeuri-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction DecodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[-- (décrémentation), opérateur](../../javascript/reference/increment-and-decrement-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonctions](../../javascript/functions-javascript.md)|N|N|N|N|N|Exp.|v8.1 : N<br />v10 : Exp.|  
|[Fonction defineProperties](../../javascript/reference/object-defineproperties-function-javascript.md)|N|Y*|Y|Y|Y|Y|Y|  
|[Fonction defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md)|N|Y*|Y|Y|Y|Y|Y|  
|[Opérateur delete](../../javascript/reference/delete-operator-decrementjavascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Propriété description](../../javascript/reference/description-property-error-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode dimensions](../../javascript/reference/dimensions-method-vbarray-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Opérateur d'assignation division (/=)](../../javascript/reference/division-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Opérateur Division (/)](../../javascript/reference/division-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Instruction do...while](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Constante E](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction encodeURI](../../javascript/reference/encodeuri-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction de composant encodeURI](../../javascript/reference/encodeuricomponent-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode entries (Array)](../../javascript/reference/entries-method-array-javascript.md)|N|N|N|N|N|N|v8.1 : N<br />v10 : Y|  
|[Objet Enumerator](../../javascript/reference/enumerator-object-javascript.md)|Y|Y|Y|Y|Y|Y|N|  
|[Constantes Number](../../javascript/reference/number-constants-javascript.md)|N|N|N|N|N|N|v8.1 : N<br />v10 : Y|  
|[== (égalité), opérateur](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Objet Error](../../javascript/reference/error-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Propriété stack (Error)](../../javascript/reference/stack-property-error-javascript.md)|N|N|N|Y|Y|Y|Y|  
|[Propriété stackTraceLimit (Error)](../../javascript/reference/stacktracelimit-property-error-javascript.md)|N|N|N|Y|Y|Y|Y|  
|[Fonction escape](../../javascript/reference/escape-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction eval](../../javascript/reference/eval-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode exec](../../javascript/reference/exec-method-regular-expression-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode every](../../javascript/reference/every-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Fonction exp](../../javascript/reference/math-exp-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode fill (Array)](../../javascript/reference/fill-method-array-javascript.md)|N|N|N|N|N|N|v8.1 : N<br />v10 : Y|  
|[Méthode filter](../../javascript/reference/filter-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Instruction finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode findIndex (Array)](../../javascript/reference/findindex-method-array-javascript.md)|N|N|N|N|N|N|v8.1 : N<br />v10 : Y|  
|[Méthode fixed](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Objet Float32Array](../../javascript/reference/float32array-object.md)|N|N|N|Y|Y|Y|Y|  
|[Objet Float64Array](../../javascript/reference/float64array-object.md)|N|N|N|Y|Y|Y|Y|  
|[Fonction floor](../../javascript/reference/math-floor-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode fontcolor](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode fontsize](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Instruction for](../../javascript/reference/for-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode forEach](../../javascript/reference/foreach-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Instruction for...in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Instruction for...of](../../javascript/reference/for-dot-dot-dot-of-statement-javascript.md)|N|N|N|N|N|Y|v8.1 : N<br />v10 : Y|  
|[Fonction freeze](../../javascript/reference/object-freeze-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Fonction fromCharCode](../../javascript/reference/string-fromcharcode-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction fromCodePoint](../../javascript/reference/string-fromcodepoint-function-javascript.md)|N|N|N|N|N|Y|v8.1 : N<br />v10 : Y|  
|[Objet de function](../../javascript/reference/function-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Instruction function](../../javascript/reference/function-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Générateurs](../../javascript/advanced/iterators-and-generators-javascript.md)|N|N|N|N|N|Exp.|v8.1 : N<br />v10 : Exp.|  
|[Méthode getDate](../../javascript/reference/getdate-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode getDay](../../javascript/reference/getday-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode getFullYear](../../javascript/reference/getfullyear-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode getHours](../../javascript/reference/gethours-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode getItem](../../javascript/reference/getitem-method-vbarray-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode getMilliseconds](../../javascript/reference/getmilliseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode getMinutes](../../javascript/reference/getminutes-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode getMonth](../../javascript/reference/getmonth-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction GetObject](../../javascript/reference/getobject-function-javascript.md)|Y|Y|N|N|N|N|N|  
|[Fonction getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)|N|Y*|Y|Y|Y|Y|Y|  
|[Fonction getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Fonction getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Méthode getSeconds](../../javascript/reference/getseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode getTime](../../javascript/reference/gettime-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode getTimezoneOffset](../../javascript/reference/gettimezoneoffset-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode getUTCDate](../../javascript/reference/getutcdate-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode getUTCDay](../../javascript/reference/getutcday-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode getUTCFullYear](../../javascript/reference/getutcfullyear-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode getUTCHours](../../javascript/reference/getutchours-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode getUTCMilliseconds](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode getUTCMinutes](../../javascript/reference/getutcminutes-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode getUTCMonth](../../javascript/reference/getutcmonth-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode getUTCSeconds](../../javascript/reference/getutcseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode getVarDate](../../javascript/reference/getvardate-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|N|  
|[Méthode getYear](../../javascript/reference/getyear-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Objet Global](../../javascript/reference/global-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Propriété global](../../javascript/reference/global-property-regular-expression-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Opérateur Supérieur à (>)](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Opérateur Supérieur ou égal à (>=)](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode hasOwnProperty](../../javascript/reference/hasownproperty-method-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthodes de balisage HTML](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[hypot, fonction](../../javascript/reference/math-hypot-function-javascript.md)|N|N|N|N|N|Y|v8.1 : N<br />v10 : Y|  
|[Opérateur d'identité (===)](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Instruction if...else](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Propriété ignoreCase](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction imul](../../javascript/reference/math-imul-function-javascript.md)|N|N|N|N|N|Y|v8.1 : N<br />v10 : Y|  
|[Opérateur In](../../javascript/reference/in-operator-decrementjavascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[includes, méthode (String)](../../javascript/reference/includes-method-string-javascript.md)|N|N|N|N|N|Y|v8.1 : N<br />v10 : Y|  
|[++ (incrémentation), opérateur](../../javascript/reference/increment-and-decrement-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Propriété index](../../javascript/reference/index-property-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode indexOf (tableau)](../../javascript/reference/indexof-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Méthode indexOf (chaîne)](../../javascript/reference/indexof-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[!= (inégalité), opérateur](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Constante Infinity](../../javascript/reference/infinity-constant-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Propriété input ($_)](../../javascript/reference/input-property-dollar-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Opérateur instanceof](../../javascript/reference/instanceof-operator-decrementjavascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Objet Int8Array](../../javascript/reference/int8array-object.md)|N|N|N|Y|Y|Y|Y|  
|[Objet Int16Array](../../javascript/reference/int16array-object.md)|N|N|N|Y|Y|Y|Y|  
|[Objet Int32Array](../../javascript/reference/int32array-object.md)|N|N|N|Y|Y|Y|Y|  
|[Objet Intl.Collator](../../javascript/reference/intl-collator-object-javascript.md)|N|N|N|N|Y|Y|v8 (Win) : N<br />v8.1 (Win) : Y<br />v8.1 (Phone) : Y|  
|[Objet Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md)|N|N|N|N|Y|Y|v8 : N<br />v8.1 : Y|  
|[Objet Intl.NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md)|N|N|N|N|Y|Y|v8 : N<br />v8.1 : Y|  
|[Fonction isFinite](../../javascript/reference/isfinite-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction isArray](../../javascript/reference/array-isarray-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Fonction IsExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Fonction isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Fonction isInteger](../../javascript/reference/number-isinteger-function-number-javascript.md)|N|N|N|N|N|Y|v8.1 : N<br />v10 : Y|  
|[Fonction isNaN](../../javascript/reference/isnan-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction isNaN (Number)](../../javascript/reference/number-isnan-function-number-javascript.md)|N|N|N|N|N|Y|v8.1 : N<br />v10 : Y|  
|[Format de date ISO](../../javascript/date-and-time-strings-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Méthode IsPrototypeOf](../../javascript/reference/isprototypeof-method-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction isSealed](../../javascript/reference/object-issealed-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Méthode italics](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Itérateurs](../../javascript/advanced/iterators-and-generators-javascript.md)|N|N|N|N|N|Y|v8.1 : N<br />v10 : Y|  
|[Méthode item](../../javascript/reference/item-method-enumerator-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode join](../../javascript/reference/join-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Objet JSON](../../javascript/reference/json-object-javascript.md)|N|Y|Y|Y|Y|Y|Y|  
|[Fonction keys](../../javascript/reference/object-keys-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Méthode keys (Array)](../../javascript/reference/keys-method-array-javascript.md)|N|N|N|N|N|Y|v8.1 : N<br />v10 : Y|  
|[Instruction étiquetée](../../javascript/reference/labeled-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Propriété lastIndex](../../javascript/reference/lastindex-property-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode lastIndexOf (tableau)](../../javascript/reference/lastindexof-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Méthode lastIndexOf (Chaîne)](../../javascript/reference/lastindexof-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Propriété lastMatch ($&)](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Propriété lastParen ($+)](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode lbound](../../javascript/reference/lbound-method-vbarray-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Propriété leftContext ($')](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[<<= (décalage vers la gauche), opérateur d'assignation](../../javascript/reference/left-shift-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Propriété length (Arguments)](../../javascript/reference/length-property-arguments-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[length, propriété (tableau)](../../javascript/reference/length-property-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Propriété length (Fonction)](../../javascript/reference/length-property-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Propriété length (Chaîne)](../../javascript/reference/length-property-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Opérateur Inférieur à (<)](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Opérateur Inférieur ou égal à (<=)](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Instruction let](../../javascript/reference/let-statement-javascript.md)|N|N|N|N|Y|Y|v8 : N<br />v8.1 : Y|  
|[Méthode link](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Constante LN2](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Constante LN10](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[méthode localeCompare](../../javascript/reference/localecompare-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction log](../../javascript/reference/math-log-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Constante LOG2E](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Constante LOG10E](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[&& (AND logique), opérateur](../../javascript/reference/logical-and-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[! (NOT logique), opérateur](../../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Opérateur logique OR (opérateur &#124; &#124;)](../../javascript/reference/logical-or-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode map](../../javascript/reference/map-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Objet Map](../../javascript/reference/map-object-javascript.md)|N|N|N|N|Y|Y|v8 : N<br />v8.1 : Y|  
|[Méthode match](../../javascript/reference/match-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Objet Math](../../javascript/reference/math-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction max](../../javascript/reference/math-max-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Constante MAX_VALUE](../../javascript/reference/number-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Propriété message](../../javascript/reference/message-property-error-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction min](../../javascript/reference/math-min-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Constante MIN_VALUE](../../javascript/reference/number-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Opérateur d'assignation de module (%=)](../../javascript/reference/modulus-assignment-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Opérateur de module (%)](../../javascript/reference/modulus-operator-decrementjavascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode moveFirst](../../javascript/reference/movefirst-method-enumerator-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode moveNext](../../javascript/reference/movenext-method-enumerator-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Propriété multiline](../../javascript/reference/multiline-property-regular-expression-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Opérateur d'assignation de multiplication (*=)](../../javascript/reference/multiplication-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Opérateur Multiplication (*)](../../javascript/reference/multiplication-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Propriété name](../../javascript/reference/name-property-error-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Constante NaN (Global)](../../javascript/reference/nan-constant-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Constante NaN (Nombre)](../../javascript/reference/number-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Constante NEGATIVE_INFINITY](../../javascript/reference/number-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Opérateur new](../../javascript/reference/new-operator-decrementjavascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[!== (non-identité), opérateur](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction now](../../javascript/reference/date-now-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Objet Number](../../javascript/reference/number-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Propriété number](../../javascript/reference/number-property-error-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Objet Object](../../javascript/reference/object-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction Date.parse](../../javascript/reference/date-parse-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction JSON.parse](../../javascript/reference/json-parse-function-javascript.md)|N|Y|Y|Y|Y|Y|Y|  
|[Fonction parseFloat](../../javascript/reference/parsefloat-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction parseInt](../../javascript/reference/parseint-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Constante PI](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode pop](../../javascript/reference/pop-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Constante POSITIVE_INFINITY](../../javascript/reference/number-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction pow](../../javascript/reference/math-pow-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Promise, objet](../../javascript/reference/promise-object-javascript.md)|N|N|N|N|N|Y|v8.1 : N<br />v10 : Y|  
|[prototype, propriété](../../javascript/reference/prototype-property-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode propertyIsEnumerable](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Objet proxy](../../javascript/reference/proxy-object-javascript.md)|N|N|N|N|N|Y|v8.1 : N<br />v10 : Y|  
|[Méthode push](../../javascript/reference/push-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction random](../../javascript/reference/math-random-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction raw](../../javascript/reference/string-raw-function-javascript.md)|N|N|N|N|N|Y|v8.1 : N<br />v10 : Y|  
|[Méthode reduce](../../javascript/reference/reduce-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Méthode reduceRight](../../javascript/reference/reduceright-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Objet RegExp](../../javascript/reference/regexp-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Objet Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Syntaxe d'une expression régulière](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)|Y|Y|Y|Y|Y|Y|Y|  
|[Indicateur /y d'expression régulière](../../javascript/reference/regular-expression-object-javascript.md)|N|N|N|N|N|Exp.|v8.1 : N<br />v10 : Exp.|  
|[Méthode repeat (String)](../../javascript/reference/repeat-method-string-javascript.md)|N|N|N|N|N|Y|v8.1 : N<br />v10 : Y|  
|[Méthode replace](../../javascript/reference/replace-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonctions](../../javascript/functions-javascript.md)|N|N|N|N|N|N|v8.1 : N<br />v10 : Y|  
|[Instruction return](../../javascript/reference/return-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode reverse](../../javascript/reference/reverse-method-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Propriété rightContext ($')](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[>>= (décalage vers la droite), opérateur d'assignation](../../javascript/reference/right-shift-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction round](../../javascript/reference/math-round-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction ScriptEngine](../../javascript/reference/scriptengine-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction ScriptEngineBuildVersion](../../javascript/reference/scriptenginebuildversion-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction ScriptEngineMajorVersion](../../javascript/reference/scriptenginemajorversion-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction ScriptEngineMinorVersion](../../javascript/reference/scriptengineminorversion-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction seal](../../javascript/reference/object-seal-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Méthode search](../../javascript/reference/search-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Objet Set](../../javascript/reference/set-object-javascript.md)|N|N|N|N|Y|Y|v8 : N<br />v8.1 : Y|  
|[Méthode setDate](../../javascript/reference/setdate-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode setFullYear](../../javascript/reference/setfullyear-method-date-javascript.md)||Y|Y|Y|Y|Y|Y|  
|[Méthode setHours](../../javascript/reference/sethours-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode setMilliseconds](../../javascript/reference/setmilliseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode setMinutes](../../javascript/reference/setminutes-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode setMonth](../../javascript/reference/setmonth-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode setSeconds](../../javascript/reference/setseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode setTime](../../javascript/reference/settime-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode setUTCDate](../../javascript/reference/setutcdate-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode setUTCFullYear](../../javascript/reference/setutcfullyear-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode setUTCHours](../../javascript/reference/setutchours-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode setUTCMilliseconds](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode setUTCMinutes](../../javascript/reference/setutcminutes-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode setUTCMonth](../../javascript/reference/setutcmonth-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode setUTCSeconds](../../javascript/reference/setutcseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode setYear](../../javascript/reference/setyear-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode shift](../../javascript/reference/shift-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction sin](../../javascript/reference/math-sin-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode slice (tableau)](../../javascript/reference/slice-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode slice (Chaîne)](../../javascript/reference/slice-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode small](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode some](../../javascript/reference/some-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Méthode sort](../../javascript/reference/sort-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Propriété source](../../javascript/reference/source-property-regular-expression-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode splice](../../javascript/reference/splice-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode split](../../javascript/reference/split-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonctions](../../javascript/functions-javascript.md)|N|N|N|N|N|Y|v8.1 : N<br />v10 : Y|  
|[Fonction sqrt](../../javascript/reference/math-sqrt-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Constante SQRT1_2](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Constante SQRT2](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Directive use strict](../../javascript/reference/use-strict-directive.md)|N|N|N|Y|Y|Y|Y|  
|[Méthode strike](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Objet String](../../javascript/reference/string-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md)|N|Y|Y|Y|Y|Y|Y|  
|[Méthode sub](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode substr](../../javascript/reference/substr-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode substring](../../javascript/reference/substring-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Opérateur d'assignation de soustraction (-=)](../../javascript/reference/subtraction-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Opérateur de soustraction (-)](../../javascript/reference/subtraction-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode sup](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Instruction switch](../../javascript/reference/switch-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Symbol, objet](../../javascript/reference/symbol-object-javascript.md)|N|N|N|N|N|Y|v8.1 : N<br />v10 : Y|  
|[Fonction tan](../../javascript/reference/math-tan-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Chaînes de modèle](../../javascript/advanced/template-strings-javascript.md)|N|N|N|N|N|Y|v8.1 : N<br />v10 : Y|  
|[test, méthode](../../javascript/reference/test-method-regular-expression-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Instruction this](../../javascript/reference/this-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Instruction throw](../../javascript/reference/throw-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode toArray](../../javascript/reference/toarray-method-vbarray-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode toDateString](../../javascript/reference/todatestring-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode toExponential](../../javascript/reference/toexponential-method-number-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode toFixed](../../javascript/reference/tofixed-method-number-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode toGMTString](../../javascript/reference/togmtstring-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode toISOString](../../javascript/reference/toisostring-method-date-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Méthode toJSON](../../javascript/reference/tojson-method-date-javascript.md)|N|Y|Y|Y|Y|Y|Y|  
|[Méthode toLocaleDateString](../../javascript/reference/tolocaledatestring-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode toLocaleLowercase](../../javascript/reference/tolocalelowercase-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode toLocaleString](../../javascript/reference/tolocalestring-method-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode toLocaleTimeString](../../javascript/reference/tolocaletimestring-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode toLocaleUppercase](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode toLowerCase](../../javascript/reference/tolowercase-method-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode toPrecision](../../javascript/reference/toprecision-method-number-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode toString](../../javascript/reference/tostring-method-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode toTimeString](../../javascript/reference/totimestring-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode toUpperCase](../../javascript/reference/touppercase-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode toUTCString](../../javascript/reference/toutcstring-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode trim](../../javascript/reference/trim-method-string-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Méthode try](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Opérateur typeof](../../javascript/reference/typeof-operator-decrementjavascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode ubound](../../javascript/reference/ubound-method-vbarray-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Objet Uint8Array](../../javascript/reference/uint8array-object.md)|N|N|N|Y|Y|Y|Y|  
|[Objet Uint16Array](../../javascript/reference/uint16array-object.md)|N|N|N|Y|Y|Y|Y|  
|[Objet Uint32Array](../../javascript/reference/uint32array-object.md)|N|N|N|Y|Y|Y|Y|  
|[Objet Uint8ClampedArray](../../javascript/reference/uint8clampedarray-object-javascript.md)|N|N|N|N|Y|Y|v8 : N<br />v8.1 (Win) : Y<br />v8.1 (Phone) : N<br />v10 : Y|  
|[- (négation unaire), opérateur](../../javascript/reference/subtraction-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Constante undefined](../../javascript/reference/undefined-constant-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction unescape](../../javascript/reference/unescape-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Caractères d'échappement de point de code Unicode](../../javascript/advanced/special-characters-javascript.md)|N|N|N|N|N|Y|v8.1 : N<br />v10 : Y|  
|[Méthode unshift](../../javascript/reference/unshift-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[>>>= (décalage vers la droite non signé), opérateur d'assignation](../../javascript/reference/unsigned-right-shift-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[>>> (décalage vers la droite non signé), opérateur](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Directive use strict](../../javascript/reference/use-strict-directive.md)|N|N|N|Y|Y|Y|Y|  
|[Fonction UTC](../../javascript/reference/date-utc-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode valueOf](../../javascript/reference/valueof-method-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Méthode values (Array)](../../javascript/reference/values-method-array-javascript.md)|N|N|N|N|N|Y|v8.1 : N<br />v10 : Y|  
|[Instruction var](../../javascript/reference/var-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Objet VBArray](../../javascript/reference/vbarray-object-javascript.md)|Y|Y|Y|Y|Y|Y|N|  
|[Opérateur void](../../javascript/reference/void-operator-decrementjavascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Objet WeakMap](../../javascript/reference/weakmap-object-javascript.md)|N|N|N|N|Y|Y|v8 : N<br />v8.1 : Y|  
|[WeakSet, objet](../../javascript/reference/weakset-object-javascript.md)|N|N|N|N|N|Y|v8.1 : N<br />v10 : Y|  
|[Instruction while](../../javascript/reference/while-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Objet WinRTError](../../javascript/reference/winrterror-object-javascript.md)|N|N|N|Y|Y|Y|Y|  
|[Instruction with](../../javascript/reference/with-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction write](../../javascript/reference/debug-write-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Fonction writeln](../../javascript/reference/debug-writeln-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
  
 \*Prend en charge les objets DOM, mais les objets non définis par l’utilisateur. Les attributs `enumerable` et `configurable` peuvent être spécifiés, mais ils ne sont pas utilisés.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition de la compatibilité des documents](http://go.microsoft.com/fwlink/?LinkId=208537)