---
title: "Serveur et la Configuration du client dans les déploiements ClickOnce | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications, ClickOnce
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- Windows applications, ClickOnce deployments
ms.assetid: 929e5fcc-dd56-409c-bb57-00bd9549b20b
caps.latest.revision: "33"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 4b7153b0a20c10e7dbdb31ac943f150f72cb39d8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>Problèmes de configuration de serveur et de client lors de déploiements ClickOnce
Si vous utilisez Internet Information Services (IIS) sur Windows Server et que votre déploiement contient un type de fichier Windows ne reconnaît pas, tel qu’un fichier Microsoft Word, IIS refusera de transmettre ce fichier et votre déploiement ne réussira pas.  
  
 En outre, certains serveurs Web et Web tels que les logiciels d’application, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], contiennent une liste de fichiers et les types que vous ne pouvez pas télécharger de fichiers. Par exemple, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] empêche le téléchargement de tous les fichiers Web.config. Ces fichiers peuvent contenir des informations sensibles telles que les noms d’utilisateur et mots de passe.  
  
 Bien que cette restriction ne pose aucun problème de téléchargement core [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] fichiers tels que les manifestes et les assemblys, cette restriction peut vous empêcher de télécharger des fichiers de données inclus dans le cadre de votre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application. Dans [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], vous pouvez résoudre cette erreur en supprimant le gestionnaire qui interdit le téléchargement de ces fichiers à partir du Gestionnaire de configuration IIS. Consultez la documentation du serveur IIS pour plus d’informations.  
  
 Certains serveurs Web peuvent bloquer les fichiers portant les extensions .dll, .config et .mdf. Les applications Windows incluent généralement les fichiers ayant certaines de ces extensions. Si un utilisateur tente d’exécuter un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application qui accède à un fichier bloqué sur un serveur Web, une erreur se produit. Plutôt que de débloquer toutes les extensions de fichier, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] publie chaque fichier d’application avec une extension de fichier « .deploy » par défaut. Par conséquent, l’administrateur doit uniquement configurer le serveur Web pour débloquer les trois extensions suivantes :  
  
-   .application  
  
-   .manifest  
  
-   .deploy  
  
 Toutefois, vous pouvez désactiver cette option en désactivant la **utiliser l’extension de fichier « .deploy »** option sur le [boîte de dialogue Options de publication](http://msdn.microsoft.com/en-us/fd9baa1b-7311-4f9e-8ffb-ae50cf110592), auquel cas vous devez configurer le serveur Web pour débloquer toutes les extensions de fichier utilisé dans l’application.  
  
 Vous devez configurer .manifest, .application et .deploy, par exemple, si vous utilisez IIS où vous n’avez pas installé le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], ou si vous utilisez un autre serveur Web (par exemple, Apache).  
  
## <a name="clickonce-and-secure-sockets-layer-ssl"></a>ClickOnce et Secure Sockets Layer (SSL)  
 A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application fonctionne correctement sur le protocole SSL, sauf lorsque Internet Explorer émet une invite de commandes sur le certificat SSL. L’invite de commandes peut être déclenché lorsqu’il existe un problème avec le certificat, par exemple lorsque les noms de sites ne correspondent pas ou le certificat a expiré. Pour rendre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] fonctionne sur une connexion SSL, assurez-vous que le certificat est à jour, et que les données du certificat correspond aux données du site.  
  
## <a name="clickonce-and-proxy-authentication"></a>ClickOnce et authentification Proxy  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]prend en charge l’authentification de proxy intégrée de Windows à partir de .NET Framework 3.5. Aucune directive machine.config spécifique n’est requis. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]ne fournit pas de prise en charge pour les autres protocoles d’authentification tels que Basic ou Digest.  
  
 Vous pouvez également appliquer un correctif pour .NET Framework 2.0 pour activer cette fonctionnalité. Pour plus d’informations, consultez http://go.microsoft.com/fwlink/?LinkId=158730.  
  
 Pour plus d’informations, consultez [ \<defaultProxy >, élément (paramètres réseau)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings).  
  
## <a name="clickonce-and-web-browser-compatibility"></a>ClickOnce et compatibilité du navigateur Web  
 Actuellement, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installations lancera uniquement si l’URL pour le manifeste de déploiement est ouverte à l’aide d’Internet Explorer. Un déploiement dont l’URL est lancé à partir d’une autre application, telles que Microsoft Office Outlook, sera lancé avec succès uniquement si Internet Explorer est configuré en tant que le navigateur Web par défaut.  
  
> [!NOTE]
>  Mozilla Firefox est pris en charge si le fournisseur de déploiement n’est pas vide ou l’extension de l’Assistant Microsoft .NET Framework est installée. Cette extension est empaquetée avec .NET Framework 3.5 SP1. Pour la prise en charge de l’application XBAP, le plug-in NPWPF est activé si nécessaire.  
  
