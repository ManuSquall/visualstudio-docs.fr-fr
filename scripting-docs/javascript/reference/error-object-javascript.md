---
title: "Erreur de l’objet (JavaScript) | Documents Microsoft"
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
- Error
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Error object
ms.assetid: 0b27d6ec-3997-4e91-a6c0-5afbaf494db7
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: efc03f13a501a1a13a2e7f3eea000b406559f30b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="error-object-javascript"></a>Error, objet (JavaScript)
Contient des informations sur des erreurs.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      errorObj = new Error()  
errorObj = new Error([number])  
errorObj = new Error([number[, description]])  
```  
  
## <a name="parameters"></a>Paramètres  
 `errorObj`  
 Obligatoire. Nom de la variable à laquelle l'objet `Error` est assigné. L'affectation de variable est omise lorsque vous créez l'erreur à l'aide d'une instruction `throw`.  
  
 `number`  
 Facultatif. Valeur numérique assignée à une erreur. Zéro si omise.  
  
 `description`  
 Facultatif. Brève chaîne qui décrit une erreur. Chaîne vide si omise.  
  
## <a name="remarks"></a>Remarques  
 Chaque fois qu'une erreur d'exécution se produit, une instance de l'objet `Error` est créée pour décrire l'erreur. Cette instance a deux propriétés intrinsèques qui contiennent la description de l'erreur (propriété `description`) et le numéro de l'erreur (propriété `number`). Pour plus d’informations, consultez [erreurs d’exécution JavaScript](../../javascript/reference/javascript-run-time-errors.md).  
  
 Un numéro d'erreur est une valeur 32 bits. Le mot de 16 bits de poids fort est le code de service tandis que le mot de poids faible est le code d'erreur effectif.  
  
 Les objets `Error` peuvent également être créés explicitement, à l'aide de la syntaxe indiquée ci-dessus, ou levés à l'aide de l'instruction `throw`. Dans les deux cas, vous pouvez ajouter les propriétés de votre choix pour développer les fonctionnalités de l'objet `Error`.  
  
 En règle générale, la variable locale qui est créée dans un **try... catch** instruction fait référence à créé implicitement `Error` objet. Par conséquent, vous pouvez utiliser le numéro et la description de l'erreur à votre convenance.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous illustre l'utilisation de l'objet `Error`.  
  
```  
function checkInput(x) {  
    try  
    {  
        if (isNaN(parseInt(x))) {  
            throw new Error("Input is not a number.");  
        }  
    }  
    catch(e)  
    {  
        document.write(e.description);  
    }  
}  
  
checkInput("not a number");  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de l'objet `Error` créé implicitement.  
  
```JavaScript  
try  
   {  
   // Cause an error.  
   x = y;  
   }  
catch(e)  
   {  
      document.write(e);  
      document.write ("<br />");  
  
      document.write ("Number: ");  
      document.write (e.number & 0xFFFF);  
      document.write ("<br />");  
  
      document.write ("Facility Code: ");  
      document.write(e.number>>16 & 0x1FFF);  
      document.write ("<br />");  
  
      document.write ("Description: ");  
      document.write (e.description);  
   }  
  
// Output:  
// ReferenceError: 'y' is undefined  
// Number: 5009  
// Facility Code: 10  
// Description: 'y' is undefined  
  
```  
  
## <a name="methods"></a>Méthodes  
 [ToString, méthode (Error)](../../javascript/reference/tostring-method-error.md) &#124; [valueOf, méthode (Date)](../../javascript/reference/valueof-method-date.md)  
  
## <a name="properties"></a>Propriétés  
 [constructor, propriété (Error)](../../javascript/reference/constructor-property-error.md) &#124; [propriété description](../../javascript/reference/description-property-error-javascript.md) &#124; [propriété message](../../javascript/reference/message-property-error-javascript.md) &#124; [name, propriété](../../javascript/reference/name-property-error-javascript.md) &#124; [number, propriété](../../javascript/reference/number-property-error-javascript.md) &#124; [prototype, propriété (Error)](../../javascript/reference/prototype-property-error.md) &#124; [stack, propriété (Error)](../../javascript/reference/stack-property-error-javascript.md) &#124; [stacktracelimit, propriété (Error)](../../javascript/reference/stacktracelimit-property-error-javascript.md)  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [new, opérateur](../../javascript/reference/new-operator-decrementjavascript.md)   
 [throw (instruction)](../../javascript/reference/throw-statement-javascript.md)   
 [try... catch... finally, instruction](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Instruction var](../../javascript/reference/var-statement-javascript.md)   
 [Hilo JavaScript exemple d’application (Windows Store)](http://hilojs.codeplex.com/SourceControl/latest)