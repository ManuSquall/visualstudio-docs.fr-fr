---
title: 'Procédure : collecter des données de performances pour un site web | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f91646575fba2df1f48c08adc7a9233bb63f27df
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62974007"
---
# <a name="how-to-collect-performance-data-for-a-web-site"></a>Procédure : collecter des données de performances pour un site web

Vous pouvez utiliser **l’Assistant Performance** pour collecter des données de performances pour une application web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Vous pouvez profiler une application web ouverte dans Visual Studio, ou bien un site web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] qui se trouve sur votre ordinateur local et qui n’est pas ouvert dans l’IDE de Visual Studio.

> [!NOTE]
> L’ **Assistant Performance** vous permet d’ajouter des données d’interaction de couche (TIP), des données de performance JScript, ou les deux, aux données de profilage collectées. L’option TIP collecte des données auprès des processus côté serveur. Le profilage JScript collecte des données auprès des scripts qui s’exécutent sur un site web local ou distant. Dans la plupart des cas, vous devez choisir une seule des options.

 Selon les valeurs des autorisations d’accès utilisateur rendues disponibles par l’administrateur, un utilisateur peut ou non disposer de l’autorisation de sécurité pour créer une session de profileur sur l’ordinateur qui héberge le processus ASP.NET. Les exemples suivants montrent les différences possibles entre les utilisateurs :

- Certains utilisateurs peuvent accéder à des fonctionnalités de profilage avancé lorsque l’administrateur a défini le démarrage du pilote et du service.

- Les utilisateurs de domaine peuvent accéder uniquement au profilage d’échantillon.

- Certains utilisateurs peuvent refuser l’accès au profilage à tous les autres utilisateurs.

  Pour plus d’informations, consultez [Profilage et sécurité Windows Vista](../profiling/profiling-and-windows-vista-security.md), ainsi que les options d’administration dans [VSPerfCmd](../profiling/vsperfcmd.md).

## <a name="to-profile-a-web-site-project"></a>Pour profiler un projet de site web

1. Ouvrez le projet web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] dans Visual Studio.

2. Dans le menu **Analyser**, sélectionnez **Profileur de performances**, **Explorateur de performances**, puis**Démarrer**.

3. Sur la première page de l’Assistant, sélectionnez une méthode de profilage, puis cliquez sur **Suivant**. Pour plus d’informations sur les méthodes de profilage, consultez [Présenter les méthodes de collecte des performances](../profiling/understanding-performance-collection-methods.md). Notez que la méthode de profilage du visualiseur concurrentiel n’est pas disponible pour les applications web.

4. Dans la liste déroulante **Quelle application voulez-vous cibler pour le profilage ?** , vérifiez que le projet actuel est sélectionné, puis cliquez sur **Suivant**.

5. Dans la troisième page de l’Assistant, vous pouvez choisir d’ajouter des données de profilage d’interaction de couche (TIP), des données du code JavaScript s’exécutant dans les pages web ou les deux.

    - Pour collecter l’interaction de couche, cochez la case **Activer le profilage d’interaction de couche** .

    - Pour collecter des données du JavaScript s’exécutant dans les pages web, cochez la case **Profiler JavaScript** .

6. Cliquez sur **Suivant**.

7. Dans la quatrième page de l’Assistant, cliquez sur **Terminer**.

8. Une session de performance est créée pour l’application [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], et le site web est démarré dans le navigateur. Utilisez les fonctionnalités que vous voulez profiler, puis fermez le navigateur.

     Le profileur génère le fichier de données et affiche la vue Résumé des données dans la fenêtre principale de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="to-profile-a-web-site-without-opening-a-project-in-visual-studio"></a>Pour profiler un site web sans ouvrir un projet dans Visual Studio

1. Ouvrez Visual Studio.

2. Dans le menu **Analyser**, sélectionnez **Profileur de performances**, **Explorateur de performances**, puis**Démarrer**.

3. Sur la première page de l’Assistant, sélectionnez une méthode de profilage, puis cliquez sur **Suivant**. Pour plus d’informations, consultez [Understanding Performance Collection Methods](../profiling/understanding-performance-collection-methods.md) (Fonctionnement des méthodes de collecte des données de performances).

4. Dans la deuxième page de l’Assistant, sélectionnez l’option sur **Profiler une application ASP.NET ou JavaScript** , puis cliquez sur **Suivant**.

5. Dans la zone **Quel URL ou chemin d’accès exécutera votre application web** sur la troisième page de l’Assistant, entrez l’URL de la page d’accueil de l’application, puis cliquez sur **Suivant**.

   - Pour un site web basé sur un serveur (IIS), tapez une URL telle que **<`http://localhost/MySite/default.aspx`>**. Ceci déclenche le profilage de l’application [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] sur l’ordinateur local à la racine de l’application MonSite et le démarrage de la page defaut.aspx dans Internet Explorer pour démarrer la session.

   - Pour un site web basé sur un fichier, tapez un chemin comme file///**c:\sites_web\MonSite\defaut.aspx**. Cela déclenche le profilage de l’application [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] située sur c:\webSites\MySite et l’ouverture de la page `http://localhost:nnnn/MySite/default.aspx` dans Internet Explorer pour démarrer la session.

   - Pour les sites externes dont vous souhaitez collecter les données JavaScript, tapez une URL telle que `http://www.contoso.com`.

     Pour plus d’informations, consultez les pages de propriétés un binaire cible [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] .

6. Dans la troisième page de l’Assistant, vous pouvez choisir d’ajouter des données de profilage d’interaction de couche (TIP), des données du code JavaScript s’exécutant dans les pages web ou les deux.

    - Pour collecter l’interaction de couche, cochez la case **Activer le profilage d’interaction de couche** .

    - Pour collecter des données du code JavaScript s’exécutant dans les pages web, cochez la case **Profiler JavaScript**.

7. Cliquez sur **Suivant**.

8. Dans la quatrième page de l’Assistant, cliquez sur **Terminer**.

9. Une session de performance est créée pour l’application ASP.NET et le site web est démarré dans le navigateur. Utilisez les fonctionnalités que vous voulez profiler, puis fermez le navigateur.

     Le profileur génère le fichier de données et affiche la vue Résumé des données dans la fenêtre principale de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="see-also"></a>Voir aussi

[Vues d’ensemble](../profiling/overviews-performance-tools.md)
[Configurer des sessions de performances](../profiling/configuring-performance-sessions.md)
[Comprendre le fonctionnement des valeurs de données d’instrumentation](../profiling/understanding-instrumentation-data-values.md)
[Comprendre le fonctionnement des valeurs de données d’échantillonnage](../profiling/understanding-sampling-data-values.md)