## <a name="activating-clickonce-applications-through-browser-scripting"></a>Activation d’Applications ClickOnce via des scripts de navigateur  
 Si vous avez développé une page Web personnalisée qui lance un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application à l’aide d’Active Scripting, vous découvrirez peut-être que l’application n’est pas lancée sur certains ordinateurs. Internet Explorer contient un paramètre appelé **demander confirmation pour les téléchargements de fichier**, ce qui affecte ce comportement. Ce paramètre est disponible sur le **sécurité** onglet dans son **Options** menu qui affecte ce comportement. Il est appelé **demander confirmation pour les téléchargements de fichier**, et il est répertorié sous le **télécharge** catégorie. La propriété est définie **activer** par défaut pour les pages Web intranet et **désactiver** par défaut pour les pages Web d’Internet. Lorsque ce paramètre a la valeur **désactiver**, toute tentative d’activer un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application par programme (par exemple, en assignant son URL à la `document.location` propriété) sera bloquée. Dans ce cas, les utilisateurs peuvent lancer des applications uniquement par le biais d’un téléchargement initiée par l’utilisateur, par exemple, en cliquant sur un lien hypertexte correspondant à l’URL de l’application.  
  
## <a name="additional-server-configuration-issues"></a>Problèmes de Configuration de serveur supplémentaires  
  
##### <a name="administrator-permissions-required"></a>Autorisations d’administrateur requises  
 Si vous publiez avec HTTP, vous devez disposer des autorisations d’administrateur sur le serveur cible. IIS requiert ce niveau d’autorisations. Si vous ne publiez pas à l’aide de HTTP, vous avez besoin de l’autorisation écrire sur le chemin d’accès cible.  
  
##### <a name="server-authentication-issues"></a>Problèmes d’authentification serveur  
 Lorsque vous publiez sur un serveur distant qui « accès anonyme » est désactivée, vous recevrez l’avertissement suivant :  
  
```  
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."  
```  
  
> [!NOTE]
>  Vous pouvez utiliser l’authentification NTLM (NT stimulation-réponse) si le site demande des informations d’identification autres que vos informations d’identification par défaut et, dans la boîte de dialogue de sécurité, vous cliquez sur **OK** lorsque vous êtes invité si vous souhaitez enregistrer fourni informations d’identification pour les futures sessions. Toutefois, cette solution de contournement ne fonctionnera pas pour l’authentification de base.  
  
## <a name="using-third-party-web-servers"></a>À l’aide de serveurs Web de tiers  
 Si vous déployez un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application à partir d’un serveur Web autres qu’IIS, vous pouvez rencontrer un problème si le serveur retourne le type de contenu incorrect pour la clé [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] fichiers, tels que le manifeste de déploiement et manifeste d’application. Pour résoudre ce problème, consultez l’aide de votre serveur Web documentation sur la façon d’ajouter de nouveaux types de contenu sur le serveur et assurez-vous que tous les mappages extension nom de fichier répertorié dans le tableau suivant sont en place.  
  
|Extension de nom de fichier|Type de contenu|  
|-------------------------|------------------|  
|`.application`|`application/x-ms-application`|  
|`.manifest`|`application/x-ms-manifest`|  
|`.deploy`|`application/octet-stream`|  
|`.msu`|`application/octet-stream`|  
|`.msp`|`application/octet-stream`|  
  
