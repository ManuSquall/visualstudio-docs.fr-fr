---
title: "Limitations du d&#233;bogage de script | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ASPX (mappage de points d'arrêt), limitations"
  - "mappage de points d'arrêt, limitations"
  - "débogage de script, limitations"
ms.assetid: 280eead5-693c-47af-967f-dfe9d23f84db
caps.latest.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 22
---
# Limitations du d&#233;bogage de script
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] prend en charge le débogage de script côté client, sous réserve des limitations de cette rubrique.  
  
## Limitations relatives au mappage de points d'arrêt avec script côté client  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vous permet de définir un point d'arrêt dans un fichier ASPX ou HTML côté serveur transformé en fichier côté client au moment de l'exécution.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mappe le point d'arrêt à partir du fichier côté serveur à un point d'arrêt correspondant dans le fichier côté client, selon les limitations suivantes :  
  
-   Les points d'arrêt doivent être définis à l'intérieur de blocs `<script>`.  Les points d'arrêt dans le script inline ou les blocs `<% %>` ne peuvent pas être mappés.  
  
-   L'URL de navigateur pour la page doit contenir le nom de la page.  Par exemple, http:\/\/microsoft.com\/default.apsx.  Le mappage de points d'arrêt ne peut pas reconnaître une redirection d'une adresse telle que http:\/\/microsoft.com vers la page par défaut.  
  
-   Le point d'arrêt doit être défini dans la page spécifiée dans l'URL de navigateur, pas dans un fichier de contrôle ASPX \(ascx\), une page maître ou un autre fichier inclus dans cette page.  Les points d'arrêt définis dans les pages incluses ne peuvent pas être mappés.  
  
-   Les points d'arrêt définis dans des blocs `<script defer=true>` ne peuvent pas être mappés.  
  
-   Pour les points d'arrêt définis dans des blocs `<script id="">`, le mappage de points d'arrêt ignore l'attribut `id`.  
  
## Mappage de points d'arrêt et doublons  
 Pour trouver l'emplacement correspondant dans le script côté serveur et côté client, l'algorithme de mappage de points d'arrêt examine le code sur chaque ligne.  L'algorithme suppose que chaque ligne est unique.  Si deux ou plusieurs lignes contiennent le même code et si vous définissez un point d'arrêt sur l'un de ces doublons, il se peut que l'algorithme de mappage de points d'arrêt sélectionne le doublon incorrect dans le fichier côté client.  Pour empêcher cela, ajoutez un commentaire à la ligne où vous avez défini le point d'arrêt.  Par exemple :  
  
```  
i++ ;  
i ++; // I added a comment, so this line is now unique  
i ++;  
```