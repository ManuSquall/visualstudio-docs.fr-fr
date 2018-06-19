---
title: valueOf, méthode (Error) | Documents Microsoft
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
ms.assetid: ca25c57d-c9ad-445b-8235-561390de680c
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c7593937530469142265f8081bf3472fa4935aee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640199"
---
# <a name="valueof-method-error"></a>valueOf, méthode (Error)
Retourne la valeur de chaîne d’une erreur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
error.valueOf()  
```  
  
#### <a name="parameters"></a>Paramètres  
 Le `error` objet est une instance d’une erreur.  
  
## <a name="return-value"></a>Valeur de retour  
 La chaîne « Erreur : « ainsi que le message d’erreur.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la `valueOF` méthode avec une date.  
  
```JavaScript  
var myError = new Error();  
myError.message = "This is an error.";  
var value = myError.valueOf();  
document.write(value);  
  
// Output: Error: This is an error.  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]