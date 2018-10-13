---
title: 'Procédure : collecte des données de performances pour un site web | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vsperf.url.url
- vsperf.chooseurl
- vs.performance.wizard.asppage
- vsperf.url.ok
- vsperf.url.cancel
helpviewer_keywords:
- Profiling Tools,profiling ASP.NET
- web sites, performance profiling
- ASP.NET, performance profilng
ms.assetid: a62d27fd-a966-4065-bebe-6874195a71fb
caps.latest.revision: 38
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b1ebe51079735beab22e63d595ae3a3cfbee3e5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49185897"
---
# <a name="how-to-collect-performance-data-for-a-web-site"></a>Procédure : collecte des données de performances pour un site web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez utiliser l’ **Assistant Performance** pour collecter des données de performances pour une application web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Vous pouvez profiler une application web qui est ouverte dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ou profiler un site web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] qui se trouve sur votre ordinateur local et qui n’est pas ouvert dans l’IDE [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
> [!NOTE]
>  L’ **Assistant Performance** vous permet d’ajouter des données d’interaction de couche (TIP), des données de performance JScript, ou les deux, aux données de profilage collectées. L’option TIP collecte des données auprès des processus côté serveur. Le profilage JScript collecte des données auprès des scripts qui s’exécutent sur un site web local ou distant. Dans la plupart des cas, vous devez choisir une seule des options.  
  
 Selon les valeurs des autorisations d’accès utilisateur rendues disponibles par l’administrateur, un utilisateur peut ou non disposer de l’autorisation de sécurité pour créer une session de profileur sur l’ordinateur qui héberge le processus ASP.NET. Les exemples suivants montrent les différences possibles entre les utilisateurs :  
  
-   Certains utilisateurs peuvent accéder à des fonctionnalités de profilage avancées quand l’administrateur a défini le démarrage du pilote et du service.  
  
-   Les utilisateurs de domaine peuvent accéder seulement au profilage d’échantillon.  
  
-   Certains utilisateurs peuvent refuser l’accès au profilage à tous les autres utilisateurs.  
  
 Pour plus d’informations, consultez [Profilage et sécurité Windows Vista](../profiling/profiling-and-windows-vista-security.md), ainsi que les options d’administration dans [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### <a name="to-profile-a-web-site-project"></a>Pour profiler un projet de site web  
  
1.  Ouvrez le projet web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] dans [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] ou [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)].  
  
2.  Dans le menu **Analyser** , cliquez sur **Lancer l’Assistant Performance**.  
  
3.  Sur la première page de l’Assistant, sélectionnez une méthode de profilage, puis cliquez sur **Suivant**. Pour plus d’informations sur les méthodes de profilage, consultez [Understanding Performance Collection Methods](../profiling/understanding-performance-collection-methods.md) (Fonctionnement des méthodes de collecte des données de performances). Notez que la méthode de profilage du visualiseur concurrentiel n’est pas disponible pour les applications web.  
  
4.  Dans la liste déroulante **Quelle application voulez-vous cibler pour le profilage ?** , vérifiez que le projet actuel est sélectionné, puis cliquez sur **Suivant**.  
  
5.  Sur la troisième page de l’Assistant, vous pouvez choisir d’ajouter des données de profilage d’interaction de couche (TIP), des données du JavaScript s’exécutant dans les pages web, ou les deux.  
  
    -   Pour collecter l’interaction de couche, cochez la case **Activer le profilage d’interaction de couche** .  
  
    -   Pour collecter des données du JavaScript s’exécutant dans les pages web, cochez la case **Profiler JavaScript** .  
  
6.  Cliquez sur **Suivant**.  
  
7.  Dans la quatrième page de l’Assistant, cliquez sur **Terminer**.  
  
8.  Une session de performance est créée pour l’application [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] et le site web est démarré dans le navigateur. Utilisez les fonctionnalités que vous voulez profiler, puis fermez le navigateur.  
  
     Le profileur génère le fichier de données et affiche la vue Résumé des données dans la fenêtre principale de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
### <a name="to-profile-a-web-site-without-opening-a-project-in-visual-studio"></a>Pour profiler un site web sans ouvrir un projet dans Visual Studio  
  
1.  Ouvrez [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] ou [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)].  
  
2.  Dans le menu **Analyser** , cliquez sur **Lancer l’Assistant Performance**.  
  
3.  Sur la première page de l’Assistant, sélectionnez une méthode de profilage, puis cliquez sur **Suivant**. Pour plus d’informations, consultez [Understanding Performance Collection Methods](../profiling/understanding-performance-collection-methods.md) (Fonctionnement des méthodes de collecte des données de performances).  
  
4.  Dans la deuxième page de l’Assistant, sélectionnez l’option sur **Profiler une application ASP.NET ou JavaScript** , puis cliquez sur **Suivant**.  
  
5.  Dans la zone **Quel URL ou chemin d’accès exécutera votre application web** sur la troisième page de l’Assistant, entrez l’URL de la page d’accueil de l’application, puis cliquez sur **Suivant**.  
  
    -   Pour un site web basé sur un serveur (IIS), tapez une URL telle que **http://localhost/MySite/default.aspx**. Ceci déclenche le profilage de l’application [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] sur l’ordinateur local à la racine de l’application MonSite et le démarrage de la page defaut.aspx dans Internet Explorer pour démarrer la session.  
  
    -   Pour un site web basé sur un fichier, tapez un chemin comme file///**c:\sites_web\MonSite\defaut.aspx**. Cela déclenche le profilage de l’application [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] située sur c:\webSites\MySite et l’ouverture de la page http://localhost:nnnn/MySite/default.aspx dans Internet Explorer pour démarrer la session.  
  
    -   Pour les sites externes dont vous souhaitez collecter les données JavaScript, tapez une URL telle que http://www.contoso.com.  
  
     Pour plus d’informations, consultez les pages de propriétés un binaire cible [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] .  
  
6.  Sur la troisième page de l’Assistant, vous pouvez choisir d’ajouter des données de profilage d’interaction de couche (TIP), des données du JavaScript s’exécutant dans les pages web, ou les deux.  
  
    -   Pour collecter l’interaction de couche, cochez la case **Activer le profilage d’interaction de couche** .  
  
    -   Pour collecter des données du JavaScript s’exécutant dans les pages web, cochez la case **Profiler JavaScript** .  
  
7.  Cliquez sur **Suivant**.  
  
8.  Dans la quatrième page de l’Assistant, cliquez sur **Terminer**.  
  
9. Une session de performance est créée pour l’application ASP.NET et le site web est démarré dans le navigateur. Utilisez les fonctionnalités que vous voulez profiler, puis fermez le navigateur.  
  
     Le profileur génère le fichier de données et affiche la vue Résumé des données dans la fenêtre principale de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Vues d’ensemble](../profiling/overviews-performance-tools.md)   
 [Configuration de sessions de performance](../profiling/configuring-performance-sessions.md)   
 [Présentation des valeurs de données d’instrumentation](../profiling/understanding-instrumentation-data-values.md)   
 [Présentation des valeurs de données d’échantillonnage](../profiling/understanding-sampling-data-values.md)



