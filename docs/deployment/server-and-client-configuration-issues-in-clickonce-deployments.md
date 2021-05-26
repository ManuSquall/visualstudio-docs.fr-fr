---
title: Problèmes de configuration du serveur/du client (ClickOnce)
description: En savoir plus sur les problèmes de configuration du serveur et du client qui peuvent affecter le déploiement de votre application ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8040fb8028666d0dd551369b6b7f782de09058ca
ms.sourcegitcommit: 18e7300d4878f2fcd0263a4aff31a755ae8fc289
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/25/2021
ms.locfileid: "110449940"
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>Problèmes de configuration de serveur et de client dans les déploiements ClickOnce
Si vous utilisez Internet Information Services (IIS) sur Windows Server et que votre déploiement contient un type de fichier que Windows ne reconnaît pas, tel qu’un fichier Microsoft Word, IIS refusera de transmettre ce fichier, et votre déploiement échouera.

 En outre, certains serveurs Web et logiciels d’application Web, tels que [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] , contiennent une liste de fichiers et de types de fichiers que vous ne pouvez pas télécharger. Par exemple, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] empêche le téléchargement de tous les fichiers de *Web.config* . Ces fichiers peuvent contenir des informations sensibles telles que des noms d’utilisateur et des mots de passe.

 Bien que cette restriction ne soit pas à l’origine de problèmes de téléchargement des fichiers de base [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tels que les manifestes et les assemblys, cette restriction peut vous empêcher de télécharger les fichiers de données inclus dans votre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application. Dans [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] , vous pouvez résoudre cette erreur en supprimant le gestionnaire qui interdit le téléchargement de tels fichiers à partir du gestionnaire de configuration IIS. Pour plus d’informations, consultez la documentation du serveur IIS.

 Certains serveurs Web peuvent bloquer des fichiers avec des extensions telles que *. dll*, *. config* et *. mdf*. Les applications Windows incluent généralement des fichiers avec certaines de ces extensions. Si un utilisateur tente d’exécuter une [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application qui accède à un fichier bloqué sur un serveur Web, une erreur se produit. Au lieu de débloquer toutes les extensions de fichier, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] publie chaque fichier d’application avec une extension de fichier *. deploy* par défaut. Par conséquent, l’administrateur a uniquement besoin de configurer le serveur Web pour débloquer les trois extensions de fichier suivantes :

- *. application*

- *. manifest*

- *. déployer*

  Toutefois, vous pouvez désactiver cette option en désactivant l’option **utiliser l’extension de fichier « . deploy »** dans la [boîte de dialogue Options de publication](/previous-versions/visualstudio/visual-studio-2010/7z83t16a(v=vs.100)). dans ce cas, vous devez configurer le serveur Web pour débloquer toutes les extensions de fichier utilisées dans l’application.

  Vous devrez configurer *. manifest*, *. application* et *. deploy*, par exemple, si vous utilisez IIS où vous n’avez pas installé le .NET Framework ou si vous utilisez un autre serveur Web (par exemple, Apache).

## <a name="clickonce-and-secure-sockets-layer-ssl"></a>ClickOnce et SSL (Secure Sockets Layer) (SSL)
 Une [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application fonctionnera correctement avec SSL, sauf quand Internet Explorer émet une invite sur le certificat SSL. L’invite peut être déclenchée en cas de problème avec le certificat, par exemple lorsque les noms de site ne correspondent pas ou que le certificat a expiré. Pour effectuer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] un travail sur une connexion SSL, assurez-vous que le certificat est à jour et que les données du certificat correspondent aux données du site.

## <a name="clickonce-and-proxy-authentication"></a>Authentification ClickOnce et proxy
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] fournit la prise en charge de l’authentification Windows intégrée du proxy à partir de .NET Framework 3,5. Aucune directive de machine.config spécifique n’est requise. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ne prend pas en charge d’autres protocoles d’authentification tels que Basic ou Digest.

 Vous pouvez également appliquer un correctif à .NET Framework 2,0 pour activer cette fonctionnalité. Pour plus d’informations, consultez [corriger : message d’erreur lorsque vous essayez d’installer une application ClickOnce que vous avez créée dans le .NET Framework 2,0 sur un ordinateur client qui est configuré pour utiliser un serveur proxy : « authentification proxy requise »](https://support.microsoft.com/help/917952/fix-error-message-when-you-try-to-install-a-clickonce-application-that).

 Pour plus d’informations, consultez [ \<defaultProxy> élément (paramètres réseau)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings).

## <a name="clickonce-and-web-browser-compatibility"></a>ClickOnce et compatibilité des navigateurs Web
 Actuellement, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] les installations sont lancées uniquement si l’URL du manifeste de déploiement est ouverte à l’aide d’Internet Explorer. Un déploiement dont l’URL est lancée à partir d’une autre application, par exemple Microsoft Office Outlook, est lancé avec succès uniquement si Internet Explorer est défini comme navigateur Web par défaut.

