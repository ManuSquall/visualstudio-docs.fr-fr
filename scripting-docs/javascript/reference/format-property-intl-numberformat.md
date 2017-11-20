---
title: "format, propriété (Intl.NumberFormat) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 68c3223a-023c-4fa0-aa99-d049a7a0e26a
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: be40f8e94220ad7504dd3b9736e71b3416bb3d2a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="format-property-intlnumberformat"></a>format, propriété (Intl.NumberFormat)
Retourne une fonction qui met en forme un nombre de paramètres régionaux spécifiques en utilisant les paramètres de module de formatage de nombre spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
numberFormatObj.format  
```  
  
#### <a name="parameters"></a>Paramètres  
 `numberFormatObj`  
 Obligatoire. Le nom de la `NumberFormat` objet à utiliser comme un formateur.  
  
## <a name="remarks"></a>Remarques  
 La fonction retournée par le `format` propriété accepte un argument unique, `value`et retourne une chaîne qui représente le nombre de localisé à l’aide des options spécifiées dans le `NumberFormat` objet. Si `value` n’est pas fourni, la fonction retourne `NaN` (pas un nombre).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise un `NumberFormat` objet pour créer un numéro localisé.  
  
```JavaScript  
var nf = new Intl.NumberFormat(["en-US"], {  
    style: "currency",  
    currency: "CNY",  
    currencyDisplay: "symbol",  
    maximumFractionDigit: 1  
})  
  
if (console && console.log) {  
    console.log(nf.format(100)); // "¥100.00"  
}  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Objet Intl.NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md)