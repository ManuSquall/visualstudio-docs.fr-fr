---
title: Cordes utilisées comme clés pour trouver un plug-in de contrôle de source (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f9333ff1b6742ca14dc5541bd15e92b2eb39085
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699718"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Chaînes utilisées comme clés pour rechercher un plug-in de contrôle de code source
Les chaînes suivantes sont les clés pour accéder au registre pour trouver des informations sur le plug-in de contrôle source.

 `STR_SCC_PROVIDER_REG_LOCATION`, `STR_PROVIDERREGKEY` `STR_SCCPROVIDERPATH`, `STR_SCCPROVIDERNAME` et sont des clés de registre ou des valeurs utilisées pour enregistrer un DLL comme un plug-in de contrôle source pour Visual Studio.

 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY` `SCC_KEY, SCC_FILE_SIGNATURE`, `SCC_STATUS_FILE` et sont utilisés pour décrire le format de la MSSCCPRJ. Fichier CSC.

## <a name="string-keys-and-values"></a>Clés et valeurs à cordes

|Clé|Valeur|
|---------|-----------|
|`STR_SCC_PROVIDER_REG_LOCATION`|Logiciel-SourceCodeControlProvider|
|`STR_PROVIDERREGKEY`|FournisseurRegKey|
|`STR_SCCPROVIDERPATH`|SCCServerPath|
|`STR_SCCPROVIDERNAME`|SCCServerName (en)|
|`STR_SCC_INI_SECTION`|Contrôle de code source|
|`STR_SCC_INI_KEY`|SourceCodeControlProvider|
|`SCC_PROJECTNAME_KEY`|SCC_Project_Name|
|`SCC_PROJECTAUX_KEY`|SCC_Aux_Path|
|`SCC_STATUS_FILE`|MSSCCPRJ. Scc|
|`SCC_KEY`|SCC|
|`SCC_FILE_SIGNATURE`|Un fichier de contrôle de code source|
|`SCC_NSE`|Extension de l’espace de nom|
|`SCC_NSE_PREFIX`|Préfixe protocal|
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|
|`STR_SCCHELPCOLLECTION`|AideCollection|
|`STR_UI_LANGUAGE`|UILanguage|
|`STR_SRCSAFE_ROOT_KEY`|Logiciel-Microsoft-SourceSafe|

## <a name="see-also"></a>Voir aussi
- [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)
- [Guide pratique pour installer un plug-in de contrôle de code source](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Fichier MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)
