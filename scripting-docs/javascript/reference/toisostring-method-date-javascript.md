---
title: toisostring, méthode (Date) (JavaScript) | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toISOString method [JavaScript]
ms.assetid: 58577d8f-3ae8-4887-8687-26233ea79ff6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 31559e1bc44849573ec7dc903411ce98b0a4440d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640269"
---
# <a name="toisostring-method-date-javascript"></a>toISOString, méthode (Date) (JavaScript)
Retourne une date sous la forme d’une valeur de chaîne au format ISO.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
  
objDate.toISOString()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Représentation sous forme de chaîne de la date dans l’organisation internationale de format de normalisation (ISO).  
  
## <a name="exceptions"></a>Exceptions  
 Si `objDate` ne contient pas une date valide, un `RangeError` exception est levée.  
  
## <a name="remarks"></a>Remarques  
 Le format ISO est une version simplifiée du format ISO 8601. Pour plus d’informations, consultez [chaînes de Date et heure](../../javascript/date-and-time-strings-javascript.md).  
  
 Le fuseau horaire est toujours UTC, désigné par le suffixe Z dans la sortie.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `toISOString`.  
  
```JavaScript  
var dt = new Date("30 July 2010 15:05 UTC");  
document.write(dt.toISOString());  
document.write("<br />");  
document.write(dt.toUTCString());  
  
// Output:  
//  2010-07-30T15:05:00.000Z  
//  Fri, 30 Jul 2010 15:05:00 UTC  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Date (objet)](../../javascript/reference/date-object-javascript.md)   
 [Chaînes de date et heure](../../javascript/date-and-time-strings-javascript.md)