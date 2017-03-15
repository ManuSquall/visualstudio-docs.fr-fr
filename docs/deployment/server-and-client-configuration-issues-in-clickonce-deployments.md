---
title: "Server and Client Configuration Issues in ClickOnce Deployments | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "deploying applications, ClickOnce"
  - "troubleshooting ClickOnce deployments"
  - "ClickOnce deployment, troubleshooting"
  - "Windows applications, ClickOnce deployments"
ms.assetid: 929e5fcc-dd56-409c-bb57-00bd9549b20b
caps.latest.revision: 33
caps.handback.revision: 33
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Server and Client Configuration Issues in ClickOnce Deployments
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si vous utilisez des services \(IIS\) sur Windows Server et que votre déploiement contient un type de fichier que Windows ne reconnaît pas, tel qu'un fichier Microsoft Word, IIS refusera de transmettre ce fichier et votre déploiement ne réussira pas.  
  
 En outre, certains serveurs Web et logiciels d'application Web, tels que [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], contiennent une liste de fichiers et de types de fichier que vous ne pouvez pas télécharger.  Par exemple, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] empêche le téléchargement de tous les fichiers Web.config.  Ces fichiers peuvent contenir des informations critiques telles que les noms d'utilisateurs et les mots de passe.  
  
 Bien que cette restriction ne pose généralement pas de problème pour le téléchargement des fichiers [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] principaux tels que les manifestes et les assemblys, elle peut, en revanche, vous empêcher de télécharger des fichiers de données inclus dans l'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Dans [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], vous pouvez résoudre cette erreur en supprimant du gestionnaire de configurations IIS le gestionnaire qui interdit le téléchargement de ces fichiers.  Consultez la documentation du serveur IIS pour les détails supplémentaires.  
  
 Certains serveurs Web peuvent bloquer des fichiers avec des extensions telles que .dll, .config et .mdf.  Les applications Windows comprennent généralement des fichiers portant certaines de ces extensions.  Si un utilisateur essaie d'exécuter une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] qui accède à un fichier bloqué sur un serveur Web, une erreur se produit.  Plutôt que de débloquer toutes les extensions de fichier, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] publie chaque fichier d'application avec une extension de fichier ".deploy" par défaut.  Par conséquent, l'administrateur n'a plus qu'à configurer le serveur Web pour débloquer les trois extensions de fichier suivantes :  
  
-   .application  
  
-   .manifest  
  
-   .deploy  
  
 Toutefois, vous pouvez désactiver cette option en désactivant l'option **Utiliser l'extension de fichier ".deploy"** dans la [Publish Options Dialog Box](http://msdn.microsoft.com/fr-fr/fd9baa1b-7311-4f9e-8ffb-ae50cf110592). Dans ce cas, vous devez configurer le serveur Web pour débloquer toutes les extensions de fichier utilisées dans l'application.  
  
 Vous devez configurer .manifest, .application et .deploy, par exemple, si vous utilisez IIS ailleurs qu'à l'emplacement d'installation du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] ou si vous utilisez un autre serveur Web \(par exemple, Apache\).  
  
## ClickOnce et la couche SSL \(Secure Sockets Layer\)  
 Une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] fonctionne correctement sur la couche SSL, sauf lorsque Internet Explorer émet une invite à propos du certificat SSL.  L'invite peut être émise en cas de problème avec le certificat, par exemple lorsque les noms de sites ne correspondent pas ou que le certificat a expiré.  Pour faire en sorte que [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] fonctionne sur une connexion SSL, assurez\-vous que le certificat est à jour, et que les données de certificat correspondent aux données de site.  
  
## ClickOnce et authentification proxy  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] fournit une prise en charge pour l'authentification de proxy intégrée de Windows incluse à partir de .NET Framework 3.5.  Aucune directive machine.config spécifique n'est requise.  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ne fournit pas de prise en charge pour d'autres protocoles d'authentification tels que Basic ou Digest.  
  
 Vous pouvez également appliquer un correctif logiciel à .NET Framework 2.0 pour activer cette fonction.  Pour plus d'informations, consultez http:\/\/go.microsoft.com\/fwlink\/?LinkId\=158730  
  
 Pour plus d'informations, consultez [\<defaultProxy\>, élément \(paramètres réseau\)](../Topic/%3CdefaultProxy%3E%20Element%20\(Network%20Settings\).md).  
  
