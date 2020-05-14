---
title: MSSCCPRJ. Fichier SCC (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89511b7c8b69c5793eceef7d58153dde253a4f47
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702471"
---
# <a name="mssccprjscc-file"></a>MSSCCPRJ. Fichier SCC
Lorsque vous placez une solution ou un projet Visual Studio sous contrôle source à l’aide de l’IDE, l’IDE reçoit deux informations clés. L’information provient du plug-in de contrôle source sous forme de cordes. Ces chaînes, "AuxPath" et "ProjName", sont opaques pour l’IDE, mais elles sont utilisées par le plug-in pour localiser la solution ou le projet dans le contrôle de la version. L’IDE obtient généralement ces chaînes la première fois en appelant le [SccGetProjPath](../extensibility/sccgetprojpath-function.md), et il les enregistre ensuite dans la solution ou le fichier de projet pour les appels futurs à la [SccOpenProject](../extensibility/sccopenproject-function.md). Lorsqu’elles sont intégrées dans les fichiers de la solution et du projet, les chaînes "AuxPath" et "ProjName" ne sont pas automatiquement mises à jour lorsqu’un utilisateur dispose, une fourchette ou copie des fichiers de solution et de projet qui sont dans le contrôle de la version. Pour s’assurer que la solution et les fichiers de projet indiquent leur emplacement correct dans le contrôle de la version, les utilisateurs doivent mettre à jour manuellement les chaînes. Parce que les cordes sont censées être opaques, il peut ne pas toujours être clair comment ils doivent être mis à jour.

 Le plug-in de contrôle source peut éviter ce problème en stockant les chaînes "AuxPath" et "ProjName" dans un fichier spécial appelé le fichier *MSSCCPRJ.SCC.* Il s’agit d’un fichier local côté client qui est détenu et entretenu par le plug-in. Ce fichier n’est jamais placé sous contrôle source, mais est généré par le plug-in pour chaque répertoire qui contient des fichiers contrôlés par la source. Pour déterminer quels fichiers sont des fichiers de solutions visual Studio et de projet, un plug-in de contrôle source peut comparer les extensions de fichiers par rapport à une liste standard ou fournie par l’utilisateur. Une fois qu’un plug-in prend en charge le fichier *MSSCCPRJ.SCC,* il cesse d’intégrer les chaînes « AuxPath » et « ProjName » dans les fichiers de solutions et de projet, et il lit ces chaînes du fichier *MSSCCPRJ.SCC* à la place.

 Un plug-in de contrôle source qui prend en charge le fichier *MSSCCPRJ.SCC* doit respecter les lignes directrices suivantes :

- Il ne peut y avoir qu’un seul fichier *MSSCCPRJ.SCC* par répertoire.

- Un fichier *MSSCCPRJ.SCC* peut contenir les "AuxPath" et "ProjName" pour plusieurs fichiers qui sont sous contrôle source dans un répertoire donné.

- La chaîne "AuxPath" ne doit pas avoir de citations à l’intérieur. Il est permis d’avoir des citations autour d’elle comme délimitants (par exemple, une paire de citations doubles peuvent être utilisées pour indiquer une chaîne vide). L’IDE dépouillera toutes les citations de la chaîne "AuxPath" lorsqu’elle sera lue à partir du fichier *MSSCCPRJ.SCC.*

- La chaîne "ProjName" dans le *MSSCCPRJ. Le fichier SCC* doit correspondre `SccGetProjPath` exactement à la chaîne retournée de la fonction. Si la chaîne retournée par la fonction a des citations autour d’elle, la chaîne dans le fichier *MSSCCPRJ.SCC* doit avoir des citations autour d’elle, et vice versa.

- Un fichier *MSSCCPRJ.SCC* est créé ou mis à jour chaque fois qu’un fichier est placé sous contrôle source.

- Si un fichier *MSSCCPRJ.SCC* est supprimé, un fournisseur doit le régénérer la prochaine fois qu’il effectue une opération de contrôle source concernant cet annuaire.

- Un fichier *MSSCCPRJ.SCC* doit suivre strictement le format défini.

## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>Une illustration du MSSCCPRJ. Format de fichier SCC
 Voici un échantillon du format de fichier *MSSCCPRJ.SCC* (les numéros de ligne ne sont fournis que comme guide, et ne devraient pas être inclus dans l’organe de dossier) :

- [Ligne 1]`SCC = This is a Source Code Control file`

- [Ligne 2]

- [Ligne 3]`[TestApp.sln]`

- [Ligne 4]`SCC_Aux_Path = "\\server\vss\"`

- [Ligne 5]`SCC_Project_Name = "$/TestApp"`

- [Ligne 6]

- [Ligne 7]`[TestApp.csproj]`

- [Ligne 8]`SCC_Aux_Path = "\\server\vss\"`

- [Ligne 9]`SCC_Project_Name = "$/TestApp"`

 La première ligne indique le but du fichier et sert de signature pour tous les fichiers de ce type. Cette ligne devrait apparaître exactement comme ceci dans tous les fichiers *MSSCCPRJ.SCC:*

 `SCC = This is a Source Code Control file`

 La section suivante détaille les paramètres de chaque fichier, marqués par le nom du fichier entre parenthèses carrées. Cette section est répétée pour chaque fichier suivi. Cette ligne est un échantillon d’un nom de fichier, à savoir, `[TestApp.csproj]`. L’IDE s’attend aux deux lignes suivantes. Il ne définit cependant pas le style des valeurs définies. Les variables `SCC_Aux_Path` `SCC_Project_Name`sont et .

 `SCC_Aux_Path = "\\server\vss\"`

 `SCC_Project_Name = "$/TestApp"`

 Il n’y a pas de délimital final à cette section. Le nom du fichier, ainsi que tous les littérals qui apparaissent dans le fichier, sont définis dans le fichier d’en-tête scc.h. Pour plus d’informations, voir [Les chaînes utilisées comme clés pour trouver un plug-in de contrôle source](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md).

## <a name="see-also"></a>Voir aussi
- [Plug-ins de contrôle des sources](../extensibility/source-control-plug-ins.md)
- [Cordes utilisées comme clés pour trouver un plug-in de contrôle source](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)
