---
title: Normalize, méthode (String) (JavaScript) | Documents Microsoft
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
ms.assetid: d50077c1-b5fa-4e7a-9c9d-dc66cfc423ac
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aece38339ea1ce8924f404938b2d35d07504d539
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638739"
---
# <a name="normalize-method-string-javascript"></a>normalize, méthode (String) (JavaScript)
Retourne le formulaire de normalisation Unicode d'une chaîne spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
stringObj.normalize([form]);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `stringObj`  
 Obligatoire. Objet de chaîne pour le test.  
  
 `form`  
 Facultatif. Valeur du formulaire de normalisation Unicode.  
  
## <a name="return-value"></a>Valeur de retour  
 Formulaire de normalisation Unicode d'une chaîne spécifiée.  
  
## <a name="exceptions"></a>Exceptions  
 Si `form` est une valeur non prise en charge, une `RangeError` est levée.  
  
## <a name="remarks"></a>Remarques  
 Si `stringObj` n'est pas une chaîne, il sera converti en chaîne avant que la méthode ne tente de retourner le formulaire de normalisation Unicode de la chaîne.  
  
 `form`doit être une valeur d’un formulaire de normalisation Unicode, « NFC », « NFD », « NFKC » ou « NFKD », correspondant aux valeurs spécifiées pour [Unicode annexe 15 de la norme](http://www.unicode.org/reports/tr15/). La valeur par défaut de `form` est « NFC ».  
  
## <a name="example"></a>Exemple  
 Les exemples de code suivants illustrent l'utilisation de la méthode `normalize`.  
  
```JavaScript  
// ANGSTORM SIGN and LATIN CAPITAL A WITH RING ABOVE is canonically equivalent  
"\u212b".normalize("NFC") === "\u00c5";  
  
// Decomposed, ANGSTOM SIGN is LATIN CAPITAL A followed by COMBINING RING ABOVE  
"\u212b".normalize("NFD") === "\u0041\u030a"  
  
// Normalization Form C will combine the result back into the precombined character  
"\u0041\u030a".normalize("NFC") === "\u00c5"  
  
// LATIN SMALL LIGATURE FI is compatibility equivalent with LATIN SMALL LETTER F followed by  
// LATIN SMALL LETTER I.  
"\ufb01".normalize("NFKD") === "fi";  
  
// Same mapping in NFKC  
"\ufb01".normalize("NFKC") === "fi";  
  
// NFKC will not recombine compatibility characters.  
"fi".normalize("NFKC") === "fi";  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]