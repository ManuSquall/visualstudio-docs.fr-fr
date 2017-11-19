---
title: "constructor, propriété (Date) | Documents Microsoft"
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
ms.assetid: 5db153a1-788b-4a61-bfc8-2d2ec38f36ea
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 798064117e17ee5b2988396de3c6545917373b10
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="constructor-property-date"></a>constructor, propriété (Date)
Spécifie la fonction qui crée une date.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
date.constructor  
```  
  
## <a name="remarks"></a>Remarques  
 Requis `date` est le nom d’un objet date.  
  
 La propriété `constructor` est un membre du prototype de chaque objet qui en possède un. La propriété `constructor` contient une référence à la fonction qui crée les instances d'un objet donné.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la propriété de constructeur.  
  
```JavaScript  
var x = new Date("Hi");  
  
if (x.constructor == Date)  
    document.write("Object is a date.");  
  
// Output:  
// Object is a date.  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]