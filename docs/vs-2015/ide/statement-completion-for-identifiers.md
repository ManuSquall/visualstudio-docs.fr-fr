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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f5e52bf174e5a41d79fa23bfca39121db668e40e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72643861"
---
# <a name="statement-completion-for-identifiers"></a>Saisie semi-automatique des instructions pour les identificateurs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript n’autorise pas les types explicites pour les déclarations de variables. Par conséquent, IntelliSense ne peut pas toujours fournir de listes de saisie semi-automatique pour les objets. Cela peut se produire dans diverses situations. Voici quelques-uns des plus courants.

- Un paramètre est déclaré, mais il n’a pas été appelé ailleurs dans le document actif, comme indiqué dans l’exemple suivant.

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

   Si le moteur IntelliSense peut déterminer que l’événement doit être appelé, en général par le biais de l’utilisation de `addEventListener` pour l’événement dans le document actif, des informations IntelliSense plus précises sont fournies.

  Quand IntelliSense ne peut pas identifier un objet, le moteur IntelliSense remplit la liste de saisie semi-automatique avec les entités nommées, ou les identificateurs, qui sont présents dans le document actif. Lorsque la liste de saisie semi-automatique contient ces identificateurs, des icônes d’informations s’affichent en regard. En outre, une info-bulle pour chaque identificateur indique que l’expression est inconnue. L’illustration suivante montre les options de saisie semi-automatique des instructions pour un objet de type `light` qui ne peut pas être identifié, car l’objet et ses propriétés ne sont pas définis. Toutefois, la `intensity` propriété est disponible dans la liste d’identificateurs, car elle a été utilisée dans la `illuminate` fonction.

  **Options d’achèvement pour un objet qui ne peut pas être identifié**

  ![JavaScript IntelliSense pour les identificateurs](../ide/media/js-intellisense-identifiers.png "js_intellisense_identifiers")

  Vous pouvez remplacer la liste de saisie semi-automatique d’un objet à l’aide de commentaires de documentation XML ou de fonctionnalités d’extensibilité IntelliSense JavaScript. À l’aide de ces fonctionnalités, vous pouvez fournir des informations de type et des informations IntelliSense plus descriptives lorsqu’elles ne sont pas disponibles autrement. Pour plus d’informations, consultez [extension de JavaScript IntelliSense](../ide/extending-javascript-intellisense.md) et [créer des commentaires de documentation XML](../ide/create-xml-documentation-comments-for-javascript-intellisense.md).

## <a name="see-also"></a>Voir aussi
 [IntelliSense JavaScript](../ide/javascript-intellisense.md)
