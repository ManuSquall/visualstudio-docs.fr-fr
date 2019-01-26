---
title: MSSCCPRJ. Fichier de SCC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 028490e6c23051496202fad2d85b0d11cc434218
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54964286"
---
# <a name="mssccprjscc-file"></a>MSSCCPRJ. Fichier de contrôle de code source
Lorsque vous placez une solution Visual Studio ou un projet sous contrôle de code source à l’aide de l’IDE, l’IDE reçoit deux informations essentielles. Les informations proviennent du plug-in sous la forme de chaînes de contrôle de code source. Ces chaînes, « AuxPath » et « ProjName », sont opaques à l’IDE, mais elles sont utilisées par le plug-in pour rechercher la solution ou le projet dans le contrôle de version. L’IDE obtient généralement ces chaînes de la première fois en appelant le [SccGetProjPath](../extensibility/sccgetprojpath-function.md), et il les enregistre ensuite dans le fichier solution ou un projet pour les appels suivants à la [SccOpenProject](../extensibility/sccopenproject-function.md). Lorsqu’il est incorporé dans les fichiers solution et projet, les chaînes « AuxPath » et « ProjName » ne sont pas automatiquement mis à jour un utilisateur, les branchements, branches ou copie des fichiers solution et projet qui se trouvent dans le contrôle de version. Pour vous assurer que les fichiers solution et projet pointent vers leur emplacement correct dans le contrôle de version, les utilisateurs doivent mettre à jour manuellement les chaînes. Étant donné que les chaînes sont destinés à être opaque, il peut pas toujours clair comment ils doivent être mis à jour.  
  
 Le plug-in de contrôle de code source peut éviter ce problème en stockant les chaînes « AuxPath » et « ProjName » dans un fichier spécial appelé le *MSSCCPRJ.SCC* fichier. C’est un fichier local, côté client qui est détenu et géré par le plug-in. Ce fichier n’est jamais placé sous contrôle de code source, mais est généré par le plug-in pour chaque répertoire qui contient les fichiers sous contrôle de code source. Pour déterminer quels fichiers sont des fichiers solution et projet de Visual Studio, un plug-in de contrôle de code source peut comparer les extensions de fichier par rapport à une liste standard ou fourni par l’utilisateur. Une fois que l’IDE détecte qu’un plug-in prend en charge la *MSSCCPRJ.SCC* fichier, il cesse d’incorporer les chaînes « AuxPath » et « ProjName » dans les fichiers solution et projet, et il lit ces chaînes à partir de la *MSSCCPRJ.SCC*de fichiers à la place.  
  
 Un plug-in de contrôle de code source qui prend en charge la *MSSCCPRJ.SCC* fichier doit respecter les consignes suivantes :  
  
-   Il peut être seulement un *MSSCCPRJ.SCC* fichiers par répertoire.  
  
-   Un *MSSCCPRJ.SCC* fichier peut contenir le « AuxPath » et « ProjName » pour plusieurs fichiers qui sont sous contrôle de code source dans un répertoire donné.  
  
-   La chaîne « AuxPath » ne doit pas contenir de guillemets qu’il contient. Il est autorisé à placer entre guillemets comme délimiteurs (par exemple, une paire de guillemets doubles permettre servir à indiquer une chaîne vide). L’IDE supprimera tous les devis à partir de la chaîne « AuxPath » lorsqu’il est lu à partir de la *MSSCCPRJ.SCC* fichier.  
  
-   Chaîne de la « ProjName » dans le *MSSCCPRJ. Fichier de SCC* doit correspondre exactement à la chaîne retournée par la `SccGetProjPath` (fonction). Si la chaîne retournée par la fonction a entre guillemets, la chaîne dans le *MSSCCPRJ.SCC* fichier doit avoir des guillemets autour d’elle et vice versa.  
  
-   Un *MSSCCPRJ.SCC* fichier est créé ou mis à jour chaque fois qu’un fichier est placé sous contrôle de code source.  
  
-   Si un *MSSCCPRJ.SCC* fichier est supprimé, un fournisseur doit régénérer la prochaine fois qu’il effectue une opération de contrôle de code source concernant ce répertoire.  
  
-   Un *MSSCCPRJ.SCC* fichier doit respecter strictement le format défini.  
  
## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>Obtenir une illustration de la MSSCCPRJ. Format de fichier de contrôle de code source  
 Voici un exemple de la *MSSCCPRJ.SCC* format de fichier (les numéros de ligne sont fournies uniquement comme guide et ne doivent pas être inclus dans le corps du fichier) :  
  
 [Ligne 1] `SCC = This is a Source Code Control file`  
  
 [Ligne 2]  
  
 [Ligne 3] `[TestApp.sln]`  
  
 [Ligne 4] `SCC_Aux_Path = "\\server\vss\"`  
  
 [Ligne 5] `SCC_Project_Name = "$/TestApp"`  
  
 [Ligne 6]  
  
 [Ligne 7] `[TestApp.csproj]`  
  
 [Ligne 8] `SCC_Aux_Path = "\\server\vss\"`  
  
 [Ligne 9] `SCC_Project_Name = "$/TestApp"`  
  
 La première ligne indique l’objectif du fichier et sert de signature pour tous les fichiers de ce type. Cette ligne doit apparaître exactement comme cela dans tous les *MSSCCPRJ.SCC* fichiers :  
  
 `SCC = This is a Source Code Control file`  
  
 La section suivante décrit en détail les paramètres pour chaque fichier, marquée par le nom de fichier entre crochets. Cette section est répétée pour chaque fichier en cours de suivi. Cette ligne est un exemple d’un nom de fichier, à savoir, `[TestApp.csproj]`. L’IDE attend les deux lignes suivantes. Il ne définit pas le cas, toutefois, le style des valeurs définies. Les variables sont `SCC_Aux_Path` et `SCC_Project_Name`.  
  
 `SCC_Aux_Path = "\\server\vss\"`  
  
 `SCC_Project_Name = "$/TestApp"`  
  
 Il n’existe aucun délimiteur de fin de cette section. Le nom de fichier, ainsi que tous les littéraux qui apparaissent dans le fichier, sont définis dans le fichier d’en-tête scc.h. Pour plus d’informations, consultez [chaînes utilisées comme clés pour rechercher un contrôle de source de plug-in](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)   
 [Chaînes utilisées comme clés pour rechercher un contrôle de source de plug-in](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)