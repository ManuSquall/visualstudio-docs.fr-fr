---
title: "Cannot copy multifile assembly &#39;assembly&#39; to directory &#39;directory&#39;. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannotcopyscatterassembly"
ms.assetid: 939519c7-741d-4e05-8b63-71e39fb426ad
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Cannot copy multifile assembly &#39;assembly&#39; to directory &#39;directory&#39;. &lt;reason&gt;
Les assemblys multifichiers sont copiés dans un sous\-répertoire du répertoire du projet à partir duquel ils seront exécutés.  Par exemple, si le chemin de sortie est c:\\projet1\\bin et qu'il existe un assembly \(dont la propriété `CopyLocal` a la valeur `true`\) nommé Test contenant des fichiers a.dll et b.dll, vous obtenez la structure de fichiers ci\-dessous une fois que la copie est terminée :  
  
```  
c:\project1\bin\Test  
   c:\project1\bin\Test\Test.dll   (main assembly)  
   c:\project1\bin\Test\a.dll       (file a.dll)  
   c:\project1\bin\Test\b.dll       (file b.dll)  
```  
  
 Cette erreur serait affichée par le système de projet si le répertoire c:\\projet1\\bin\\Test n'avait pas pu être créé sur le disque.  
  
 Cette erreur indique que l'espace disque est insuffisant ou que vous atteignez la limite MAX\_PATH pour la longueur du chemin d'accès.  
  
 **Pour corriger cette erreur**  
  
-   Vérifiez l'espace disque.  
  
-   Déplacez le projet vers un dossier dont la longueur du chemin d'accès est inférieure à celle du dossier contenant actuellement le projet.  
  
-   Changez le répertoire de sortie au profit d'un dossier dont la longueur du chemin d'accès absolu est plus petite \(cela s'applique aux projets clients uniquement\).  
  
## Voir aussi  
 [Dépannage de références rompues](../ide/troubleshooting-broken-references.md)   
 [Comment : ajouter ou supprimer des références à l'aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/fr-fr/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Assemblies in the Common Language Runtime](http://msdn.microsoft.com/fr-fr/33a0bc6a-6bb3-44c7-ada7-4a046e8c0945)