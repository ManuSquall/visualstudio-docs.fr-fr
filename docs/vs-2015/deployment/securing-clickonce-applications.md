---
title: Sécurisation des applications ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce security
- ClickOnce deployment, security
- deploying applications, ClickOnce security
ms.assetid: a05b5f2f-d1f2-471a-8096-8b11f7554265
caps.latest.revision: 47
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2a2610c1fef92bb77d150dad7972bb991b6ef4a4
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686008"
---
# <a name="securing-clickonce-applications"></a>Sécurisation des applications ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les applications[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] sont soumises aux contraintes de sécurité d'accès du code dans .NET Framework afin d'aider à limiter l'accès du code aux opérations et aux ressources protégées. Pour cette raison, il est important de comprendre les implications de la sécurité d'accès du code afin d'écrire vos applications [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] en conséquence. Vos applications peuvent utiliser des zones de confiance totale ou de confiance partielle, telles que les zones intranet et Internet, pour limiter l'accès.  
  
 En outre, ClickOnce utilise des certificats pour vérifier l'authenticité de l'éditeur de l'application, et pour signer les manifestes de déploiement et d'application permettant de prouver que les fichiers n'ont pas été falsifiés. La signature est une étape facultative, qui facilite la modification des fichiers d'application après que les manifestes ont été générés. Toutefois, sans manifestes signés, il est difficile de garantir que le programme d'installation de l'application n'a pas été falsifié lors d'attaques de l'intercepteur au niveau de la sécurité. Pour cette raison, nous vous recommandons de signer vos manifestes d'application et de déploiement pour aider à sécuriser vos applications.  
  
## <a name="zones"></a>Zones  
 Les applications déployées à l'aide de la technologie [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] sont restreintes à un jeu d'autorisations et d'actions défini par la zone de sécurité. Les zones de sécurité sont définies dans Internet Explorer et sont basées sur l'emplacement de l'application. Le tableau suivant répertorie les autorisations par défaut en fonction de l'emplacement de déploiement:  
  
|Emplacement de déploiement|Zone de sécurité|  
|-------------------------|-------------------|  
|Exécution à partir du Web|Zone Internet|  
|Installation à partir du Web|Zone Internet|  
|Installation à partir du partage de fichier réseau|Zone Intranet local|  
|Installation à partir du CD-ROM|Confiance totale|  
  
 Les autorisations par défaut prennent comme base l'emplacement à partir duquel la version originale de l'application a été déployée ; les mises à jour de l'application hériteront de ces autorisations. Si l'application est configurée pour vérifier les mises à jour à partir d'un emplacement Web ou réseau et qu'une version plus récente est disponible, l'installation d'origine peut recevoir des autorisations pour la zone Internet ou Intranet plutôt que des autorisations de confiance totale. Pour empêcher des utilisateurs d'être invités, un administrateur système peut spécifier une stratégie de déploiement ClickOnce qui définit un éditeur de l'application spécifique comme une source fiable. Pour les ordinateurs sur lesquels cette stratégie est déployée, les autorisations seront automatiquement accordées et l'invite ne sera pas présentée à l'utilisateur. Pour plus d'informations, consultez [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md). Pour configurer le déploiement d'applications approuvées, le certificat peut être installé au niveau de l'ordinateur ou au niveau de l'entreprise. Pour plus d'informations, voir [Procédure : Ajouter un éditeur approuvé à un ordinateur client pour les applications ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).  
  
