---
title: "Chaînes utilisées en tant que clés pour la recherche d’un contrôle de Source de plug-in | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d2ee5e741466b7976c8b397928cd9fccd12472fe
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Chaînes utilisées en tant que clés pour la recherche d’un contrôle de Source de plug-in
Les chaînes suivantes sont les clés d’accès au Registre pour trouver des informations sur le contrôle de source de plug-in.  
  
 `STR_SCC_PROVIDER_REG_LOCATION`, `STR_PROVIDERREGKEY`, `STR_SCCPROVIDERPATH`, et `STR_SCCPROVIDERNAME` sont des clés de Registre ou des valeurs utilisées pour inscrire une DLL comme un plug-in de contrôle de code source pour Visual Studio.  
  
 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY`, `SCC_KEY, SCC_FILE_SIGNATURE`, et `SCC_STATUS_FILE` sont utilisés pour décrire le format de la MSSCCPRJ. Fichier de contrôle de code source.  
  
## <a name="string-keys-and-values"></a>Les clés de chaîne et de valeurs  
  
|Touche|Valeur|  
|---------|-----------|  
|`STR_SCC_PROVIDER_REG_LOCATION`|Software\SourceCodeControlProvider|  
|`STR_PROVIDERREGKEY`|ProviderRegKey|  
|`STR_SCCPROVIDERPATH`|SCCServerPath|  
|`STR_SCCPROVIDERNAME`|SCCServerName|  
|`STR_SCC_INI_SECTION`|Contrôle de Code source|  
|`STR_SCC_INI_KEY`|SourceCodeControlProvider|  
|`SCC_PROJECTNAME_KEY`|SCC_Project_Name|  
|`SCC_PROJECTAUX_KEY`|SCC_Aux_Path|  
|`SCC_STATUS_FILE`|MSSCCPRJ. CONTRÔLE DE CODE SOURCE|  
|`SCC_KEY`|CONTRÔLE DE CODE SOURCE|  
|`SCC_FILE_SIGNATURE`|Un fichier de contrôle de code source|  
|`SCC_NSE`|Extension de Namespace|  
|`SCC_NSE_PREFIX`|Préfixe de Protocal|  
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|  
|`STR_SCCHELPCOLLECTION`|HelpCollection|  
|`STR_UI_LANGUAGE`|UILanguage|  
|`STR_SRCSAFE_ROOT_KEY`|Software\Microsoft\SourceSafe|  
  
## <a name="see-also"></a>Voir aussi  
 [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)   
 [Comment : installer un plug-in de contrôle de code Source](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [Fichier MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)