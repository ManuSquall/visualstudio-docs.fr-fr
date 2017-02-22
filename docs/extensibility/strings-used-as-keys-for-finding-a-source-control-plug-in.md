---
title: "Cha&#238;nes utilis&#233;es comme cl&#233;s pour rechercher un contr&#244;le de Source de plug-in | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "source plug-ins de contrôle, utilisés pour rechercher des chaînes"
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Cha&#238;nes utilis&#233;es comme cl&#233;s pour rechercher un contr&#244;le de Source de plug-in
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les chaînes suivantes sont les clés d'accès au Registre pour trouver des informations sur le contrôle de code source du plug\-in.  
  
 `STR_SCC_PROVIDER_REG_LOCATION`, `STR_PROVIDERREGKEY`, `STR_SCCPROVIDERPATH`, et `STR_SCCPROVIDERNAME` sont des clés de Registre ou de valeurs utilisées pour enregistrer une DLL comme un plug\-in de contrôle de code source pour Visual Studio.  
  
 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY`, `SCC_KEY, SCC_FILE_SIGNATURE`, et `SCC_STATUS_FILE` sont utilisés pour décrire le format de la MSSCCPRJ. Fichier de contrôle de code source.  
  
## Clés et des valeurs  
  
|Clé|Valeur|  
|---------|------------|  
|`STR_SCC_PROVIDER_REG_LOCATION`|Software\\SourceCodeControlProvider|  
|`STR_PROVIDERREGKEY`|ProviderRegKey|  
|`STR_SCCPROVIDERPATH`|SCCServerPath|  
|`STR_SCCPROVIDERNAME`|SCCServerName|  
|`STR_SCC_INI_SECTION`|Contrôle de Code source|  
|`STR_SCC_INI_KEY`|SourceCodeControlProvider|  
|`SCC_PROJECTNAME_KEY`|SCC\_Project\_Name|  
|`SCC_PROJECTAUX_KEY`|SCC\_Aux\_Path|  
|`SCC_STATUS_FILE`|MSSCCPRJ. CONTRÔLE DE CODE SOURCE|  
|`SCC_KEY`|CONTRÔLE DE CODE SOURCE|  
|`SCC_FILE_SIGNATURE`|Un fichier de contrôle de code source|  
|`SCC_NSE`|Extension de l'espace de noms|  
|`SCC_NSE_PREFIX`|Préfixe de Protocol|  
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|  
|`STR_SCCHELPCOLLECTION`|HelpCollection|  
|`STR_UI_LANGUAGE`|UILanguage|  
|`STR_SRCSAFE_ROOT_KEY`|Software\\Microsoft\\SourceSafe|  
  
## Voir aussi  
 [Plug\-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)   
 [Comment : installer un plug\-in de contrôle de code Source](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [MSSCCPRJ. Fichier de contrôle de code source](../extensibility/mssccprj-scc-file.md)