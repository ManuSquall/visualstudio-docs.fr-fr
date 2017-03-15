---
title: "Comment&#160;: limiter l’instrumentation &#224; des fonctions sp&#233;cifiques | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "outils d’analyse des performances, limiter l’instrumentation à des fonctions"
ms.assetid: bd98d6bf-2560-4eba-b063-2facb09f87c4
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Comment&#160;: limiter l’instrumentation &#224; des fonctions sp&#233;cifiques
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez limiter l'instrumentation et la collecte de données à une ou plusieurs fonctions en définissant des options sur la page **Avancé** des pages de propriétés de la **session de performance** ou des fichiers binaires cibles :  
  
-   Si vous spécifiez les fonctions sur la page des propriétés de la session de performance, seules ces fonctions sont instrumentées dans tous les fichiers binaires instrumentés de la session.  
  
-   Si vous spécifiez les fonctions sur la page des propriétés d'un fichier binaire cible, seules les fonctions qui figurent dans ce fichier binaire sont instrumentées.  Les fonctions contenues dans les autres fichiers binaires de la performance sont instrumentées comme d'habitude.  
  
 Cette méthode de limitation de la collecte de données est uniquement prise en charge lorsque vous sélectionnez la méthode de profilage par instrumentation.  
  
> [!NOTE]
>  Vous pouvez également utiliser la page **Avancé** des pages de propriétés de la **session de performance** afin de définir d'autres options disponibles dans l'outil d'instrumentation par ligne de commande des outils de profilage [VSInstr](../profiling/vsinstr.md).  
  
### Pour limiter l'instrumentation à des fonctions spécifiques dans une session de performance  
  
1.  Dans l'**Explorateur de performances**, cliquez avec le bouton droit sur le nom de la session de votre choix, puis cliquez sur **Propriétés**.  
  
     La boîte de dialogue **Pages de propriétés** s'affiche.  
  
2.  Dans la boîte de dialogue **Pages de propriétés**, cliquez sur **Avancé**.  
  
3.  Dans la zone de texte **Options d'instrumentation supplémentaires**, tapez le nom des fonctions à instrumenter en respectant la syntaxe suivante :  
  
     **\/include:** `FuncSpec` **\[;** `FuncSpec` **\]** `...`  
  
     `FuncSpec` correspond à l'espace de noms et au nom de la fonction.  Il présente le format `Namespace`**::**`FunctionName`.  Utilisez un point\-virgule pour séparer plusieurs fonctions.  Utilisez un astérisque \(\*\) pour spécifier un caractère générique qui remplace un ou plusieurs caractères.  Par exemple, **\/include:MyNS::\***  spécifie toutes les fonctions dans l'espace de noms MyNS.  
  
    > [!NOTE]
    >  Pour obtenir la liste des fonctions dans un fichier binaire, ouvrez une fenêtre d'invite de commandes dans le répertoire d'installation des outils de profilage \(en général, il s'agit du répertoire \\Team Tools\\Performance Tools situé dans le répertoire d'installation de [!INCLUDE[vsprvsts](../code-quality/includes/vsprvsts_md.md)]\), puis tapez vsinstr \/DumpFuncs.  
  
### Pour limiter l'instrumentation à des fonctions spécifiques dans un fichier binaire  
  
1.  Dans l'**Explorateur de performances**, localisez le nom du fichier binaire dans le nœud **Cibles** de la session de performance.  
  
2.  Cliquez avec le bouton droit sur le nom du fichier binaire, puis cliquez sur **Propriétés**.  
  
     La boîte de dialogue **Pages de propriétés** s'affiche.  
  
3.  Dans la boîte de dialogue **Pages de propriétés**, cliquez sur **Avancé**.  
  
4.  Dans la zone de texte **Options d'instrumentation supplémentaires**, tapez le nom des fonctions à instrumenter en respectant la syntaxe suivante :  
  
     **\/include:** `FuncSpec` **\[;** `FuncSpec` **\]** `...`  
  
     `FuncSpec` correspond à l'espace de noms et au nom de la fonction.  Il présente le format `Namespace`**::**`FunctionName`.  Utilisez un point\-virgule pour séparer plusieurs fonctions.  Utilisez un astérisque \(\*\) pour spécifier un caractère générique qui remplace un ou plusieurs caractères.  Par exemple, **\/include:MyNS::\***  spécifie toutes les fonctions dans l'espace de noms MyNS.  
  
    > [!NOTE]
    >  Pour obtenir la liste des fonctions dans un fichier binaire, ouvrez une fenêtre d'invite de commandes dans le répertoire d'installation des outils de profilage \(en général, il s'agit du répertoire \\Team Tools\\Performance Tools situé dans le répertoire d'installation de [!INCLUDE[vsprvsts](../code-quality/includes/vsprvsts_md.md)]\), puis tapez vsinstr \/DumpFuncs.  
  
## Voir aussi  
 [Contrôle de la collecte de données](../profiling/controlling-data-collection.md)   
 [Procédure : limiter l’instrumentation à des DLL spécifiques](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)   
 [Comment : spécifier des options d’instrumentation supplémentaires](../Topic/How%20to:%20Specify%20Additional%20Instrumentation%20Options.md)