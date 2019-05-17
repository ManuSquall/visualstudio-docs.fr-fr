---
title: Problèmes de sécurité, le contrôle de version et manifestes dans les déploiements ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- versioning, ClickOnce applications
- ClickOnce applications, Windows Vista User Account Control
- ClickOnce applications, versioning issues
- security, ClickOnce applications
- Windows 7, ClickOnce deployments
- ClickOnce applications, manifest issues
- User Account Control, ClickOnce applications
- Windows Vista, ClickOnce deployments
- manifests [ClickOnce]
- ClickOnce applications, security issues
ms.assetid: d5d0c90b-ac1a-44e2-88dc-0d0ffd881624
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a4864d37cb5930075b292ee765bce9b288794019
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444989"
---
# <a name="security-versioning-and-manifest-issues-in-clickonce-deployments"></a>Problèmes liés à la sécurité, au contrôle de version et aux manifestes dans les déploiements ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il existe une variété de problèmes avec [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] sécurité, des versions et manifeste de syntaxe et sémantique qui peut entraîner un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] réussite du déploiement ne pas.  
  
## <a name="clickonce-and-windows-vista-user-account-control"></a>ClickOnce et contrôle de compte d’utilisateur Windows Vista  
 Dans [!INCLUDE[windowsver](../includes/windowsver-md.md)], applications par défaut exécutent en tant qu’utilisateur standard, même si l’utilisateur actuel est connecté avec un compte disposant des autorisations d’administrateur. Si une application doit effectuer une action qui nécessite des autorisations d’administrateur, elle indique le système d’exploitation, puis invite l’utilisateur à entrer leurs informations d’identification d’administrateur. Cette fonctionnalité, appelée contrôle de compte utilisateur (UAC), empêche les applications d’apporter des modifications susceptibles d’affecter l’ensemble du système d’exploitation sans approbation explicite d’un utilisateur. Les applications Windows déclarent qu’ils nécessitent l’élévation d’autorisations en spécifiant le `requestedExecutionLevel` d’attribut dans la `trustInfo` section de leur manifeste d’application.  
  
 En raison du risque d’exposition aux attaques d’élévation de sécurité, les applications [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applications ne peuvent pas demander l’élévation d’autorisations si UAC est activé pour le client. N’importe quel [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application qui tente de définir son `requestedExecutionLevel` attribut `requireAdministrator` ou `highestAvailable` n’installera pas sur [!INCLUDE[windowsver](../includes/windowsver-md.md)].  
  
 Dans certains cas, votre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application peut essayer de s’exécuter avec les autorisations d’administrateur en raison de la logique de détection de programme d’installation sur [!INCLUDE[windowsver](../includes/windowsver-md.md)]. Dans ce cas, vous pouvez définir le `requestedExecutionLevel` attribut dans le manifeste d’application pour `asInvoker`. Cela entraîne l’application de manière à s’exécuter sans élévation. [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] ajoute automatiquement cet attribut à tous les manifestes d’application.  
  
 Si vous développez une application qui nécessite des autorisations d’administrateur pour toute la durée de vie de l’application, vous devez envisager le déploiement de l’application à l’aide de la technologie Windows Installer (MSI) à la place. Pour plus d’informations, consultez [principes fondamentaux du programme d’installation Windows](../extensibility/internals/windows-installer-basics.md).  
  
## <a name="online-application-quotas-and-partial-trust-applications"></a>Applications de confiance partielle et des Quotas de l’Application en ligne  
 Si votre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application s’exécute en ligne et non via une installation, elle doit répondre au quota défini à part pour les applications en ligne. En outre, une application de réseau qui s’exécute en confiance partielle, comme avec un ensemble limité d’autorisations de sécurité, ne peut pas être supérieure à la moitié de la taille de quota.  
  
 Pour plus d’informations et d’obtenir des instructions sur la façon de modifier le quota d’application en ligne, consultez [vue d’ensemble du Cache ClickOnce](../deployment/clickonce-cache-overview.md).  
  
## <a name="versioning-issues"></a>Problèmes de contrôle de version  
 Vous pouvez rencontrer des problèmes si vous assignez des noms forts à votre assembly et incrémentez le numéro de version d’assembly pour refléter une mise à jour de l’application. N’importe quel assembly compilé avec une référence à un assembly avec nom fort doit être recompilé ou l’assembly va tenter de faire référence à l’ancienne version. L’assembly va tenter cela, car l’assembly est à l’aide de l’ancienne valeur de version dans sa demande de liaison.  
  
 Par exemple, que vous avez un assembly avec nom fort dans son propre projet avec la version 1.0.0.0. Après la compilation de l’assembly, ajoutez-le en tant que référence au projet qui contient votre application principale. Si vous mettez à jour l’assembly, incrémentez la version à 1.0.0.1 et tentez de déployer sans recompiler également l’application, il se peut que l’application ne sera pas en mesure de charger l’assembly au moment de l’exécution.  
  
 Cette erreur peut se produire uniquement si vous modifiez votre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestes manuellement ; vous ne devez pas rencontrer cette erreur si vous générez votre déploiement à l’aide [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)].  
  
## <a name="specifying-individual-net-framework-assemblies-in-the-manifest"></a>Spécification des assemblys .NET Framework individuels dans le manifeste  
 Votre application ne sera pas chargé si vous avez modifié manuellement un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] déploiement pour référencer une version antérieure d’un [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] assembly. Par exemple, si vous avez ajouté une référence à l’assembly System.Net pour une version de le [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] avant la version spécifiée dans le manifeste, une erreur se produit. En général, vous ne devez pas essayer spécifier des références à la personne [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] assemblys, comme la version de la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] par rapport à laquelle votre application s’exécute est spécifié en tant que dépendance dans le manifeste d’application.  
  
