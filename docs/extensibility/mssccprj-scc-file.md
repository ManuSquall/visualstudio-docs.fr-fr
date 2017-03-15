---
title: "MSSCCPRJ. Fichier de contr&#244;le de code source | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSCCPRJ plug-ins de contrôle de code source. Fichier de contrôle de code source"
  - "MSSCCPRJ. Fichier de contrôle de code source"
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# MSSCCPRJ. Fichier de contr&#244;le de code source
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lorsqu'une solution Visual Studio ou un projet est placé sous contrôle de code source à l'aide de l'IDE, l'IDE reçoit deux informations essentielles à partir du contrôle de code source du plug\-in sous la forme de chaînes. Ces chaînes, « AuxPath » et « NomProjet », sont opaques à l'IDE, mais elles sont utilisées par le plug\-in pour rechercher la solution ou un projet sous contrôle de version. L'IDE obtienne généralement ces chaînes de la première fois en appelant le [SccGetProjPath](../extensibility/sccgetprojpath-function.md), et il les enregistre dans le fichier solution ou un projet pour les appels suivants à la [SccOpenProject](../extensibility/sccopenproject-function.md). Incorporé dans les fichiers solution et projet, les chaînes « AuxPath » et « NomProjet » ne sont pas automatiquement mis à jour lorsqu'un utilisateur, les branchements, branches ou copie les fichiers solution et projet qui sont sous contrôle de version. Pour vous assurer que les fichiers solution et projet pointent vers leur emplacement approprié dans le contrôle de version, les utilisateurs doivent mettre à jour manuellement les chaînes. Étant donné que les chaînes sont destinées à être opaque, toujours peut\-être pas clairement comment ils doivent être mis à jour.  
  
 Le plug\-in de contrôle de code source peut éviter ce problème en stockant les chaînes « AuxPath » et « NomProjet » dans un fichier spécial appelé le MSSCCPRJ. Fichier de contrôle de code source. Il est un fichier local, côté client qui est détenu et maintenu par le plug\-in. Ce fichier n'est jamais placé sous contrôle de code source, mais est généré par le plug\-in pour chaque répertoire qui contient les fichiers de contrôle de code source. Pour déterminer quels fichiers sont les fichiers solution et projet Visual Studio, un plug\-in de contrôle de code source peut comparer les extensions de fichier par rapport à une liste standard ou fourni par l'utilisateur. Une fois que l'IDE détecte qu'un plug\-in prend en charge la MSSCCPRJ. Fichier de contrôle de code source, il cesse d'intégrer la « AuxPath » et chaînes « NomProjet » dans la solution et fichiers projet et lit le MSSCCPRJ ces chaînes. Contrôle de code source du fichier à la place.  
  
 Plug\-in de contrôle source qui prend en charge la MSSCCPRJ. Fichier de contrôle de code source doit respecter les consignes suivantes :  
  
-   Il ne peut exister qu'un seul MSSCCPRJ. Fichier de contrôle de code source par répertoire.  
  
-   Un MSSCCPRJ. Fichier de contrôle de code source peut contenir le « AuxPath » et « NomProjet » pour plusieurs fichiers qui sont sous contrôle de code source dans un répertoire donné.  
  
-   La chaîne « AuxPath » ne doit pas contenir de guillemets doubles à l'intérieur. Il est autorisé à le placer entre guillemets comme délimiteurs \(par exemple, une paire de guillemets doubles peut être utilisée pour indiquer une chaîne vide\). L'IDE supprimera tous les devis à partir de la chaîne « AuxPath » lorsqu'il est lu à partir de la MSSCCPRJ. Fichier de contrôle de code source.  
  
-   La chaîne « NomProjet » dans la MSSCCPRJ. Fichier de contrôle de code source doit correspondre exactement à la chaîne retournée par le `SccGetProjPath` \(fonction\). Si la chaîne retournée par la fonction est entre guillemets, la chaîne dans le MSSCCPRJ. Fichier de contrôle de code source doive être placées entre guillemets autour d'elle et vice versa.  
  
-   Un MSSCCPRJ. Fichier de contrôle de code source est créé ou mis à jour chaque fois qu'un fichier est placé sous contrôle de code source.  
  
-   If une MSSCCPRJ. Fichier de contrôle de code source est supprimé, un fournisseur doit régénérer la prochaine fois qu'il effectue une opération de contrôle de code source concernant ce répertoire.  
  
-   Un MSSCCPRJ. Contrôle de code source doit suivre strictement le format défini.  
  
## Une Illustration de la MSSCCPRJ. Format de fichier de contrôle de code source  
 Voici un exemple de la MSSCCPRJ. Format de fichier de contrôle de code source \(les numéros de ligne sont uniquement des indications et ne doivent pas être incluses dans le corps du fichier\) :  
  
 \[Ligne 1\] `SCC = This is a Source Code Control file`  
  
 \[Ligne 2\]  
  
 \[Ligne 3\] `[TestApp.sln]`  
  
 \[Ligne 4\] `SCC_Aux_Path = "\\server\vss\"`  
  
 \[Ligne 5\] `SCC_Project_Name = "$/TestApp"`  
  
 \[Ligne 6\]  
  
 \[Ligne 7\] `[TestApp.csproj]`  
  
 \[Ligne 8\] `SCC_Aux_Path = "\\server\vss\"`  
  
 \[Ligne 9\] `SCC_Project_Name = "$/TestApp"`  
  
 La première ligne indique la fin du fichier et sert à la signature pour tous les fichiers de ce type. Cette ligne doit apparaître exactement comme dans tous les MSSCCPRJ. Fichiers de contrôle de code source :  
  
 `SCC = This is a Source Code Control file`  
  
 Ce qui suit est une section de paramètres pour chaque fichier, marquées par le nom de fichier entre crochets. Cette section est répétée pour chaque fichier de suivi. Cette ligne est un exemple de nom de fichier, à savoir `[TestApp.csproj]`. L'IDE attend que les deux lignes suivantes. Il ne définit pas, toutefois, le style des valeurs définies. Les variables sont `SCC_Aux_Path` et `SCC_Project_Name`.  
  
 `SCC_Aux_Path = "\\server\vss\"`  
  
 `SCC_Project_Name = "$/TestApp"`  
  
 Il n'existe aucun délimiteur de fin de cette section. Le nom de fichier, ainsi que tous les littéraux apparaissent dans le fichier, sont définis dans le fichier d'en\-tête scc.h. Pour plus d'informations, consultez [Chaînes utilisées comme clés pour rechercher un contrôle de Source de plug\-in](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md).  
  
## Voir aussi  
 [Plug\-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)   
 [Chaînes utilisées comme clés pour rechercher un contrôle de Source de plug\-in](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)