## <a name="clickonce-and-mapped-drives"></a>ClickOnce et lecteurs mappés  
 Si vous utilisez Visual Studio pour publier une application ClickOnce, vous ne pouvez pas spécifier un lecteur mappé comme emplacement d’installation. Toutefois, vous pouvez modifier l’application ClickOnce à installer à partir d’un lecteur mappé à l’aide de l’éditeur (Mage.exe et MageUI.exe) et le Générateur de manifeste. Pour plus d’informations, consultez [Mage.exe (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) et [MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client).  
  
## <a name="ftp-protocol-not-supported-for-installing-applications"></a>Protocole FTP non pris en charge pour l’installation d’Applications  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]prend en charge l’installation d’applications à partir de n’importe quel serveur Web HTTP 1.1 ou le serveur de fichiers. FTP, le protocole de transfert de fichier, n’est pas prise en charge pour l’installation d’applications. Vous pouvez utiliser FTP pour publier des applications uniquement. Le tableau suivant récapitule ces différences :  
  
|Type d’URL|Description|  
|--------------|-----------------|  
|FTP : / /|Vous pouvez publier un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application à l’aide de ce protocole.|  
|http://|Vous pouvez installer un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application à l’aide de ce protocole.|  
|https://|Vous pouvez installer un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application à l’aide de ce protocole.|  
|file://|Vous pouvez installer un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application à l’aide de ce protocole.|  
  
## <a name="windows-xp-sp2-windows-firewall"></a>Windows XP SP2 : Pare-feu Windows  
 Par défaut, Windows XP Service Pack 2 Active le pare-feu Windows. Si vous développez votre application sur un ordinateur équipé de Windows XP est installé, vous êtes toujours en mesure de publier et d’exécuter [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applications à partir du serveur local qui exécute IIS. Toutefois, vous ne peut pas accéder à ce serveur qui exécute IIS à partir d’un autre ordinateur, sauf si vous ouvrez le pare-feu Windows. Pour obtenir des instructions sur la gestion du pare-feu Windows, consultez l’aide de Windows.  
  
## <a name="windows-server-enable-frontpage-server-extensions"></a>Windows Server : Activez les extensions serveur FrontPage  
 Les Extensions serveur FrontPage de Microsoft est requises pour publier des applications sur un serveur Web Windows qui utilise le protocole HTTP.  
  
 Par défaut, Windows Server n’a pas les Extensions serveur FrontPage sont installées. Si vous souhaitez utiliser [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour publier sur un serveur Web Windows Server qui utilise HTTP avec les Extensions serveur FrontPage, vous devez installer tout d’abord les Extensions serveur FrontPage. Vous pouvez effectuer l’installation à l’aide de l’outil d’administration gérer votre serveur dans Windows Server.  
  
## <a name="windows-server-locked-down-content-types"></a>Windows Server : Types de contenu verrouillé  
 IIS sur [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] verrouille tous les types de fichiers à l’exception de certains types de contenus connus (par exemple, .htm, .html, .txt et ainsi de suite). Pour activer le déploiement de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] les applications à l’aide de ce serveur, vous devez modifier les paramètres IIS pour autoriser le téléchargement des fichiers de type .application, .manifest et tout autre type de fichier personnalisé utilisé par votre application.  
  
 Si vous déployez à l’aide d’un serveur IIS, exécutez inetmgr.exe et ajoutez de nouveaux Types de fichier pour la page Web par défaut :  
  
-   Pour les extensions .application et .manifest, le type MIME doit être « application/x-ms-application. » Pour les autres types de fichier, le type MIME doit être « application/octet-stream ».  
  
-   Si vous créez un type MIME avec l’extension « * » et le type MIME « application/octet-stream », vous pourrez débloqué du type de fichier à télécharger les fichiers. (Toutefois, bloqué fichier types tels que .aspx et .asmx ne peut pas être téléchargés.)  
  
 Pour obtenir des instructions spécifiques sur la configuration des types MIME sur Windows Server, consultez l’article KB326965, de la Base de connaissances Microsoft « IIS 6.0 ne pas servir inconnu type MIME » sur le [http://support.microsoft.com/default.aspx?scid=kb;en-us;326965](http://support.microsoft.com/default.aspx?scid=kb;en-us;326965).  
  
## <a name="content-type-mappings"></a>Mappages de Type de contenu  
 Lors de la publication sur HTTP, le type de contenu (également connu sous le type MIME) pour le fichier .application doit être « application/x-ms-application. » Si vous avez [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] installé sur le serveur, il sera configuré pour vous automatiquement. Si ce n’est pas installé, vous devez créer une association de types MIME pour le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] la racine virtuelle de l’application (ou serveur entier).  
  
 Si vous déployez à l’aide d’un serveur IIS, exécutez inetmgr.exe et ajoutez un nouveau type de contenu de « application/x-ms-application » pour l’extension .application.  
  
## <a name="http-compression-issues"></a>Problèmes de Compression HTTP  
 Avec [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], vous pouvez effectuer des téléchargements qui utilisent la compression HTTP, une technologie de serveur Web qui utilise l’algorithme GZIP pour compresser un flux de données avant d’envoyer le flux de données au client. Le client, dans ce cas, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], décompresse le flux de données avant de lire les fichiers.  
  
 Si vous utilisez IIS, vous pouvez facilement activer la compression HTTP. Toutefois, lorsque vous activez la compression HTTP, elle est uniquement activée pour certains types de fichiers, à savoir, les fichiers texte et HTML. Pour activer la compression pour les assemblys (.dll), XML (.xml), les manifestes de déploiement (.application) et les manifestes d’application (.manifest), vous devez ajouter ces types de fichiers à la liste des types pour IIS doit compresser. Jusqu'à ce que vous ajoutez les types de fichiers à votre déploiement, texte et fichiers HTML seront compressés.  
  
 Pour obtenir des instructions détaillées pour IIS, consultez [comment spécifier des types de documents supplémentaires pour la compression HTTP](http://go.microsoft.com/fwlink/?LinkId=178459).  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage des déploiements ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)   
 [Choix d’une stratégie de déploiement ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Prérequis pour le déploiement d’applications](../deployment/application-deployment-prerequisites.md)