## <a name="manifest-parsing-issues"></a>Problèmes d’analyse du manifeste  
 Les fichiers manifeste sont utilisés par [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] sont des fichiers XML, et ils doivent être bien formé et valide : ils doivent respecter les règles de syntaxe XML et utiliser uniquement les éléments et attributs définis dans le schéma XML pertinent.  
  
 Quelque chose qui peut entraîner des problèmes dans un fichier manifeste consiste à sélectionner un nom pour votre application qui contient un caractère spécial, tel qu’une marque de guillemets simple ou double. Nom de l’application fait partie de son [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] identité. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] actuellement n’analyse pas les identités qui contiennent des caractères spéciaux. Si votre application ne parvient pas à activer, assurez-vous que vous utilisez des caractères alphabétiques et numériques d’uniquement pour le nom et tentez de déployer de nouveau.  
  
 Si vous avez modifié manuellement vos manifestes de déploiement ou d’application, vous avez endommagés volontairement leur. Un manifeste endommagé empêche une correct [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] installation. Vous pouvez déboguer ces erreurs en cours d’exécution en cliquant sur **détails** sur le **erreur ClickOnce** boîte de dialogue et en lisant le message d’erreur dans le journal. Le journal répertorie l’un des messages suivants :  
  
- Une description de l’erreur de syntaxe et le numéro de ligne et position où l’erreur s’est produite.  
  
- Le nom d’un élément ou un attribut utilisé en violation de schéma du manifeste. Si vous avez ajouté manuellement XML à vos manifestes, vous devrez comparer vos ajouts aux schémas de manifeste. Pour plus d’informations, consultez [du manifeste de déploiement ClickOnce](../deployment/clickonce-deployment-manifest.md) et [manifeste d’Application ClickOnce](../deployment/clickonce-application-manifest.md).  
  
- Un conflit d’ID. Références de dépendance dans les manifestes d’application et de déploiement doivent être uniques à la fois dans leur `name` et `publicKeyToken` attributs. Si les deux attributs correspondent entre deux éléments d’un manifeste, l’analyse du manifeste ne réussira pas.  
  
## <a name="precautions-when-manually-changing-manifests-or-applications"></a>Précautions lorsque vous modifiez manuellement les manifestes ou des Applications  
 Lorsque vous mettez à jour un manifeste d’application, vous devez resigner le manifeste d’application et le manifeste de déploiement. Le manifeste de déploiement contient une référence au manifeste d’application qui inclut le hachage de ce fichier et sa signature numérique.  
  
### <a name="precautions-with-deployment-provider-usage"></a>Précautions lors de l’utilisation du fournisseur de déploiement  
 Le [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] le manifeste de déploiement contient un `deploymentProvider` propriété qui pointe vers le chemin d’accès complet de l’emplacement à partir d’où l’application doit être installée et pris en charge :  
  
```  
<deploymentProvider codebase="http://myserver/myapp.application" />  
```  
  
 Ce chemin d’accès est définie lorsque [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] crée l’application et est obligatoire pour les applications installées. Le chemin d’accès pointe vers l’emplacement standard où le [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] programme d’installation va installer l’application à partir d’et rechercher les mises à jour. Si vous utilisez le **xcopy** commande pour copier un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application vers un autre emplacement, mais ne modifiez pas le `deploymentProvider` propriété, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] se réfère toujours à l’emplacement d’origine lorsqu’il tente de télécharger le application.  
  
 Si vous souhaitez déplacer ou copier une application, vous devez également mettre à jour le `deploymentProvider` chemin d’accès, afin que le client installe réellement à partir du nouvel emplacement. Ce chemin d’accès de la mise à jour s’applique principalement si vous avez installé des applications. Pour les applications en ligne qui sont toujours lancées via l’URL d’origine, en définissant le `deploymentProvider` est facultatif. Si `deploymentProvider` est définie, elle est respectée ; sinon, l’URL utilisée pour démarrer l’application sera utilisé en tant que l’URL de base pour télécharger les fichiers d’application.  
  
> [!NOTE]
> Chaque fois que vous mettez à jour le manifeste vous devez également le signer à nouveau.  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage des déploiements ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)   
 [Sécurisation des applications ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Choix d’une stratégie de déploiement ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
