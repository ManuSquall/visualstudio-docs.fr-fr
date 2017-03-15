---
title: "Comment&#160;: sp&#233;cifier les emplacements du fichier de symboles &#224; partir de la ligne de commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8aa067bb-e8bf-4081-aff0-cfbcf65934a0
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Comment&#160;: sp&#233;cifier les emplacements du fichier de symboles &#224; partir de la ligne de commande
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Pour afficher les informations de symbole telles que les noms de fonction et les numéros de ligne, l'outil en ligne de commande VSPerfReport doit pouvoir accéder aux fichiers de symboles \(.PDB\) des composants profilés, ainsi qu'aux fichiers système Windows.  Les fichiers de symboles sont créés lors de la compilation d'un composant.  Pour plus d'informations, consultez [VSPerfReport](../profiling/vsperfreport.md).  VSPerfReport recherche automatiquement les fichiers de symboles aux emplacements suivants :  
  
-   Chemins spécifiés dans l'option **\/SymbolPath** ou dans la variable d'environnement **\_NT\_SYMBOL\_PATH**.  
  
-   Chemin d'accès local exact dans lequel un composant a été compilé.  
  
-   Répertoire contenant le fichier des données de profilage \(.vsp ou vsps\).  
  
 Microsoft fournit les fichiers .pdb de bon nombre de ses produits en ligne sur un serveur de symboles.  Si l'ordinateur que vous utilisez pour le reporting est connecté à Internet, VSPerfReport se connecte au serveur de symboles en ligne afin de rechercher automatiquement les informations relatives aux symboles et d'enregistrer les fichiers dans un magasin local.  
  
 Vous pouvez spécifier l'emplacement des fichiers de symboles et du magasin du serveur de symboles Microsoft comme suit :  
  
-   Définissez la variable d'environnement **\_NT\_SYMBOL\_PATH**.  
  
-   Ajoutez l'option **\/SymbolPath** à la ligne de commande de VSPerfReport.  
  
 Vous pouvez également utiliser ces deux méthodes.  
  
> [!NOTE]
>  Si [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] est installé sur l'ordinateur local, un emplacement pour les fichiers de symboles Windows a probablement déjà été défini.  Pour plus d'informations, consultez [Comment : référencer les informations de symboles Windows](../profiling/how-to-reference-windows-symbol-information.md).  Vous devez toujours configurer VSPerfReport pour utiliser l'emplacement et le serveur comme décrit ultérieurement dans cette rubrique.  
  
## Spécification des fichiers de symboles Windows  
  
#### Pour configurer l'utilisation du serveur de symboles Windows  
  
1.  Si nécessaire, créez un répertoire dans lequel stocker les fichiers de symboles en local.  
  
2.  Utilisez la syntaxe suivante pour définir la variable d'environnement **\_NT\_SYMBOL\_PATH** ou l'option VSPerfReport \/SymbolPath :  
  
     **srv\*** *LocalStore* **\*http:\/\/msdl.microsoft.com\/downloads\/symbols**  
  
     où *LocalStore* est le chemin d'accès du répertoire local que vous avez créé.  
  
## Spécification des fichiers de symboles de composants  
 Les outils de profilage recherchent les fichiers .pdb des composants que vous voulez profiler à leurs emplacements d'origine qui sont stockés dans les composants ou dans le dossier qui contient le fichier des données de profilage.  Vous pouvez spécifier d'autres emplacements à examiner en ajoutant un ou plusieurs chemins d'accès à **\_NT\_SYMBOL\_PATH** ou à l'option **\/SymbolPath**.  Séparez les chemins d'accès par des points\-virgules.  
  
## Exemple  
 La ligne de commande suivante définit la variable d'environnement **\_NT\_SYMBOL\_PATH** sur le serveur de symboles Windows et le répertoire local sur **C:\\Symbols**.  
  
 **set  \_NT\_SYMBOL\_PATH\=srv\*C:\\symbols\*http:\/\/msdl.microsoft.com\/downloads\/symbols**  
  
 La ligne de commande VSPerfReport suivante ajoute le répertoire C:\\Projects\\Symbols au chemin d'accès de recherche à l'aide de l'option **\/SymbolPath**.  
  
 **VSPerfReport**  *MyApp* **.exe \/SymbolPath:C:\\Projects\\Symbols \/summary:all**