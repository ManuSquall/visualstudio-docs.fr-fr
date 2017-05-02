---
title: "L&#39;URI &#224; encoder contient un caract&#232;re non valide | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5024"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: a3f0fdbb-8d4b-41ae-a396-43dfc9483760
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# L&#39;URI &#224; encoder contient un caract&#232;re non valide
La chaîne que vous avez tentée d'encoder comme un URI \(Uniform Resource Identifier\) contenait des caractères non valides.  Bien que la plupart des caractères soient valides à l'intérieur des chaînes à convertir en URI, certaines séquences de caractères Unicode sont non conformes.  
  
### Pour corriger cette erreur  
  
-   Assurez\-vous que la chaîne à encoder ne contient que des séquences Unicode valides.  Un identificateur URI complet comprend une séquence de composants et de séparateurs.  Les termes figurant entre les symboles « \< » et « \> » représentent les composants. Les caractères « : », « \/ », « ; » et « ? » sont réservés et utilisés comme séparateurs.  Sa forme générale est la suivante :  
  
    ```javascript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## Voir aussi  
 [Fonction encodeURI](../../javascript/reference/encodeuri-function-javascript.md)   
 [encodeURIComponent, fonction](../../javascript/reference/encodeuricomponent-function-javascript.md)