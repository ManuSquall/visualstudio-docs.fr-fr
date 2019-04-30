---
title: Serveur et les problèmes de Configuration de Client dans les déploiements ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 90772785297b84a12cc98d6ce21a2cd2e65743f9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444972"
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>Problèmes de configuration de serveur et de client lors de déploiements ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si vous utilisez Internet Information Services (IIS) sur Windows Server, et que votre déploiement contient un type de fichier Windows ne reconnaît pas, tel qu’un fichier Microsoft Word, IIS refusera de transmettre ce fichier, et votre déploiement ne réussira pas.  
  
 En outre, certains serveurs Web et Web tels que les logiciels d’application, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], contiennent une liste de fichiers et les types que vous ne pouvez pas télécharger de fichiers. Par exemple, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] empêche le téléchargement de tous les fichiers Web.config. Ces fichiers peuvent contenir des informations sensibles telles que les noms d’utilisateur et mots de passe.  
  
 Bien que cette restriction ne pose aucun problème pour le téléchargement core [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] fichiers tels que les manifestes et les assemblys, cette restriction peut vous empêcher de télécharger des fichiers de données inclus dans le cadre de votre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application. Dans [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], vous pouvez résoudre cette erreur en supprimant le gestionnaire qui interdit le téléchargement de ces fichiers à partir du Gestionnaire de configuration IIS. Consultez la documentation du serveur IIS pour plus d’informations.  
  
 Certains serveurs Web peuvent bloquer des fichiers portant les extensions .dll, .config et .mdf. Applications basées sur Windows incluent généralement des fichiers avec certaines de ces extensions. Si un utilisateur tente d’exécuter un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application qui accède à un fichier bloqué sur un serveur Web, une erreur se produit. Plutôt que de débloquer toutes les extensions de fichier, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] publie chaque fichier d’application avec une extension de fichier « .deploy » par défaut. Par conséquent, l’administrateur doit uniquement configurer le serveur Web pour débloquer les trois extensions suivantes :  
  
- .application  
  
- .manifest  
  
- .deploy  
  
  Toutefois, vous pouvez désactiver cette option en désactivant le **utiliser l’extension de fichier « .deploy »** option sur le [Publish Options Dialog Box](http://msdn.microsoft.com/fd9baa1b-7311-4f9e-8ffb-ae50cf110592), auquel cas vous devez configurer le serveur Web pour débloquer toutes les extensions de fichier utilisé dans l’application.  
  
  Vous devrez configurer .manifest, .application et .deploy, par exemple, si vous utilisez IIS où vous n’avez pas installé le [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], ou si vous utilisez un autre serveur Web (par exemple, Apache).  
  
## <a name="clickonce-and-secure-sockets-layer-ssl"></a>ClickOnce et Secure Sockets Layer (SSL)  
 Un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application fonctionne correctement avec le protocole SSL, sauf lorsque Internet Explorer émet une invite sur le certificat SSL. L’invite peut être déclenchée lorsqu’il existe un problème avec le certificat, par exemple lorsque les noms de site ne correspondent pas ou le certificat a expiré. Pour rendre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] fonctionne sur une connexion SSL, assurez-vous que le certificat est à jour, et que les données du certificat correspond aux données du site.  
  
## <a name="clickonce-and-proxy-authentication"></a>ClickOnce et l’authentification du Proxy  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] prend en charge pour l’authentification proxy intégrée de Windows à compter de .NET Framework 3.5. Aucune directive machine.config spécifique n’est requis. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ne fournit pas de prise en charge pour d’autres protocoles d’authentification tels que Basic ou Digest.  
  
 Vous pouvez également appliquer un correctif pour .NET Framework 2.0 pour activer cette fonctionnalité. Pour plus d'informations, consultez http://go.microsoft.com/fwlink/?LinkId=158730.  
  
 Pour plus d’informations, consultez [ \<defaultProxy >, élément (paramètres réseau)](http://msdn.microsoft.com/library/9d663c4b-07b4-4f6f-9b12-efbd3630354f).  
  
## <a name="clickonce-and-web-browser-compatibility"></a>ClickOnce et compatibilité du navigateur Web  
 Actuellement, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] installations seront lancée seulement si l’URL pour le manifeste de déploiement est ouverte à l’aide d’Internet Explorer. Un déploiement dont l’URL est lancée à partir d’une autre application, comme Microsoft Office Outlook, sera lancé avec succès uniquement si Internet Explorer est défini en tant que le navigateur Web par défaut.  
  
> [!NOTE]
> Mozilla Firefox est pris en charge si le fournisseur de déploiement n’est pas vide ou l’extension Assistant Microsoft .NET Framework est installée. Cette extension est empaquetée avec .NET Framework 3.5 SP1. Pour la prise en charge de l’application XBAP, le plug-in NPWPF est activé si nécessaire.  
  
