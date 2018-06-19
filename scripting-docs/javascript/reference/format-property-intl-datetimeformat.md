---
title: format, propriété (Intl.DateTimeFormat) | Documents Microsoft
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
ms.assetid: 487930fe-a948-446f-902d-06bb0d7685d5
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2e94fcd797a63944d0162dceadf773cf9b15f943
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636589"
---
# <a name="format-property-intldatetimeformat"></a>format, propriété (Intl.DateTimeFormat)
Retourne une fonction qui met en forme une date spécifique aux paramètres régionaux en utilisant les paramètres de module de formatage de date/heure spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
dateTimeFormatObj.format  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dateTimeFormatObj`  
 Obligatoire. Le nom de la `DateTimeFormat` objet à utiliser comme un formateur.  
  
## <a name="remarks"></a>Remarques  
 La fonction retournée par le `format` propriété accepte un argument unique, `date`et retourne une chaîne qui représente la date localisé à l’aide des options spécifiées dans le `DateTimeFormat` objet. Le `date` paramètre de la fonction retournée doit être un nombre, une chaîne de date, ou un `Date` objet. Si `date` n’est pas fourni, la fonction utilise [Date.now](../../javascript/reference/date-now-function-javascript.md) en tant que la valeur d’entrée par défaut.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise un `DateTimeFormat` objet à localiser la date « 1 déc 2007 » en allemand et remettre en forme.  
  
```JavaScript  
var dtFormat = new Intl.DateTimeFormat(["de"], {  
    year: "numeric",  
    month: "long",  
    day: "2-digit",  
    hour: "numeric"  
});  
  
if (console && console.log) {  
    console.log(dtFormat.format(new Date("Dec 1, 2007")));  
    // Returns 01. Dezember 2007 00:00  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Objet Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md)