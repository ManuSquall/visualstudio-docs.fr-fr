---
title: Chaînes utilisées comme clés pour rechercher un plug-in de contrôle de code source
description: En savoir plus sur les chaînes qui sont les clés pour accéder au registre afin de trouver des informations sur le plug-in de contrôle de code source.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f25a105c442fa4a1ff8ed0f95b9c49272d751932
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899380"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Chaînes utilisées comme clés pour rechercher un plug-in de contrôle de code source
Les chaînes suivantes sont les clés permettant d’accéder au registre pour rechercher des informations sur le plug-in de contrôle de code source.

 `STR_SCC_PROVIDER_REG_LOCATION`, `STR_PROVIDERREGKEY` , `STR_SCCPROVIDERPATH` et `STR_SCCPROVIDERNAME` sont des clés de registre ou des valeurs utilisées pour inscrire une dll en tant que plug-in de contrôle de code source pour Visual Studio.

 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY` , `SCC_KEY, SCC_FILE_SIGNATURE` et `SCC_STATUS_FILE` sont utilisés pour décrire le format du Mssccprj. Fichier SCC.

## <a name="string-keys-and-values"></a>Clés et valeurs de chaîne

|Clé|Valeur|
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