## <a name="activating-clickonce-applications-through-browser-scripting"></a>Activation d’Applications ClickOnce via des scripts de navigateur  
 Si vous avez développé une page Web personnalisée qui lance un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application à l’aide d’Active Scripting, vous trouverez peut-être que l’application n’est pas lancée sur certains ordinateurs. Internet Explorer contient un paramètre appelé **demander confirmation pour les téléchargements de fichier**, ce qui affecte ce comportement. Ce paramètre est disponible sur le **sécurité** onglet dans son **Options** menu qui affecte ce comportement. Il est appelé **demander confirmation pour les téléchargements de fichier**, et il est répertorié sous le **télécharge** catégorie. La propriété est définie sur **activer** par défaut pour les pages Web intranet et à **désactiver** par défaut pour les pages Web d’Internet. Lorsque ce paramètre est défini sur **désactiver**, toute tentative d’activer un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application par programmation (par exemple, en assignant son URL à la `document.location` propriété) seront bloqués. Dans ce cas, les utilisateurs peuvent lancer des applications uniquement par le biais d’un téléchargement initiée par l’utilisateur, par exemple, en cliquant sur un lien hypertexte correspondant à l’URL de l’application.  
  
## <a name="additional-server-configuration-issues"></a>Problèmes de Configuration de serveur supplémentaire  
  
##### <a name="administrator-permissions-required"></a>Autorisations d’administrateur requises  
 Vous devez disposer des autorisations d’administrateur sur le serveur cible si vous publiez avec HTTP. IIS requiert ce niveau d’autorisations. Si vous ne publiez pas à l’aide de HTTP, vous avez besoin de l’autorisation écrire sur le chemin d’accès cible.  
  
##### <a name="server-authentication-issues"></a>Problèmes d’authentification serveur  
 Lorsque vous publiez sur un serveur distant qui « accès anonyme » est désactivée, vous recevrez l’avertissement suivant :  
  
```  
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."  
```  
  
> [!NOTE]
> Vous pouvez utiliser l’authentification NTLM (NT stimulation-réponse) si le site demande des informations d’identification autres que vos informations d’identification par défaut, puis, dans la boîte de dialogue de sécurité, vous cliquez sur **OK** lorsque vous y êtes invité si vous souhaitez enregistrer fourni informations d’identification pour les sessions ultérieures. Toutefois, cette solution de contournement ne fonctionne pas pour l’authentification de base.  
  
## <a name="using-third-party-web-servers"></a>À l’aide de serveurs Web de tiers  
 Si vous déployez un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application à partir d’un serveur Web autres qu’IIS, vous pouvez rencontrer un problème si le serveur retourne le type de contenu incorrect pour la clé [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] fichiers, tels que le manifeste de déploiement et le manifeste d’application. Pour résoudre ce problème, consultez l’aide de votre serveur Web documentation sur la façon d’ajouter de nouveaux types de contenu sur le serveur et vérifiez que tous les mappages d’extension nom fichier répertorié dans le tableau suivant sont en place.  
  
|Extension de nom de fichier|Type de contenu|  
|-------------------------|------------------|  
|`.application`|`application/x-ms-application`|  
|`.manifest`|`application/x-ms-manifest`|  
|`.deploy`|`application/octet-stream`|  
|`.msu`|`application/octet-stream`|  
|`.msp`|`application/octet-stream`|  
  
## <a name="clickonce-and-mapped-drives"></a>ClickOnce et lecteurs mappés  
 Si vous utilisez Visual Studio pour publier une application ClickOnce, vous ne pouvez pas spécifier un lecteur mappé comme emplacement d’installation. Toutefois, vous pouvez modifier l’application ClickOnce pour installer à partir d’un lecteur mappé à l’aide de l’éditeur (Mage.exe et MageUI.exe) et le Générateur de manifeste. Pour plus d’informations, consultez [Mage.exe (Manifest Generation and Editing Tool)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1) et [MageUI.exe (outil Manifest Generation and Editing, client graphique)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14).  
  
## <a name="ftp-protocol-not-supported-for-installing-applications"></a>Protocole FTP non pris en charge pour l’installation d’Applications  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] prend en charge l’installation d’applications à partir de n’importe quel serveur Web HTTP 1.1 ou le serveur de fichiers. FTP, File Transfer Protocol, n’est pas pris en charge pour l’installation d’applications. Vous pouvez utiliser FTP pour publier des applications uniquement. Le tableau suivant récapitule ces différences :  
  
|Type d’URL|Description|  
|--------------|-----------------|  
|ftp://|Vous pouvez publier un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application à l’aide de ce protocole.|  
|http://|Vous pouvez installer un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application à l’aide de ce protocole.|  
|https://|Vous pouvez installer un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application à l’aide de ce protocole.|  
|file://|Vous pouvez installer un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application à l’aide de ce protocole.|  
  
