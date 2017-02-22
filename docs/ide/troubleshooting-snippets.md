---
title: "D&#233;pannage des extraits | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "extraits de code IntelliSense, dépanner"
  - "dépanner les extraits de code IntelliSense"
  - "dépanner Visual Basic, extraits de code IntelliSense"
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# D&#233;pannage des extraits
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les problèmes liés aux extraits de code IntelliSense sont généralement provoqués par deux problèmes : lorsque le fichier d'extrait est corrompu ou lorsque le contenu de ce fichier est mauvais.  
  
## Problèmes courants  
  
### L'extrait de code ne peut pas être déplacé de l'Explorateur de fichiers dans un fichier source Visual Studio  
  
-   Le XML dans le fichier d'extrait est peut\-être corrompu.  L'**Éditeur XML** dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] permet de localiser des problèmes dans la structure XML.  
  
-   Le fichier d'extrait n'est peut\-être pas conforme au schéma de l'extrait de code.  L'**Éditeur XML** dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] permet de localiser des problèmes dans la structure XML.  
  
### Certaines erreurs de compilation ne sont pas mises en surbrillance dans le code  
  
-   Une référence de projet est peut\-être manquante.  Examinez la documentation relative à l'extrait de code.  Si la référence n'est pas trouvée sur l'ordinateur, vous devez l'installer.  Lorsque vous insérez un extrait de code, toutes les références nécessaires doivent également être ajoutées au projet.  Si les informations de référence manquent dans l'extrait de code, vous pouvez signaler cette erreur au créateur de l'extrait.  
  
-   Une variable n'est peut\-être pas définie.  Les variables non définies dans un extrait de code doivent être mises en surbrillance.  Si tel n'est pas le cas, vous pouvez signaler cette erreur au créateur de l'extrait.  
  
## Voir aussi  
 [Extraits de code](../ide/code-snippets.md)