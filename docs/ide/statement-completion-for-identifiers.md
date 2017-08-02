---
title: "Saisie semi-automatique des instructions pour les identificateurs | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IntelliSense (JavaScript), saisie semi-automatique des instructions"
  - "saisie semi-automatique des instructions, IntelliSense JavaScript"
ms.assetid: c2cd4945-c67e-471b-8057-96cfd25f7fb2
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Saisie semi-automatique des instructions pour les identificateurs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

N'autorise pas JavaScript en tapant des déclarations de variables explicite.  Par conséquent, IntelliSense ne peuvent pas toujours fournir des listes de saisie semi\-automatique pour les objets.  Cela peut se produire dans diverses situations.  Voici quelques plus courants.  
  
-   Un paramètre est déclaré, mais il n'a pas été appelé ailleurs dans le document actif, comme illustré dans l'exemple suivant.  
  
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
  
-   Un objet est une fonction qui est appelée en réponse à un événement.  Au moment du design, le moteur de IntelliSense ne peut pas déterminer le type des objets utilisés dans cette situation.  
  
     Si le moteur de IntelliSense peut déterminer que l'événement doit être appelée, généralement par le biais de l'utilisation de `addEventListener` pour l'événement dans le document actif, des informations plus précises IntelliSense sont fournies.  
  
 Lorsque IntelliSense est incapable d'identifier un objet, le moteur IntelliSense remplit la liste des opérations terminées avec des entités nommées, ou identificateurs, qui sont présents dans le document actif.  Lorsque la liste de saisie contient ces identificateurs, icônes des informations s'affichent à côté d'eux.  En outre, une info\-bulle pour chaque identificateur indique que l'expression est inconnue.  L'illustration suivante montre les instruction options de saisie semi\-automatique pour un objet de type `light` qui ne peut être identifié dans la mesure où l'objet et ses propriétés ne sont pas définies.  Toutefois, la `intensity` propriété n'est disponible dans la liste Identificateur car il a été utilisé dans le `illuminate` fonction.  
  
 **Options de saisie semi\-automatique pour un objet qui ne peut pas être identifié.**  
  
 ![JavaScript IntelliSense pour les identificateurs](~/ide/media/js_intellisense_identifiers.png "js\_intellisense\_identifiers")  
  
 Vous pouvez substituer la liste de saisie semi\-automatique pour un objet à l'aide de commentaires de documentation XML ou des fonctionnalités d'extensibilité JavaScript IntelliSense.  L'utilisation de ces fonctionnalités, vous pouvez fournir des informations de type de plus descriptif IntelliSense lorsqu'il sinon peut\-être pas disponible.  Pour plus d'informations, consultez [Extension de JavaScript IntelliSense](../ide/extending-javascript-intellisense.md) et [Comment : créer des commentaires de documentation XML JavaScript](../ide/create-xml-documentation-comments-for-javascript-intellisense.md).  
  
## Voir aussi  
 [IntelliSense JavaScript](../ide/javascript-intellisense.md)