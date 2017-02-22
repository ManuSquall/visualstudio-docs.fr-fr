---
title: "Comment&#160;: d&#233;boguer des applications&#160;Web | Microsoft Docs"
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
  - "ASP.NET Web Forms, débogage"
  - "ASP.NET, déboguer les applications Web"
  - "déboguer les applications Web ASP.NET, pendant le développement"
  - "services Web, débogage"
ms.assetid: 6440d12e-6b29-42c5-a958-99aeaaff480f
caps.latest.revision: 37
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 37
---
# Comment&#160;: d&#233;boguer des applications&#160;Web
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] est la principale technologie pour le développement d'applications Web dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Le débogueur [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fournit des outils puissants pour le débogage d'applications Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] localement ou sur un serveur distant.  Cette rubrique décrit comment déboguer un projet [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pendant le développement.  Pour plus d'informations sur le débogage d'une application Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] déjà déployée sur un serveur de production, consultez [Débogage d'applications Web déployées](../debugger/debugging-deployed-web-applications.md).  
  
 Pour déboguer une application [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] :  
  
-   Vous devez disposer des autorisations requises.  Pour plus d'informations, consultez [Configuration requise](../debugger/aspnet-debugging-system-requirements.md).  
  
-   Le débogage d'[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] doit être activé dans **Propriétés du projet**.  
  
-   Le fichier de configuration de votre application \(Web.config\) doit avoir pour valeur mode débogage.  En mode débogage, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] génère des symboles pour les fichiers générés dynamiquement et le débogueur peut être attaché à l'application [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] définit cela automatiquement lorsque vous commencez le débogage, si vous avez créé votre projet à partir du modèle de projets Web.  
  
-   Pour plus d'informations, consultez [Comment : activer le débogage pour les applications ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md).  
  
### Pour déboguer une application Web lors du développement  
  
1.  Dans le menu **Déboguer**, cliquez sur **Démarrer** pour commencer le débogage de l'application Web.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] génère le projet d'application Web, déploie l'application si nécessaire, démarre le serveur de développement ASP.NET si vous effectuez un débogage localement, et crée un attachement au processus de traitement [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
2.  Utilisez le débogueur pour définir et effacer les points d'arrêt, effectuer du pas à pas et d'autres opérations de débogage, comme pour n'importe quelle application.  
  
     Pour plus d'informations, consultez [Principes de base du débogueur](../debugger/debugger-basics.md).  
  
3.  Dans le menu **Déboguer**, cliquez sur **Arrêt Débogage** pour terminer la session de débogage, ou, dans le menu **Fichier** d'Internet Explorer, sur **Fermer**.  
  
## Voir aussi  
 [Débogage d'applications et de scripts Web](../debugger/debugging-web-applications-and-script.md)   
 [Débogage d'applications ASP.NET et AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Comment : activer le débogage pour les applications ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)