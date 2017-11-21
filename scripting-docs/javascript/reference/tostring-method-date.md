---
title: "ToString, méthode (Date) | Documents Microsoft"
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
ms.assetid: d3037289-d805-409b-8781-045c59a2c404
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67b6dce74e3796c8b54431b56809473e3c5e59a5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="tostring-method-date"></a>toString, méthode (Date)
Retourne une représentation sous forme de chaîne d’une date. Le format de la chaîne varie selon les paramètres régionaux. Pour les États-Unis Anglais (en-us), il se présente comme suit :  
  
 *jour de la semaine* *mois* *jour* *heure*: *minute*:*deuxième* *fuseau horaire* *année*  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
date.toString()  
```  
  
## <a name="parameters"></a>Paramètres  
 `date`  
 Obligatoire. Date à représenter en tant que chaîne.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne la représentation sous forme de chaîne de la date.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la `toString` méthode avec une date.  
  
```JavaScript  
var myDate = new Date();  
myDate.setFullYear(2100, 5, 5);  
var dateString = myDate.toString();  
document.write(dateString);  
  
// Output: <date>  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]