## ClickOnce et compatibilité du navigateur Web  
 Actuellement, les installations [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sont lancées uniquement si l'URL du manifeste de déploiement est ouverte à l'aide d'Internet Explorer.  Un déploiement dont l'URL est lancée à partir d'une autre application, telle que Microsoft Office Outlook, sera lancé avec succès uniquement si Internet Explorer est défini comme navigateur Web par défaut.  
  
> [!NOTE]
>  Mozilla Firefox est pris en charge si le fournisseur de déploiement n'est pas vide ou si l'extension Microsoft .NET Framework Assistant est installée.  Cette extension est fournie avec .NET Framework 3.5 SP1.  Pour la prise en charge XBAP, le plug\-in NPWPF est activé si nécessaire.  
  
## Activation d'applications ClickOnce via des scripts de navigateur \(browser scripting\)  
 Si vous avez développé une page Web personnalisée qui lance une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] à l'aide d'Active Scripting, il se peut que l'application ne soit pas lancée sur certains ordinateurs.  Internet Explorer contient un paramètre appelé **Demander confirmation pour les téléchargements de fichiers** qui affecte ce comportement.  Ce paramètre est disponible sous l'onglet **Sécurité** du menu **Options** qui affecte ce comportement.  Il s'appelle **Demander confirmation pour les téléchargements de fichiers** et il est répertorié sous la catégorie **Téléchargements**.  Par défaut, la propriété a la valeur **Activer** pour les pages Web intranet et **Désactiver** pour les pages Web Internet.  Lorsque ce paramètre a la valeur **Désactiver**, toute tentative d'activation d'une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] par programmation \(par exemple, en assignant son URL à la propriété `document.location`\) sera bloquée.  Dans ce cas, les utilisateurs ne peuvent lancer les applications que via un téléchargement initialisé par utilisateur, par exemple, en cliquant sur un lien hypertexte correspondant à l'URL de l'application.  
  
## Problèmes de configuration du serveur supplémentaires  
  
##### Autorisations d'administrateur requises  
 Vous devez disposer des autorisations d'administrateur sur le serveur cible si vous publiez avec HTTP.  IIS requiert ce niveau d'autorisations.  Si vous ne publiez pas à l'aide de HTTP, vous ne devez disposer que de l'autorisation d'écriture sur le chemin d'accès cible.  
  
##### Problèmes d'authentification de serveur  
 Lors de la publication sur un serveur distant avec « Accès anonyme » désactivé, l'avertissement suivant s'affiche :  
  
```  
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."  
```  
  
> [!NOTE]
>  Vous pouvez faire fonctionner l'authentification NTLM \(stimulation\/réponse NT\) si le site demande des informations d'identification autres que celles par défaut, et que, dans la boîte de dialogue de sécurité, vous cliquez sur **OK** lorsque vous y êtes invité pour enregistrer les informations d'identification fournies pour les sessions à venir.  Toutefois, cette solution de contournement ne fonctionne pas pour l'authentification de base.  
  
## Utilisation de serveurs Web tiers  
 Si vous déployez une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] à partir d'un serveur Web autre qu'IIS, vous pouvez rencontrer un problème si le serveur retourne le type de contenu incorrect pour les fichiers [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] clés, tels que le manifeste de déploiement et le manifeste d'application.  Pour résoudre ce problème, consultez la documentation d'aide de votre serveur Web à propos de l'ajout de nouveaux types de contenus au serveur, et assurez\-vous que tous les mappages d'extension de nom de fichier répertoriés dans le tableau suivant sont en place.  
  
|Extension de nom de fichier|Type de contenu|  
|---------------------------------|---------------------|  
|`.application`|`application/x-ms-application`|  
|`.manifest`|`application/x-ms-manifest`|  
|`.deploy`|`application/octet-stream`|  
|`.msu`|`application/octet-stream`|  
|`.msp`|`application/octet-stream`|  
  
## ClickOnce et lecteurs mappés  
 Si vous utilisez Visual Studio pour publier une application ClickOnce, vous ne pouvez pas spécifier de lecteur mappé comme emplacement d'installation.  Toutefois, vous pouvez modifier l'application ClickOnce à installer à partir d'un lecteur mappé à l'aide du générateur et de l'éditeur de manifeste \(Mage.exe et MageUI.exe\).  Pour plus d'informations, consultez [Mage.exe \(outil Manifest Generation and Editing\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md) et [MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md).  
  
## Protocole FTP non pris en charge pour l'installation d'applications  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] prend en charge l'installation d'applications à partir de tout serveur de fichiers ou serveur Web HTTP 1.1.  FTP, le protocole de transfert de fichiers, n'est pas pris en charge pour l'installation d'applications.  Vous pouvez l'utiliser pour publier des applications uniquement.  Le tableau suivant récapitule ces différences :  
  
|Type URL|Description|  
|--------------|-----------------|  
|ftp:\/\/|Vous pouvez publier une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] à l'aide de ce protocole.|  
|http:\/\/|Vous pouvez installer une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] à l'aide de ce protocole.|  
|https:\/\/|Vous pouvez installer une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] à l'aide de ce protocole.|  
|file:\/\/|Vous pouvez installer une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] à l'aide de ce protocole.|  
  
