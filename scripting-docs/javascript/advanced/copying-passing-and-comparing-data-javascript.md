---
title: Copie, transmission et comparaison de données (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arrays [Visual Studio], passing values
- function parameters
- string comparison
- function parameters, about function parameters
- ByRef argument
- arrays [Visual Studio], setting data types
- arrays [Visual Studio], copying data
- ByVal argument
- string comparison, testing data
ms.assetid: fbccd877-7249-45d4-bd9f-6bcd8ba94a6b
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c3cf980ca1dfd0c0e09871b6de9756cb2a10364b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569329"
---
# <a name="copying-passing-and-comparing-data-javascript"></a>Copie, transmission et comparaison de données (JavaScript)
La façon dont les données sont traitées dans le langage [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] dépend de leur type.  
  
## <a name="by-value-vs-by-reference"></a>Par valeur ou Par référence  
 Les nombres et les valeurs booléennes (**true** et **false**) sont copiés, passés et comparés *par valeur*. Lorsque vous copiez ou passez par valeur, vous allouez un espace dans la mémoire de l'ordinateur et y copiez la valeur d'origine. Toute modification apportée à la valeur d'origine n'affecte pas la copie (et inversement), car il s'agit d'entités distinctes.  
  
 Les objets, les tableaux et les fonctions sont copiés, passés et comparés *par référence*. Lorsque vous copiez ou passez par référence, vous créez un pointeur vers l'élément original et utilisez ce pointeur comme s'il s'agissait d'une copie. Toute modification apportée à l'original est répercutée sur ce dernier et sur la copie (et inversement). Il n'existe en fait qu'une seule entité ; la « copie » n'est autre qu'une référence aux données, et non une réelle copie.  
  
 Lors d'une comparaison par référence, les deux variables doivent faire référence à exactement la même entité pour que la comparaison réussisse. Par exemple, deux objets **Tableau** distincts ne seront jamais considérés comme égaux, même s’ils contiennent les mêmes éléments. En effet, l'une des variables doit être une référence à l'autre pour que la comparaison aboutisse. Pour vérifier si deux tableaux contiennent les mêmes éléments, comparez les résultats de la méthode **toString()**.  
  
 Enfin, les chaînes sont copiées et passées par référence, mais sont comparées par valeur. Notez que si vous avez deux objets **String** (créés avec une chaîne String("something")) **new**, ils seront comparés par référence. Toutefois, si l’une des deux valeurs ou les deux valeurs correspondent à une valeur de chaîne, ils seront comparés par valeur.  
  
> [!NOTE]
>  Les jeux de caractères ASCII et ANSI sont conçus de telle sorte que les lettres majuscules précèdent les minuscules dans l'ordre de tri. Par exemple, « Zoo » est placé *avant* « aardvark ». Vous pouvez appeler **toUpperCase()** ou **toLowerCase()** sur les deux chaînes si vous voulez effectuer une comparaison qui ne tient pas compte de la casse.  
  
## <a name="passing-parameters-to-functions"></a>Passage de paramètres aux fonctions  
 Lorsque vous passez un paramètre à une fonction par valeur, vous effectuez une copie distincte de ce paramètre, copie qui n'existe qu'à l'intérieur de la fonction. Même si des objets et des tableaux sont passés par référence, si vous les remplacez directement par une nouvelle valeur dans la fonction, cette nouvelle valeur n'est pas réfléchie en dehors de la fonction. Seules les modifications apportées aux propriétés des objets ou aux éléments des tableaux sont visibles en dehors de la fonction.  
  
 Voici un exemple utilisant le modèle objet Internet Explorer :  
  
```JavaScript  
// This clobbers (over-writes) its parameter, so the change  
// is not reflected in the calling code.  
function Clobber(param)   
{  
    // clobber the parameter; this will not be seen in   
    // the calling code  
    param = new Object();  
    param.message = "This will not work";  
}  
  
// This modifies a property of the parameter, which  
// can be seen in the calling code.  
function Update(param)  
{  
    // Modify the property of the object; this will be seen  
    // in the calling code.  
    param.message = "I was changed";  
}  
  
// Create an object, and give it a property.  
var obj = new Object();  
obj.message = "This is the original";  
  
// Call Clobber, and print obj.message. Note that it hasn't changed.  
Clobber(obj);  
window.alert(obj.message); // Still displays "This is the original".  
  
// Call Update, and print obj.message. Note that is has changed.  
Update(obj);  
window.alert(obj.message); // Displays "I was changed".  
```  
  
## <a name="testing-data"></a>Test de données  
 Lorsque vous effectuez un test par valeur, vous comparez deux éléments distincts pour savoir s'ils sont égaux. En principe, cette comparaison est effectuée octet par octet. Lorsque vous effectuez un test par référence, vous vérifiez si deux éléments sont des pointeurs vers un même élément original. Si c'est le cas, ils sont considérés comme égaux dans le cadre de la comparaison. Sinon, même s'ils contiennent exactement les mêmes valeurs, octet par octet, ils ne sont pas considérés comme égaux.  
  
 La copie et le passage de chaînes par référence économise de la mémoire ; mais parce qu'il n'est pas possible de modifier des chaînes une fois qu'elles ont été créées, il devient possible de les comparer par valeur. Cela vous permet de tester si deux chaînes ont le même contenu, même si l'une d'entre elles a été générée complètement séparément de l'autre.  
  
## <a name="see-also"></a>Voir aussi  
 [Calcul des dates et des heures (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md)