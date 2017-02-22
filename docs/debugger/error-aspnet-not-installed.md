---
title: "Erreur&#160;: ASP.NET n&#39;est pas install&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.http_not_supported"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ASP.NET, messages d'erreur d'installation"
  - "débogueur, erreurs d'applications Web"
  - "messages d'erreur, ASP.NET"
  - "applications Web, erreurs"
ms.assetid: 6286dd3d-3e2b-4edd-959d-81e0ed45500b
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Erreur&#160;: ASP.NET n&#39;est pas install&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette erreur se produit quand [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] n'est pas installé correctement sur l'ordinateur que vous tentez de déboguer.  Cela peut signifier qu'[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] n'a jamais été installé ou qu'[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] a été installé avant les services IIS \(Internet Information Services\).  
  
### Pour réinstaller ASP.NET  
  
1.  À partir d'une invite de commandes, exécutez la commande suivante :  
  
    ```  
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     où *version* représente le numéro de version du .NET Framework installé sur votre ordinateur, par exemple v1.0.370.  Vous pouvez déterminer la version du .NET Framework en examinant le contenu du répertoire `\WINDOWS\Microsoft.NET\Framework`.  
  
    > [!NOTE]
    >  Sous Windows Server 2003, vous pouvez installer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] à l'aide de l'application **Ajout\/Suppression de programmes** du Panneau de configuration.  
  
## Voir aussi  
 [Débogage d'applications Web : erreurs et dépannage](../debugger/debugging-web-applications-errors-and-troubleshooting.md)