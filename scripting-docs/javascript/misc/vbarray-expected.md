---
title: VBArray attendu | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5013
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f2998d7d-13a4-4bbe-b872-3ff3316551e4
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b07c5e08e4178c9c31045317627424f5192f5e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633189"
---
# <a name="vbarray-expected"></a>VBArray attendu
Vous avez fourni un objet qui n’était pas un safeArray Visual Basic, une seule était attendue.  
  
```  
new VBArray(safeArray);  
```  
  
 Les objets VBArray sont en lecture seule et ne peuvent pas être créés directement. L’argument safeArray est une valeur VBArray et doit avoir obtenu une valeur VBArray avant d’être passé à la `VBArray` constructeur. Cela n’est possible qu’en récupérant la valeur à partir d’un objet ActiveX ou autre existant.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Assurez-vous de vous transmettez uniquement **VBArray** des objets sur le **VBArray** constructeur.  
  
## <a name="see-also"></a>Voir aussi  
 [VBArray, objet](../../javascript/reference/vbarray-object-javascript.md)   
 [Utilisation des tableaux](../../javascript/advanced/using-arrays-javascript.md)