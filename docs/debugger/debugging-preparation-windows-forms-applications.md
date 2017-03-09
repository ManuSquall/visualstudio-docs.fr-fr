---
title: "Pr&#233;paration du d&#233;bogage&#160;: applications Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "déboguer (C#), applications Windows"
  - "déboguer (J#), applications Windows"
  - "déboguer (Visual Basic), applications Windows"
  - "déboguer (Visual Studio), applications Windows"
  - "déboguer les applications Windows"
  - "applications Windows, débogage"
ms.assetid: 7092ee7f-8378-4def-aef8-1695bd97cf14
caps.latest.revision: 28
caps.handback.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Pr&#233;paration du d&#233;bogage&#160;: applications Windows Forms
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le modèle de projet Windows Forms crée une application Windows Forms.  Le débogage de ce type d'application dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] est assez simple.  Pour plus d'informations, consultez [Creating a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
 Lorsque vous créez un projet Windows Forms à l'aide du modèle de projet, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crée automatiquement les paramètres requis pour les configurations Debug et Release.  Si nécessaire, vous pouvez modifier ces paramètres.  Ces paramètres peuvent être modifiés dans la boîte de dialogue **Pages de propriétés de \<nom du projet\>** \(**My Project** en Visual Basic\).  
  
 Pour plus d'informations, consultez [Paramètres de propriété recommandés](../debugger/managed-debugging-recommended-property-settings.md).  
  
 Le tableau suivant affiche un paramètre de propriété recommandé supplémentaire.  
  
### Propriétés de configuration sous l'onglet Déboguer  
  
|**Nom de la propriété**|**Paramètre**|  
|-----------------------------|-------------------|  
|**Action de démarrage**|-   Affectez la plupart du temps la valeur **Démarrer le projet**.  Affectez la valeur **Démarrer le programme externe** si vous souhaitez démarrer un autre fichier exécutable lorsque vous commencez le débogage \(habituellement pour déboguer des DLL\).|  
  
 Vous pouvez déboguer des applications Windows Forms dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou en établissant un attachement avec une application en cours d'exécution.  Pour plus d'informations sur les attachements, consultez [Attacher aux processus en cours d'exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
### Pour déboguer une application Windows Forms Visual Basic, C\# ou F\#  
  
1.  Ouvrez le projet dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
2.  Créez des points d'arrêt selon vos besoins.  
  
     Comme les applications Windows Forms sont pilotées par événements, vos points d'arrêt sont placés dans le code du gestionnaire d'événements ou dans des méthodes appelées par le code du gestionnaire d'événements.  Les points d'arrêt sont généralement placés dans les événements suivants :  
  
    1.  Événements associés à un contrôle, tels que Click, Enter, etc.  
  
    2.  Événements associés au démarrage et à l'arrêt d'une application, tels que Load, Activated, etc.  
  
    3.  Événements de focus et de validation.  
  
     Pour plus d'informations, consultez [Création de gestionnaires d'événements dans les Windows Forms](../Topic/Creating%20Event%20Handlers%20in%20Windows%20Forms.md).  
  
3.  Dans le menu **Déboguer**, cliquez sur **Démarrer**.  
  
4.  Procédez au débogage à l'aide des techniques présentées dans [Principes de base du débogueur](../debugger/debugger-basics.md).  
  
## Voir aussi  
 [Débogage du code managé](../debugger/debugging-managed-code.md)   
 [Types de projets C\#, F\# et Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Comment : définir des configurations Debug et Release](../debugger/how-to-set-debug-and-release-configurations.md)   
 [Paramètres de projet pour des configurations Debug C\#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Paramètres de projet pour une configuration Debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Attacher aux processus en cours d'exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Windows Forms](../Topic/Windows%20Forms.md)