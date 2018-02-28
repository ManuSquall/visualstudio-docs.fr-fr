---
title: "Name, propriété (Error) (JavaScript) | Documents Microsoft"
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
- name
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Name property
- name property, error name
ms.assetid: 94df2d6b-f1a1-4931-a956-0a930cb87f76
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1a12157b4c467499fab23f7c4cb1be91e9ac5440
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="name-property-error-javascript"></a>name, propriété (Error) (JavaScript)
Retourne le nom d’une erreur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
errorObj.  
name  
  
```  
  
## <a name="parameters"></a>Paramètres  
 `errorObj`  
 Obligatoire. Instance de `Error` objet.  
  
## <a name="remarks"></a>Remarques  
 Le **nom** propriété retourne le type de nom ou une exception d’une erreur. Lorsqu’une erreur d’exécution se produit, la propriété name est définie à un des types d’exception native suivants :  
  
|Type d'exception|Signification|  
|--------------------|-------------|  
|ConversionError|Cette erreur se produit chaque fois qu’une tentative de convertir un objet en quelque chose à laquelle il ne peut pas être converti.|  
|RangeError|Cette erreur se produit lorsqu’une fonction est fournie avec un argument qui a dépassé la plage autorisée. Par exemple, cette erreur se produit si vous tentez de construire un `Array` objet dont la longueur n’est pas un entier positif valide.|  
|ReferenceError|Cette erreur se produit lorsqu’une référence non valide a été détectée. Cette erreur se produit, par exemple, si une référence attendue est `null`.|  
|RegExpError|Cette erreur se produit lorsqu’une erreur de compilation se produit dans une expression régulière. Une fois que l’expression régulière est compilée, toutefois, cette erreur ne peut pas se produire. Cet exemple se produit, par exemple, lorsqu’une expression régulière est déclarée avec un modèle qui a une syntaxe non valide, des indicateurs autre que **i**, **g**, ou **m**, ou si elle contient le même indicateur plusieurs fois.|  
|SyntaxError|Cette erreur se produit lorsque le texte source est analysé et le texte source qui ne respecte pas la syntaxe correcte. Cette erreur se produit, par exemple, si la `eval` est appelée avec un argument qui n’est pas du texte de programme valide.|  
|TypeError|Cette erreur se produit chaque fois que le type réel d’un opérande ne correspond pas au type attendu. Un exemple de lorsque cette erreur se produit est un appel de fonction sur un élément qui n’est pas un objet ou ne prend pas en charge l’appel.|  
|URIError|Cette erreur se produit lorsqu’un non conforme URI Uniform Resource Indicator () est détecté. Par exemple, il s’agit d’erreur se produit quand un caractère non conforme est trouvé dans une chaîne en cours à encoder ou à décoder.|  
  
## <a name="example"></a>Exemple  
 L’exemple suivant provoque la levée d’une exception TypeError et affiche le nom de l’erreur et son message.  
  
```JavaScript  
try  
{  
    var x = y;  
}  
catch(e)  
{  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
```  
  
## <a name="example"></a>Exemple  
 La sortie de ce code est comme suit.  
  
```JavaScript  
Error Message: 'y' is undefined  
Error Code: 5009  
Error Name: TypeError  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **S’applique aux**: [objet Error](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Description, propriété (Error)](../../javascript/reference/description-property-error-javascript.md)   
 [message, propriété (Error)](../../javascript/reference/message-property-error-javascript.md)   
 [Propriété number (Error)](../../javascript/reference/number-property-error-javascript.md)