## <a name="code-access-security-policies"></a>Stratégies de sécurité d'accès du code  
 Les autorisations d’une application sont déterminées par les paramètres figurant dans l’élément [\<trustInfo> Élément](../deployment/trustinfo-element-clickonce-application.md) du manifeste de l’application. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] génère automatiquement ces informations selon les paramètres figurant sur la page de propriété **Sécurité** du projet. Seules les autorisations spécifiques demandées par une application [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] lui sont accordées. Par exemple, à l'emplacement où l'accès au fichier requiert des autorisations de type Confiance totale, si l'application demande l'autorisation d'accès de fichier, seule l'autorisation d'accès de fichier, non les autorisations de type Confiance totale, lui sera accordée. Lors du développement de votre application [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , assurez-vous de ne demander que les autorisations spécifiques dont l'application a besoin. Dans la plupart des cas, vous pouvez utiliser les zones Internet ou intranet local pour limiter votre application à une confiance partielle. Pour plus d'informations, voir [Procédure : Définir une Zone de sécurité pour une Application ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md). Si votre application requiert des autorisations personnalisées, vous pouvez créer une zone personnalisée. Pour plus d'informations, voir [Procédure : Définir des autorisations personnalisées pour une Application ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
 L'inclusion d'une autorisation qui ne fait pas partie du jeu d'autorisations par défaut de la zone à partir de laquelle l'application est déployée amènerait l'utilisateur final à être invité à accorder l'autorisation au moment de l'installation ou de la mise à jour. Pour empêcher des utilisateurs d'être invités, un administrateur système peut spécifier une stratégie de déploiement ClickOnce qui définit un éditeur de l'application spécifique comme une source fiable. Sur les ordinateurs sur lesquels cette stratégie est déployée, les autorisations seront automatiquement accordées et l'invite ne sera pas présentée à l'utilisateur.  
  
 En tant que développeur, vous devez garantir que votre application s'exécutera avec les autorisations appropriées. Si l'application demande des autorisations en dehors d'une zone au moment de l'exécution, une exception de sécurité peut s'afficher. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vous permet de déboguer votre application dans la zone de sécurité cible. et vous aide à développer des applications sécurisées. Pour plus d'informations, voir [Procédure : Déboguer une application ClickOnce avec des autorisations restreintes](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md).  
  
 Pour plus d’informations sur la sécurité d’accès du code et sur ClickOnce, consultez [Code Access Security for ClickOnce Applications](../deployment/code-access-security-for-clickonce-applications.md).  
  
## <a name="code-signing-certificates"></a>Certificats de signature de code  
 Pour publier une application à l'aide du déploiement [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , vous pouvez signer les manifestes d'application et de déploiement de l'application en utilisant une paire de clés publique/privée. Les outils utilisés pour la signature d'un manifeste sont disponibles sur la page **Signature** du **Concepteur de projets**. Pour plus d'informations, consultez [Signing Page, Project Designer](../ide/reference/signing-page-project-designer.md). Vous pouvez également signer les manifestes avec un fichier de clé pendant le processus de publication, à l’aide de l’Assistant Publication.  
  
 Une fois les manifestes signés, les informations sur l'éditeur qui prennent comme base la signature Authenticode seront affichées pour l'utilisateur dans la boîte de dialogue d'autorisations lors de l'installation, afin de signaler à l'utilisateur que l'application provient d'une source fiable.  
  
 Pour plus d’informations sur ClickOnce et sur les certificats, consultez [ClickOnce and Authenticode](../deployment/clickonce-and-authenticode.md).  
  
## <a name="aspnet-form-based-authentication"></a>Authentification basée sur les formulaires ASP.NET  
 Si vous souhaitez contrôler les déploiements auxquels chaque utilisateur peut accéder, vous ne devez pas autoriser un accès anonyme aux applications [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] déployées sur un serveur Web. Vous devriez plutôt autoriser les utilisateurs à accéder aux déploiements que vous avez installés selon l'identité d'un utilisateur à l'aide de l'authentification Windows.  
  
 Toutefois,[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ne prend pas en charge l'authentification basée sur les formulaires ASP.NET, car il utilise des cookies persistants ; ceux-ci présentent un problème de sécurité parce qu'ils résident dans le cache Internet Explorer et peuvent être piratés. Par conséquent, si vous déployez des applications [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , tout scénario d'authentification en plus de l'authentification Windows n'est pas pris en charge.  
  
## <a name="passing-arguments"></a>Passage d'arguments  
 Une considération supplémentaire en matière de sécurité doit être prise en compte si vous devez passer des arguments dans une application [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] permet aux développeurs de fournir une chaîne de requête aux applications déployées sur le Web. La chaîne de requête prend la forme d'une série de paires nom-valeur à la fin de l'URL utilisée pour lancer l'application :  
  
 `http://servername.adatum.com/WindowsApp1.application?username=joeuser`  
  
 Les arguments de chaîne de requête sont désactivés par défaut. Pour les activer, l'attribut `trustUrlParameters` doit être défini dans le manifeste de déploiement de l'application. Cette valeur peut être définie à partir de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] et de MageUI.exe. Pour obtenir des instructions détaillées sur l’activation du passage de chaînes de requête, consultez [Comment : Récupérer les informations de chaîne de requête dans une application ClickOnce en ligne](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).  
  
 Vous ne devez jamais passer d'arguments récupérés via une chaîne de requête directement à une base de données ou à la ligne de commande sans les vérifier et vous assurer qu'ils sont sécurisés. Les arguments non sécurisés sont ceux qui incluent des caractères d'échappement de la base de données ou de la ligne de commande pouvant permettre à un utilisateur malveillant de manipuler votre application et de lui faire exécuter des commandes arbitraires.  
  
> [!NOTE]
> Les arguments de chaîne de requête constituent la seule manière de passer des arguments à une application [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] lors du lancement. Vous ne pouvez pas passer d'arguments à une application [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] à partir de la ligne de commande.  
  
## <a name="deploying-obfuscated-assemblies"></a>Déploiement d'assemblys obscurcis  
 Vous pouvez être amené à obscurcir votre application à l'aide de Dotfuscator pour empêcher d'autres utilisateurs d'effectuer une ingénierie à rebours du code. Toutefois, l'obscurcissement d'assembly n'est pas intégré dans l'IDE de Visual Studio ou le processus de déploiement ClickOnce. Par conséquent, vous devrez exécuter l'obscurcissement en dehors du processus de déploiement, éventuellement à l'aide d'une étape post-build. Après avoir généré le projet, vous pourrez exécuter manuellement les étapes suivantes, en dehors de Visual Studio :  
  
1. Exécutez l'obscurcissement à l'aide de Dotfuscator.  
  
2. Utilisez Mage.exe ou MageUI.exe pour générer et signer les manifestes ClickOnce. Pour plus d’informations, consultez [Mage.exe (Manifest Generation and Editing Tool)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1) et [MageUI.exe (outil Manifest Generation and Editing, client graphique)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14).  
  
3. Publiez (copiez) manuellement les fichiers sur votre emplacement source de déploiement (serveur Web, partage UNC ou CD-ROM).  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Choix d’une stratégie de déploiement ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
