---
title: "D&#233;bogage d&#39;applications&#160;Web d&#233;ploy&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "applications Web ASP.NET"
  - "ASP.NET, déboguer les applications Web"
  - "déboguer des services Web"
  - "services Web, débogage"
  - "services Web XML, débogage"
  - "XML, déboguer des services Web"
ms.assetid: b938a91b-be96-416f-83bc-4177e7f3929a
caps.latest.revision: 31
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 31
---
# D&#233;bogage d&#39;applications&#160;Web d&#233;ploy&#233;es
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si vous devez déboguer une application Web qui s'exécute sur un serveur de production, cela doit être fait avec précaution.  Si vous créez un attachement au processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pour le débogage et pour atteindre un point d'arrêt, par exemple, tout le code managé dans le processus de traitement s'arrête.  Un arrêt de tout le code managé dans le processus de travail peut provoquer un arrêt de traitement pour tous les utilisateurs sur le serveur.  Avant d'effectuer un débogage sur un serveur de production, considérez l'impact potentiel sur le travail de production.  
  
 Pour utiliser [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour déboguer une application déployée, vous devez créer un attachement au processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] et vous assurer que le débogueur a accès aux symboles de l'application.  Vous devez également rechercher et ouvrir les fichiers sources pour l'application.  Pour plus d'informations, consultez [Spécifier les fichiers de symbole \(.pdb\) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), [Comment : rechercher le nom du processus ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md) et [Configuration requise](../debugger/aspnet-debugging-system-requirements.md).  
  
> [!NOTE]
>  De nombreuses applications Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] font référence à des DLL qui contiennent une logique métier ou un autre code utile.  Une référence de ce genre copie automatiquement la DLL de votre ordinateur local dans le dossier \\bin du répertoire virtuel de l'application Web.  Lorsque vous effectuez un débogage, rappelez\-vous que votre application Web référence cette copie de la DLL et non pas celle qui se trouve sur votre ordinateur local.  
  
 La procédure d'attachement au processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] est identique à l'attachement à tout autre processus distant.  Lorsque vous êtes attaché, si le projet approprié n'est pas ouvert, une boîte de dialogue apparaît lorsque l'application s'arrête.  Elle vous demande d'indiquer l'emplacement des fichiers sources pour l'application.  Le nom de fichier que vous spécifiez dans la boîte de dialogue doit correspondre au nom de fichier spécifié dans les symboles de débogage, situés sur le serveur Web.  Pour plus d'informations, consultez [Attacher aux processus en cours d'exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
## Voir aussi  
 [Débogage d'applications ASP.NET et AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Débogage d'applications et de scripts Web](../debugger/debugging-web-applications-and-script.md)   
 [Comment : activer le débogage pour les applications ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [Comment : rechercher le nom du processus ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md)   
 [Spécifier les fichiers de symbole \(.pdb\) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)