> [!NOTE]
> Mozilla Firefox est pris en charge si le fournisseur de déploiement n’est pas vide ou si l’extension de l’Assistant Microsoft .NET Framework est installée. Cette extension est fournie avec .NET Framework 3,5 SP1. Pour la prise en charge de XBAP, le plug-in NPWPF est activé si nécessaire.

## <a name="activate-clickonce-applications-through-browser-scripting"></a>Activer des applications ClickOnce par le biais de scripts de navigateur
 Si vous avez développé une page Web personnalisée qui lance une [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application à l’aide d’Active Scripting, vous pouvez constater que l’application ne démarre pas sur certains ordinateurs. Internet Explorer contient un paramètre appelé **invite automatique pour les téléchargements de fichiers**, ce qui affecte ce comportement. Ce paramètre est disponible sous l’onglet **sécurité** dans le menu **options** qui affecte ce comportement. Elle est appelée « **invite automatique » pour les téléchargements de fichiers** et elle apparaît sous la catégorie **téléchargements** . La propriété est définie sur **activer** par défaut pour les pages Web intranet et pour **Désactiver** par défaut pour les pages Web Internet. Lorsque ce paramètre est défini sur **Disable**, toute tentative d’activation d’une [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application par programme (par exemple, en affectant son URL à la `document.location` propriété) est bloquée. Dans ce cas, les utilisateurs peuvent lancer des applications uniquement par le biais d’un téléchargement initié par l’utilisateur, par exemple, en cliquant sur un lien hypertexte défini sur l’URL de l’application.

## <a name="additional-server-configuration-issues"></a>Autres problèmes de configuration de serveur

##### <a name="administrator-permissions-required"></a>Autorisations d’administrateur requises
 Vous devez disposer d’autorisations d’administrateur sur le serveur cible si vous publiez avec HTTP. IIS requiert ce niveau d’autorisation. Si vous n’effectuez pas de publication à l’aide du protocole HTTP, vous n’avez besoin que d’une autorisation en écriture sur le chemin d’accès cible.

##### <a name="server-authentication-issues"></a>Problèmes d’authentification du serveur
 Lorsque vous publiez sur un serveur distant pour lequel l’option « accès anonyme » est désactivée, vous recevez l’avertissement suivant :

```
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."
```

> [!NOTE]
> Vous pouvez faire en sorte que l’authentification NTLM (stimulation/réponse NT) fonctionne si le site demande des informations d’identification autres que celles par défaut, et que, dans la boîte de dialogue sécurité, vous cliquez sur **OK** lorsque vous êtes invité à enregistrer les informations d’identification fournies pour les sessions ultérieures. Toutefois, cette solution ne fonctionne pas pour l’authentification de base.

## <a name="use-third-party-web-servers"></a>Utiliser des serveurs Web tiers
 Si vous déployez une [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application à partir d’un serveur Web autre qu’IIS, vous pouvez rencontrer un problème si le serveur retourne le type de contenu incorrect pour les fichiers de clés [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , tels que le manifeste de déploiement et le manifeste d’application. Pour résoudre ce problème, consultez la documentation d’aide de votre serveur Web sur la façon d’ajouter de nouveaux types de contenu au serveur et assurez-vous que tous les mappages d’extension de nom de fichier répertoriés dans le tableau suivant sont en place.

|Extension de nom de fichier|Type de contenu|
|-------------------------|------------------|
|`.application`|`application/x-ms-application`|
|`.manifest`|`application/x-ms-manifest`|
|`.deploy`|`application/octet-stream`|
|`.msu`|`application/octet-stream`|
|`.msp`|`application/octet-stream`|

## <a name="clickonce-and-mapped-drives"></a>ClickOnce et lecteurs mappés
 Si vous utilisez Visual Studio pour publier une application ClickOnce, vous ne pouvez pas spécifier un lecteur mappé comme emplacement d’installation. Toutefois, vous pouvez modifier l’application ClickOnce pour l’installer à partir d’un lecteur mappé à l’aide du générateur et de l’éditeur de manifeste (Mage.exe et MageUI.exe). Pour plus d’informations, consultez [Mage.exe (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) et [MageUI.exe (outil Manifest Generation and Editing, client graphique)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client).

## <a name="ftp-protocol-not-supported-for-installing-applications"></a>Protocole FTP non pris en charge pour l’installation d’applications
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] prend en charge l’installation d’applications à partir de n’importe quel serveur Web ou serveur de fichiers HTTP 1,1. FTP, le protocole FTP n’est pas pris en charge pour l’installation d’applications. Vous pouvez utiliser FTP pour publier des applications uniquement. Le tableau suivant résume ces différences :

| Type d’URL | Description |
|----------| - |
| ftp:// | Vous pouvez publier une [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application à l’aide de ce protocole. |
| http:// | Vous pouvez installer une [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application à l’aide de ce protocole. |
| https:// | Vous pouvez installer une [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application à l’aide de ce protocole. |
| file:// | Vous pouvez installer une [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application à l’aide de ce protocole. |

## <a name="windows-xp-sp2-windows-firewall"></a>Windows XP SP2 : pare-feu Windows
 Par défaut, Windows XP SP2 active le pare-feu Windows. Si vous développez votre application sur un ordinateur sur lequel Windows XP est installé, vous pouvez toujours publier et exécuter [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] des applications à partir du serveur local qui exécute IIS. Toutefois, vous ne pouvez pas accéder à ce serveur qui exécute IIS à partir d’un autre ordinateur, sauf si vous ouvrez le pare-feu Windows. Consultez l’aide de Windows pour obtenir des instructions sur la gestion du pare-feu Windows.

## <a name="windows-server-enable-frontpage-server-extensions"></a>Windows Server : activer les extensions serveur FrontPage
 FrontPage Server Extensions de Microsoft est requis pour la publication d’applications sur un serveur Web Windows qui utilise le protocole HTTP.

 Par défaut, FrontPage Server Extensions n’est pas installé sur Windows Server. Si vous souhaitez utiliser [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour publier sur un serveur Web Windows Server qui utilise le protocole http avec FrontPage Server Extensions, vous devez d’abord installer FrontPage Server Extensions. Vous pouvez effectuer l’installation à l’aide de l’outil gérer votre administration de serveur dans Windows Server.

## <a name="windows-server-locked-down-content-types"></a>Windows Server : types de contenu verrouillés
 IIS sur [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] verrouille tous les types de fichiers, à l’exception de certains types de contenu connus (par exemple, *. htm*, *. html*, *. txt*, etc.). Pour permettre le déploiement d' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applications à l’aide de ce serveur, vous devez modifier les paramètres IIS pour autoriser le téléchargement de fichiers de type *. application*, *. manifest* et tout autre type de fichier personnalisé utilisé par votre application.

 Si vous déployez à l’aide d’un serveur IIS, exécutez *inetmgr.exe* et ajoutez de nouveaux types de fichiers pour la page Web par défaut :

- Pour les extensions *. application* et *. manifest* , le type MIME doit être « application/x-ms-application ». Pour les autres types de fichier, le type MIME doit être « application/octet-stream ».

- Si vous créez un type MIME avec l’extension « \<em> » et le type MIME « application/octet-stream », les fichiers du type de fichier non bloqué sont autorisés à être téléchargés. (Toutefois, les types de fichiers bloqués, tels que *\* . aspx* et *\* . asmx* , ne peuvent pas être téléchargés.)

  Pour obtenir des instructions spécifiques sur la configuration des types MIME sur Windows Server, consultez [comment ajouter un type MIME à un site Web ou une application](/iis/configuration/system.webserver/staticcontent/mimemap#how-to-add-a-mime-type-to-a-web-site-or-application).

## <a name="content-type-mappings"></a>Mappages de types de contenu
 Lors de la publication sur HTTP, le type de contenu (également appelé type MIME) du fichier *. application* doit être « application/x-ms-application ». Si vous avez .NET Framework 2,0 installé sur le serveur, cette opération sera automatiquement définie. Si ce n’est pas le cas, vous devez créer une association de type MIME pour l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application vroot (ou le serveur entier).

 Si vous déployez à l’aide d’un serveur IIS, exécutez <em>inetmgr.</em> exe et ajoutez un nouveau type de contenu « application/x-ms-application » pour l’extension *. application* .

## <a name="http-compression-issues"></a>Problèmes de compression HTTP
 Avec [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , vous pouvez effectuer des téléchargements qui utilisent la compression http, une technologie de serveur Web qui utilise l’algorithme gzip pour compresser un flux de données avant d’envoyer le flux au client. Le client (dans ce cas, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ) décompresse le flux avant de lire les fichiers.

 Si vous utilisez IIS, vous pouvez facilement activer la compression HTTP. Toutefois, lorsque vous activez la compression HTTP, elle est activée uniquement pour certains types de fichiers, à savoir les fichiers HTML et texte. Pour activer la compression pour les assemblys (.*dll*), XML (.*XML*), les manifestes de déploiement (*. application*) et les manifestes d’application (*. manifest*), vous devez ajouter ces types de fichiers à la liste de types à compresser pour IIS. Tant que vous n’ajoutez pas les types de fichiers à votre déploiement, seuls les fichiers texte et HTML sont compressés.

 Pour obtenir des instructions détaillées sur les services Internet (IIS), consultez [comment spécifier des types de documents supplémentaires pour la compression http](/troubleshoot/iis/content-types-http-compression.md).

## <a name="see-also"></a>Voir aussi
- [Dépanner des déploiements ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
- [Choisir une stratégie de déploiement ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
- [Prérequis pour le déploiement d’applications](../deployment/application-deployment-prerequisites.md)
