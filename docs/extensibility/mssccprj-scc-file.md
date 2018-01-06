---
title: "MSSCCPRJ. Fichier de contrôle de code source | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 90a21ba6aafa0c5d06565c66531e2a6779aa419f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="mssccprjscc-file"></a>MSSCCPRJ. Fichier de contrôle de code source
Lorsqu’une solution Visual Studio ou un projet est placé sous contrôle de code source à l’aide de l’IDE, l’IDE reçoit deux éléments d’information clés à partir du contrôle de source de plug-in sous la forme de chaînes. Ces chaînes, « AuxPath » et « NomProj », sont opaques à l’IDE, mais ils sont utilisés par le plug-in pour rechercher la solution ou le projet de contrôle de version. L’IDE obtienne généralement ces chaînes de la première fois en appelant le [SccGetProjPath](../extensibility/sccgetprojpath-function.md), et il puis les enregistre dans le fichier solution ou un projet pour les appels ultérieurs à la [SccOpenProject](../extensibility/sccopenproject-function.md). Lorsqu’il est incorporé dans les fichiers solution et projet, les chaînes « AuxPath » et « NomProj » pas sont mises à jour automatiquement lorsqu’un utilisateur crée une branche, de branches, ou copie les fichiers solution et projet qui se trouvent dans le contrôle de version. Pour vous assurer que les fichiers solution et projet pointent vers leur emplacement approprié dans le contrôle de version, les utilisateurs doivent mettre à jour manuellement les chaînes. Étant donné que les chaînes sont destinés à être opaque, il ne peut pas toujours être clair comment ils doivent être mis à jour.  
  
 Le plug-in de contrôle de code source peut éviter ce problème en stockant les chaînes « AuxPath » et « NomProj » dans un fichier spécial appelé le MSSCCPRJ. Fichier de contrôle de code source. Il s’agit d’un fichier local, côté client qui est détenu et géré par le plug-in. Ce fichier n’est jamais placé sous contrôle de code source, mais est généré par le plug-in pour chaque répertoire qui contient les fichiers de contrôle de code source. Pour déterminer quels fichiers sont des fichiers solution et projet de Visual Studio, un plug-in de contrôle de code source peut comparer les extensions de fichier par rapport à une liste standard ou fourni par l’utilisateur. Une fois que l’IDE détecte qu’un plug-in prend en charge la MSSCCPRJ. Fichier de contrôle de code source, il cesse d’incorporer la « AuxPath » et les chaînes « NomProj » dans la solution, les fichiers de projet et il lit la MSSCCPRJ ces chaînes. Le fichier de contrôle de code source à la place.  
  
 Un contrôle de code source du plug-in qui prend en charge la MSSCCPRJ. Fichier de contrôle de code source doit respecter les consignes suivantes :  
  
-   Il ne peut exister qu’un seul MSSCCPRJ. Fichier de contrôle de code source par répertoire.  
  
-   Un MSSCCPRJ. Fichier de contrôle de code source peut contenir le « AuxPath » et « NomProj » pour plusieurs fichiers qui sont sous contrôle de code source dans un répertoire donné.  
  
-   La chaîne « AuxPath » ne doit pas avoir de guillemets qu’il contient. Il est autorisé à placer entre guillemets comme délimiteurs (par exemple, une paire de guillemets doubles peut être utilisée pour indiquer une chaîne vide). L’IDE supprimera tous les devis à partir de la chaîne « AuxPath » lorsqu’il est lu à partir de la MSSCCPRJ. Fichier de contrôle de code source.  
  
-   La chaîne « NomProj » dans le MSSCCPRJ. Fichier de contrôle de code source doit correspondre exactement à la chaîne retournée par la `SccGetProjPath` (fonction). Si la chaîne retournée par la fonction est entre guillemets, la chaîne dans le MSSCCPRJ. Fichier de contrôle de code source doive être placées entre guillemets autour d’elle et vice versa.  
  
-   Un MSSCCPRJ. Fichier de contrôle de code source est créé ou mis à jour chaque fois qu’un fichier est placé sous contrôle de code source.  
  
-   If un MSSCCPRJ. Fichier de contrôle de code source est supprimé, un fournisseur doit régénérer la prochaine fois qu’il effectue une opération de contrôle de code source concernant ce répertoire.  
  
-   Un MSSCCPRJ. Contrôle de code source doit suivre strictement le format défini.  
  
## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>Obtenir une Illustration de la MSSCCPRJ. Format de fichier de contrôle de code source  
 Voici un exemple de la MSSCCPRJ. Format de fichier de contrôle de code source (les numéros de ligne sont uniquement des indications et ne doivent pas être inclus dans le corps du fichier) :  
  
 [Ligne 1]`SCC = This is a Source Code Control file`  
  
 [Ligne 2]  
  
 [Ligne 3]`[TestApp.sln]`  
  
 [Ligne 4]`SCC_Aux_Path = "\\server\vss\"`  
  
 [Ligne 5]`SCC_Project_Name = "$/TestApp"`  
  
 [Ligne 6]  
  
 [Ligne 7]`[TestApp.csproj]`  
  
 [Ligne 8]`SCC_Aux_Path = "\\server\vss\"`  
  
 [Ligne 9]`SCC_Project_Name = "$/TestApp"`  
  
 La première ligne indique la fin du fichier et sert à la signature pour tous les fichiers de ce type. Cette ligne doit apparaître exactement comme dans tous les MSSCCPRJ. Fichiers SCC :  
  
 `SCC = This is a Source Code Control file`  
  
 Ce qui suit est une section de paramètres pour chaque fichier, marquée par le nom de fichier entre crochets. Cette section est répétée pour chaque fichier en cours de suivi. Cette ligne est un exemple d’un nom de fichier, à savoir, `[TestApp.csproj]`. L’IDE attend que les deux lignes suivantes. Il ne définit pas, toutefois, du style des valeurs définies. Les variables sont `SCC_Aux_Path` et `SCC_Project_Name`.  
  
 `SCC_Aux_Path = "\\server\vss\"`  
  
 `SCC_Project_Name = "$/TestApp"`  
  
 Il n’existe pas de délimiteur de fin de cette section. Le nom de fichier, ainsi que tous les littéraux qui apparaissent dans le fichier, sont définies dans le fichier d’en-tête scc.h. Pour plus d’informations, consultez [chaînes utilisées en tant que clés pour la recherche d’un plug-in de contrôle de code Source](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)   
 [Chaînes utilisées comme clés pour rechercher un plug-in de contrôle de code source](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)