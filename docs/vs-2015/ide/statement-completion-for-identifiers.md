---
title: Saisie semi-automatique des instructions pour les identificateurs | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [JavaScript], statement completion
- statement completion, JavaScript IntelliSense
ms.assetid: c2cd4945-c67e-471b-8057-96cfd25f7fb2
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 89f507c2f4d01cf5e3e1e983cfcb5bafd9d9a7dd
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54787650"
---
# <a name="statement-completion-for-identifiers"></a>Saisie semi-automatique des instructions pour les identificateurs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript ne permet pas explicite en tapant des déclarations de variables. Par conséquent, IntelliSense ne peut pas toujours fournir des listes de saisie semi-automatique pour les objets. Cela peut se produire dans diverses situations. Voici quelques fréquents.  
  
- Un paramètre est déclaré, mais il n'a pas été appelé ailleurs dans le document actif, comme illustré dans l’exemple suivant.  
  
  ```javascript  
  function illuminate(light) {  
           light.  // Accurate statement completion is not available   
                   // unless illuminate is called elsewhere with a   
                   // parameter that has a value. If it is called only  
                   // in a function that is a sibling to   
                   // illuminate(light) in the call hierarchy, the   
                   // IntelliSense engine also cannot determine the   
                   // parameter type.  
       }  
  
  // Sibling function. No statement completion for light   
  // object in preceding code.  
  function lightLamp() {  
      var x = illuminate(1);  
  }  
  
  // Uncomment the next line to obtain statement completion for  
  // light object in preceding code.  
  // var x = illuminate(1);  
  ```  
  
- Un objet est dans une fonction qui est appelée en réponse à un événement. Au moment du design, le moteur IntelliSense ne peut pas déterminer le type des objets utilisés dans cette situation.  
  
   Si le moteur IntelliSense peut déterminer que l’événement doit être appelé, généralement via l’utilisation de `addEventListener` pour l’événement dans le document actif, vous trouverez des informations IntelliSense plus précises.  
  
  Lorsque IntelliSense ne parvient pas à identifier un objet, le moteur IntelliSense remplit la liste de saisie semi-automatique avec des entités nommées ou des identificateurs, qui sont présents dans le document actif. Lorsque la liste de saisie semi-automatique contient ces identificateurs, les icônes des informations apparaissent en regard de leur. En outre, une info-bulle pour chaque identificateur indique que l’expression est inconnue. L’illustration suivante montre les options de saisie semi-automatique pour un objet de type d’instruction `light` qui ne peut pas être identifié, car l’objet et ses propriétés ne sont pas définies. Toutefois, le `intensity` propriété n’est disponible dans la liste de l’identificateur, car il a été utilisé dans le `illuminate` (fonction).  
  
  **Options de saisie semi-automatique pour un objet qui ne peut pas être identifié.**  
  
  ![JavaScript IntelliSense pour les identificateurs](../ide/media/js-intellisense-identifiers.png "js_intellisense_identifiers")  
  
  Vous pouvez remplacer la liste de saisie semi-automatique pour un objet à l’aide de commentaires de documentation XML ou des fonctionnalités d’extensibilité JavaScript IntelliSense. À l’aide de ces fonctionnalités, vous pouvez fournir des informations de type et des informations IntelliSense plus descriptives lorsqu’il n’est normalement pas disponible. Pour plus d’informations, consultez [extension de JavaScript IntelliSense](../ide/extending-javascript-intellisense.md) et [créer des commentaires de Documentation XML](../ide/create-xml-documentation-comments-for-javascript-intellisense.md).  
  
## <a name="see-also"></a>Voir aussi  
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)
