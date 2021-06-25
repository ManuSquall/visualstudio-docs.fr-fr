---
title: Mssccprj. Fichier SCC | Microsoft Docs
description: En savoir plus sur le MSSCCPRJ. Fichier SCC, qui est un fichier local côté client utilisé par le plug-in de contrôle de code source, qui fonctionne avec le kit de développement logiciel (SDK) Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e006e4462522f4c464f40e0656dcef4d32c85fb7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899249"
---
# <a name="mssccprjscc-file"></a>Mssccprj. Fichier SCC
Quand vous placez une solution ou un projet Visual Studio sous contrôle de code source à l’aide de l’IDE, l’IDE reçoit deux informations clés. Les informations proviennent du plug-in de contrôle de code source sous la forme de chaînes. Ces chaînes, « AuxPath » et « ProjName », sont opaques dans l’IDE, mais elles sont utilisées par le plug-in pour rechercher la solution ou le projet dans le contrôle de version. L’IDE obtient généralement ces chaînes la première fois en appelant [SccGetProjPath](../extensibility/sccgetprojpath-function.md), puis les enregistre dans le fichier de projet ou de solution pour les appels ultérieurs à [SccOpenProject](../extensibility/sccopenproject-function.md). Lorsqu’ils sont incorporés dans les fichiers de projet et de solution, les chaînes « AuxPath » et « ProjName » ne sont pas automatiquement mises à jour quand un utilisateur branche, duplique ou copie des fichiers solution et projet qui sont dans le contrôle de version. Pour vous assurer que les fichiers de la solution et du projet pointent vers leur emplacement correct dans le contrôle de version, les utilisateurs doivent mettre à jour manuellement les chaînes. Étant donné que les chaînes sont censées être opaques, il n’est pas toujours évident de savoir comment elles doivent être mises à jour.

 Le plug-in de contrôle de code source peut éviter ce problème en stockant les chaînes « AuxPath » et « ProjName » dans un fichier spécial appelé fichier *Mssccprj. SCC* . Il s’agit d’un fichier local, côté client, qui est détenu et géré par le plug-in. Ce fichier n’est jamais placé sous contrôle de code source, mais il est généré par le plug-in pour chaque répertoire qui contient des fichiers sous contrôle de code source. Pour déterminer quels sont les fichiers de solution et de projet Visual Studio, un plug-in de contrôle de code source peut comparer les extensions de fichier à une liste standard ou fournie par l’utilisateur. Une fois que l’IDE a détecté qu’un plug-in prend en charge le fichier *Mssccprj. SCC* , il cesse d’incorporer les chaînes « AuxPath » et « ProjName » dans les fichiers solution et projet, et il lit ces chaînes à partir du fichier *Mssccprj. SCC* à la place.

 Un plug-in de contrôle de code source qui prend en charge le fichier *Mssccprj. SCC* doit respecter les instructions suivantes :

- Il ne peut y avoir qu’un seul fichier *Mssccprj. SCC* par répertoire.

- Un fichier *Mssccprj. SCC* peut contenir le « AuxPath » et le « ProjName » pour plusieurs fichiers qui sont sous contrôle de code source dans un répertoire donné.

- La chaîne « AuxPath » ne doit pas contenir de guillemets. Il est possible d’utiliser des guillemets comme séparateurs (par exemple, une paire de guillemets doubles peut être utilisée pour indiquer une chaîne vide). L’IDE supprime tous les guillemets de la chaîne « AuxPath » lors de la lecture à partir du fichier *Mssccprj. SCC* .

- Chaîne « ProjName » dans *Mssccprj. Le fichier SCC* doit correspondre exactement à la chaîne retournée par la `SccGetProjPath` fonction. Si la chaîne retournée par la fonction est entourée de guillemets, la chaîne dans le fichier *Mssccprj. SCC* doit comporter des guillemets, et vice versa.

- Un fichier *Mssccprj. SCC* est créé ou mis à jour chaque fois qu’un fichier est placé sous contrôle de code source.

- Si un fichier *Mssccprj. SCC* est supprimé, un fournisseur doit le régénérer la prochaine fois qu’il effectue une opération de contrôle de code source relative à ce répertoire.

- Un fichier *Mssccprj. SCC* doit respecter strictement le format défini.

## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>Illustration du MSSCCPRJ. Format de fichier SCC
 Voici un exemple de format de fichier *Mssccprj. SCC* (les numéros de ligne sont fournis uniquement comme un repère et ne doivent pas être inclus dans le corps du fichier) :

- [Ligne 1] `SCC = This is a Source Code Control file`

- [Ligne 2]

- [Ligne 3] `[TestApp.sln]`

- [Ligne 4] `SCC_Aux_Path = "\\server\vss\"`

- [Ligne 5] `SCC_Project_Name = "$/TestApp"`

- [Ligne 6]

- [Ligne 7] `[TestApp.csproj]`

- [Ligne 8] `SCC_Aux_Path = "\\server\vss\"`

- [Ligne 9] `SCC_Project_Name = "$/TestApp"`

 La première ligne indique l’objectif du fichier et sert de signature pour tous les fichiers de ce type. Cette ligne doit être identique à celle-ci dans tous les fichiers *Mssccprj. SCC* :

 `SCC = This is a Source Code Control file`

 La section suivante décrit en détail les paramètres de chaque fichier, marqués par le nom de fichier entre crochets. Cette section est répétée pour chaque fichier faisant l’objet d’un suivi. Cette ligne est un exemple de nom de fichier, à savoir `[TestApp.csproj]` . L’IDE attend les deux lignes suivantes. Toutefois, il ne définit pas le style des valeurs définies. Les variables sont `SCC_Aux_Path` et `SCC_Project_Name` .

 `SCC_Aux_Path = "\\server\vss\"`

 `SCC_Project_Name = "$/TestApp"`

 Il n’existe aucun délimiteur de fin pour cette section. Le nom du fichier, ainsi que tous les littéraux qui apparaissent dans le fichier, sont définis dans le fichier d’en-tête SCC. h. Pour plus d’informations, consultez [chaînes utilisées comme clés pour la recherche d’un plug-in de contrôle de code source](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md).

## <a name="see-also"></a>Voir aussi
- [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)
- [Chaînes utilisées comme clés pour la recherche d’un plug-in de contrôle de code source](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)
