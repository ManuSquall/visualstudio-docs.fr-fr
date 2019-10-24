---
title: Chaînes utilisées comme clés pour la recherche d’un plug-in de contrôle de code source | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 07962ff9e0f9371b1fc308a35600a6819602b4f5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719454"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Chaînes utilisées comme clés pour rechercher un plug-in de contrôle de code source
Les chaînes suivantes sont les clés permettant d’accéder au registre pour rechercher des informations sur le plug-in de contrôle de code source.

 `STR_SCC_PROVIDER_REG_LOCATION`, `STR_PROVIDERREGKEY`, `STR_SCCPROVIDERPATH` et `STR_SCCPROVIDERNAME` sont des clés de registre ou des valeurs utilisées pour inscrire une DLL en tant que plug-in de contrôle de code source pour Visual Studio.

 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY`, `SCC_KEY, SCC_FILE_SIGNATURE` et `SCC_STATUS_FILE` sont utilisés pour décrire le format du MSSCCPRJ. Fichier SCC.

## <a name="string-keys-and-values"></a>Clés et valeurs de chaîne

|Touche|valeur|
|---------|-----------|
|`STR_SCC_PROVIDER_REG_LOCATION`|Software\SourceCodeControlProvider|
|`STR_PROVIDERREGKEY`|ProviderRegKey|
|`STR_SCCPROVIDERPATH`|SCCServerPath|
|`STR_SCCPROVIDERNAME`|SCCServerName|
|`STR_SCC_INI_SECTION`|Contrôle de code source|
|`STR_SCC_INI_KEY`|SourceCodeControlProvider|
|`SCC_PROJECTNAME_KEY`|SCC_Project_Name|
|`SCC_PROJECTAUX_KEY`|SCC_Aux_Path|
|`SCC_STATUS_FILE`|Mssccprj. SCC|
|`SCC_KEY`|SCC|
|`SCC_FILE_SIGNATURE`|Fichier de contrôle de code source|
|`SCC_NSE`|Extension de l’espace de noms|
|`SCC_NSE_PREFIX`|Préfixe protocole|
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|
|`STR_SCCHELPCOLLECTION`|HelpCollection|
|`STR_UI_LANGUAGE`|UILanguage|
|`STR_SRCSAFE_ROOT_KEY`|Software\Microsoft\SourceSafe|

## <a name="see-also"></a>Voir aussi
- [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)
- [Guide pratique pour installer un plug-in de contrôle de code source](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Fichier MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)