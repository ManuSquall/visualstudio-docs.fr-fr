---
title: "Pr&#233;paration du d&#233;bogage&#160;: applications Web ASP.NET | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "déboguer (Visual Studio), applications Web"
  - "déboguer les applications Web ASP.NET"
ms.assetid: bcfb1080-98d1-42f9-96af-186fb14f232a
caps.latest.revision: 35
caps.handback.revision: 35
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Pr&#233;paration du d&#233;bogage&#160;: applications Web ASP.NET
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le modèle de site Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] crée une application Web Form.  Lorsque vous créez un site Web à l'aide de ce modèle, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crée les paramètres par défaut pour le débogage.  Dans la boîte de dialogue **Propriétés du projet**, vous pouvez spécifier si vous souhaitez que la page Web soit une page démarrage.  Lorsque vous commencez à déboguer un site Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] avec ces paramètres par défaut, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] démarre Internet Explorer et attache le débogueur au processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] \(aspnet\_wp.exe ou w3wp.exe\).  Pour plus d'informations, consultez [Configuration requise](../debugger/aspnet-debugging-system-requirements.md).  
  
### Pour créer une application Web Forms  
  
1.  Dans le menu **Fichier**, cliquez sur **Nouveau site Web**.  
  
2.  Dans la boîte de dialogue **Nouveau site Web**, sélectionnez **Site Web** [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
3.  Cliquez sur **OK**.  
  
### Pour déboguer votre Web Form  
  
1.  Définissez un ou plusieurs points d'arrêt dans vos fonctions et gestionnaires d'événements.  
  
     Pour plus d'informations, consultez [Breakpoints and Tracepoints](http://msdn.microsoft.com/fr-fr/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2.  Lorsqu'un point d'arrêt est atteint, parcourez le code à l'intérieur de la fonction.  Observez l'exécution de votre code jusqu'à cerner le problème.  
  
     Pour plus d'informations, consultez [Stepping](http://msdn.microsoft.com/fr-fr/8791dac9-64d1-4bb9-b59e-8d59af1833f9) et [Débogage d'applications et de scripts Web](../debugger/debugging-web-applications-and-script.md).  
  
## Modification des configurations par défaut  
 Si vous le souhaitez, vous êtes autorisé à modifier les valeurs par défaut des configurations Debug et Release créées par [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Pour plus d'informations, consultez [Comment : définir des configurations Debug et Release](../debugger/how-to-set-debug-and-release-configurations.md).  
  
#### Pour modifier la configuration Debug par défaut  
  
1.  Cliquez avec le bouton droit sur le site Web dans l'**Explorateur de solutions**, puis sélectionnez **Pages de propriétés** pour ouvrir la boîte de dialogue **Pages de propriétés**.  
  
2.  Cliquez sur **Options de démarrage**.  
  
3.  Pour **Action de démarrage**, choisissez la page Web qui doit être affichée en premier.  
  
4.  Sous **Débogueurs**, assurez\-vous que la case à cocher **Débogage ASP.NET** est activée.  
  
     Pour plus d'informations, consultez [Paramètres des pages de propriétés pour les projets Web](../debugger/property-pages-settings-for-web-projects.md).  
  
## Voir aussi  
 [Paramètres et préparation du débogage](../debugger/debugger-settings-and-preparation.md)   
 [Principes de base du débogueur](../debugger/debugger-basics.md)   
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Débogage du code managé](../debugger/debugging-managed-code.md)