## Windows XP SP2 : Pare\-feu Windows  
 Par défaut, Windows XP SP2 active le Pare\-feu Windows.  Si vous développez votre application sur un ordinateur sur lequel Windows XP est installé, vous êtes toujours en mesure de publier et d'exécuter des applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] à partir du serveur local exécutant IIS.  Toutefois, vous ne pouvez pas accéder à ce serveur exécutant IIS à partir d'un autre ordinateur à moins que vous n'ouvriez le Pare\-feu Windows.  Consultez l'aide de Windows pour obtenir les instructions sur la gestion du Pare\-feu Windows.  
  
## Windows Server : activez les extensions serveur FrontPage  
 Les extensions serveur FrontPage de Microsoft sont indispensables pour publier des applications sur un serveur Web Windows qui utilise HTTP.  
  
 Par défaut, les extensions serveur FrontPage ne sont pas installées sous Windows Server.  Si vous souhaitez utiliser [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour publier sur un serveur Web Windows Server qui utilise HTTP avec les extensions serveur FrontPage, vous devez d'abord installer les extensions serveur FrontPage.  Vous pouvez effectuer l'installation à l'aide de l'outil d'administration Gérer votre serveur dans Windows Server.  
  
## Windows Server : types de contenus verrouillés  
 Sous [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)], IIS verrouille tous les types de fichier, à l'exception de certains types de contenus connus \(par exemple, .htm, .html, .txt, etc.\).  Pour permettre le déploiement d'applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] à l'aide de ce serveur, vous devez modifier les paramètres IIS afin d'autoriser le téléchargement de fichiers de type .application, .manifest, et de tout autre type de fichier personnalisé utilisé par votre application.  
  
 Si vous effectuez le déploiement à l'aide d'un serveur IIS, exécutez inetmgr.exe et ajoutez de nouveaux Types de fichiers pour la page Web par défaut :  
  
-   Pour les extensions .application et .manifest, le type MIME doit être "application\/x\-ms\-application". Pour les autres types de fichier, le type MIME doit être "application\/octet\-stream".  
  
-   Si vous créez un type MIME avec l'extension "\*" et le type MIME "application\/octet\-stream", il autorisera le téléchargement de fichiers débloqués.  \(Toutefois, les fichiers bloqués tels que .aspx et .asmx ne peuvent pas être téléchargés.\)  
  
 Pour obtenir des instructions spécifiques sur la configuration de types MIME sous Windows Server, consultez l'article KB326965, « IIS 6.0 ne dessert pas de type MIME inconnu » \(éventuellement en anglais\), de la Base de connaissances Microsoft à l'adresse [http:\/\/support.microsoft.com\/kb\/326965\/fr\-fr](http://support.microsoft.com/kb/326965/fr-fr).  
  
## Mappages de types de contenus  
 Lors de la publication sur HTTP, le type de contenu \(également appelé type MIME\) du fichier .application doit être « application\/x\-ms\-application ». Si le [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] est installé sur le serveur, il sera configuré automatiquement.  S'il n'est pas installé, vous devez créer une association de types MIME pour la racine virtuelle \(ou serveur entier\) de l'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 Si vous effectuez le déploiement à l'aide d'un serveur IIS, exécutez inetmgr.exe et ajoutez un nouveau type de contenu de « application\/x\-ms\-application » pour l'extension .application.  
  
## Problèmes de compression HTTP  
 Avec [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], vous pouvez exécuter des téléchargements qui utilisent la compression HTTP, une technologie de serveur Web qui utilise l'algorithme GZIP pour compresser un flux de données avant de l'envoyer au client.  Le client, dans ce cas\-ci [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], décompresse le flux de données avant de lire les fichiers.  
  
 Si vous utilisez IIS, vous pouvez facilement activer la compression HTTP.  Toutefois, lorsque vous activez la compression HTTP, elle n'est activée que pour certains fichiers — à savoir, les fichiers texte et HTML.  Pour activer la compression pour les assemblys \(.dll\), XML \(.xml\), les manifestes de déploiement \(.application\) et les manifestes d'application \(.manifest\), vous devez ajouter ces types de fichier à la liste de types qu'IIS doit compresser.  Tant que vous n'ajoutez pas les types de fichier à votre déploiement, seuls les fichiers texte et HTML seront compressés.  
  
 Pour obtenir des instructions détaillées concernant IIS, consultez [Comment spécifier des types de documents supplémentaires pour la compression HTTP \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=178459).  
  
## Voir aussi  
 [Troubleshooting ClickOnce Deployments](../deployment/troubleshooting-clickonce-deployments.md)   
 [Choosing a ClickOnce Deployment Strategy](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Composants requis pour le déploiement d'applications](../deployment/application-deployment-prerequisites.md)