## <a name="windows-xp-sp2-windows-firewall"></a>Windows XP SP2 : Pare-feu Windows  
 Par défaut, Windows XP Service Pack 2 Active le pare-feu Windows. Si vous développez votre application sur un ordinateur Windows XP est installé, vous êtes toujours en mesure de publier et exécuter [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applications à partir du serveur local qui exécute IIS. Toutefois, vous ne peut pas accéder à ce serveur qui exécute IIS à partir d’un autre ordinateur, sauf si vous ouvrez le pare-feu Windows. Pour obtenir des instructions sur la gestion du pare-feu Windows, consultez l’aide de Windows.  
  
## <a name="windows-server-enable-frontpage-server-extensions"></a>Windows Server : Activer les extensions serveur FrontPage  
 Les Extensions serveur FrontPage de Microsoft est requises pour la publication d’applications sur un serveur Web de Windows qui utilise le protocole HTTP.  
  
 Par défaut, Windows Server n’a pas les Extensions serveur FrontPage sont installées. Si vous souhaitez utiliser [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour publier sur un serveur Web Windows Server qui utilise le protocole HTTP avec les Extensions serveur FrontPage, vous devez installer tout d’abord les Extensions serveur FrontPage. Vous pouvez effectuer l’installation à l’aide de l’outil d’administration gérer votre serveur dans Windows Server.  
  
## <a name="windows-server-locked-down-content-types"></a>Windows Server : Types de contenu verrouillée  
 IIS sur [!INCLUDE[WinXPSvr](../includes/winxpsvr-md.md)] verrouille tous les types de fichiers à l’exception de certains types de contenu connus (par exemple, .htm, .html, .txt, etc.). Pour activer le déploiement de [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applications à l’aide de ce serveur, vous devez modifier les paramètres IIS pour autoriser le téléchargement de fichiers de type .application, .manifest et tout autre type de fichier personnalisé utilisé par votre application.  
  
 Si vous déployez à l’aide d’un serveur IIS, exécutez inetmgr.exe et ajouter de nouveaux Types de fichier pour la page Web par défaut :  
  
- Pour les extensions .application et .manifest, le type MIME doit être « application/x-ms-application. » Pour les autres types de fichier, le type MIME doit être « application/octet-stream ».  
  
- Si vous créez un type MIME avec l’extension « * » et le type MIME « application/octet-stream », il autorisera débloqué du type de fichier à télécharger. (Toutefois, bloqué fichier types tels que .aspx et .asmx ne peut pas être téléchargés.)  
  
  Pour obtenir des instructions spécifiques sur la configuration des types MIME sur Windows Server, consultez l’article KB326965, de la Base de connaissances Microsoft « IIS 6.0 ne pas répondre MIME type inconnu » sur le [ http://support.microsoft.com/default.aspx?scid=kb; en-us ; 326965](http://support.microsoft.com/default.aspx?scid=kb;en-us;326965).  
  
## <a name="content-type-mappings"></a>Mappages de Type de contenu  
 Lors de la publication via HTTP, le type de contenu (également connu sous le type MIME) pour le fichier .application doit être « application/x-ms-application. » Si vous avez [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] installé sur le serveur, il sera configuré pour vous automatiquement. Si ce n’est pas installé, vous devez créer une association de types MIME pour le [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] vroot application (ou serveur entier).  
  
 Si vous déployez à l’aide d’un serveur IIS, exécutez inetmgr.exe et ajoutez un nouveau type de contenu de « application/x-ms-application » pour l’extension .application.  
  
## <a name="http-compression-issues"></a>Problèmes de Compression HTTP  
 Avec [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], vous pouvez effectuer des téléchargements qui utilisent la compression HTTP, une technologie de serveur Web qui utilise l’algorithme GZIP pour compresser un flux de données avant d’envoyer le flux de données au client. Le client — dans ce cas, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], décompresse le flux de données avant de lire les fichiers.  
  
 Si vous utilisez IIS, vous pouvez facilement activer la compression HTTP. Toutefois, lorsque vous activez la compression HTTP, il est uniquement activé pour certains types de fichiers — à savoir, les fichiers texte et HTML. Pour activer la compression pour les assemblys (.dll), XML (.xml), les manifestes de déploiement (.application) et les manifestes d’application (.manifest), vous devez ajouter ces types de fichiers à la liste des types pour IIS doit compresser. Jusqu'à ce que vous ajoutez les types de fichiers à votre déploiement, texte et les fichiers HTML seront compressés.  
  
 Pour obtenir des instructions détaillées pour IIS, consultez [comment spécifier les types de documents supplémentaires pour la compression HTTP](http://go.microsoft.com/fwlink/?LinkId=178459).  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage des déploiements ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)   
 [Choix d’une stratégie de déploiement ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Prérequis pour le déploiement d’applications](../deployment/application-deployment-prerequisites.md)
