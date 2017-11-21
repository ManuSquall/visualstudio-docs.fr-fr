---
title: "valueOf, méthode (Date) | Documents Microsoft"
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
ms.assetid: 39a1f96e-14b0-4db2-b53d-cdfd67cbb208
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87c5e6ea3c3e28d866f7cabf92dc97b81703b5b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="valueof-method-date"></a>valueOf, méthode (Date)
Retourne la valeur d’heure stockée en millisecondes depuis minuit, le 1er janvier 1970 UTC.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
date.valueOf()  
```  
  
#### <a name="parameters"></a>Paramètres  
 Le `date` objet est une instance d’une Date.  
  
## <a name="return-value"></a>Valeur de retour  
 La valeur stockée de temps en millisecondes écoulées depuis minuit, le 1er janvier 1970 UTC. Ceci est la même valeur que `getTime`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la `valueOf` méthode avec une date.  
  
```JavaScript  
var myDate = new Date();  
myDate.setFullYear(2100, 5, 5);  
if (myDate.getTime() == myDate.valueOf())  
    document.write("values are the same");  
else  
    document.write("values are different");  
  
// Output: values are the same  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]