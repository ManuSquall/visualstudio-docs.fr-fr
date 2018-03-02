---
title: "Problèmes de sécurité, le contrôle de version et manifestes dans les déploiements ClickOnce | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
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
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 2dd693a35725d41b2b8ced99d78bd4a62d8d9e3a
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="security-versioning-and-manifest-issues-in-clickonce-deployments"></a>Problèmes liés à la sécurité, au contrôle de version et aux manifestes dans les déploiements ClickOnce

Il existe une multitude de problèmes avec [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sécurité, versioning d’application et manifeste syntaxe et sémantique qui peut entraîner un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] réussite du déploiement ne pas.

## <a name="clickonce-and-windows-vista-user-account-control"></a>ClickOnce et le contrôle de compte d’utilisateur Windows Vista

Dans [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)], applications par défaut s’exécutent en tant qu’utilisateur standard, même si l’utilisateur actuel est connecté avec un compte qui dispose des autorisations d’administrateur. Si une application doit exécuter une action qui nécessite des autorisations d’administrateur, il indique le système d’exploitation, puis invite l’utilisateur à entrer leurs informations d’identification d’administrateur. Cette fonctionnalité, appelée contrôle de compte d’utilisateur (UAC), empêche les applications d’apporter des modifications susceptibles d’affecter l’ensemble du système d’exploitation sans une approbation explicite d’un utilisateur. Applications Windows déclarent qu’ils ont besoin de cette élévation d’autorisations en spécifiant le `requestedExecutionLevel` l’attribut dans la `trustInfo` section de leur manifeste d’application.

En raison du risque d’exposition aux attaques par élévation de sécurité, les applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applications ne peuvent pas demander l’élévation d’autorisations si le compte d’utilisateur est activé pour le client. N’importe quel [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application qui tente de définir son `requestedExecutionLevel` attribut `requireAdministrator` ou `highestAvailable` s’installe pas sur [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)].

Dans certains cas, votre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application peut essayer de s’exécuter avec des autorisations d’administrateur en raison de la logique de détection de programme d’installation sur [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]. Dans ce cas, vous pouvez définir le `requestedExecutionLevel` attribut dans le manifeste d’application pour `asInvoker`. Cela entraîne l’application elle-même à s’exécuter sans élévation. [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] ajoute automatiquement cet attribut à tous les manifestes d’application.

Si vous développez une application qui nécessite des autorisations d’administrateur pour toute la durée de vie de l’application, vous devez envisager de déployer l’application à l’aide de la technologie Windows Installer (MSI) à la place. Pour plus d’informations, consultez [concepts de base de Windows Installer](../extensibility/internals/windows-installer-basics.md).

## <a name="online-application-quotas-and-partial-trust-applications"></a>Applications de confiance partielle et les Quotas de l’Application en ligne

Si votre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application s’exécute en ligne et non via une installation, elle doit répondre au quota défini à part pour les applications en ligne. En outre, une application de réseau qui s’exécute en confiance partielle, comme avec un ensemble limité d’autorisations de sécurité, ne peut pas être supérieure à la moitié de la taille de quota.

Pour plus d’informations et d’instructions sur la façon de modifier le quota d’application en ligne, consultez [vue d’ensemble du Cache ClickOnce](../deployment/clickonce-cache-overview.md).

## <a name="versioning-issues"></a>Problèmes de contrôle de version

Vous pouvez rencontrer des problèmes si vous assignez des noms forts à votre assembly et incrémentez le numéro de version d’assembly pour refléter une mise à jour de l’application. Tout assembly compilé avec une référence à un assembly avec nom fort doit être recompilé, ou l’assembly va tenter de faire référence à la version antérieure. L’assembly il essaiera, car l’assembly est à l’aide de l’ancienne valeur de version dans sa demande de liaison.

Par exemple, que vous disposez d’un assembly avec nom fort dans son propre projet avec la version 1.0.0.0. Après la compilation de l’assembly, ajoutez-le en tant que référence au projet qui contient votre application principale. Si vous mettre à jour de l’assembly, que vous incrémentez la version à 1.0.0.1 et que vous tentez de déployer sans recompiler également l’application, il se peut que l’application ne sera pas en mesure de charger l’assembly au moment de l’exécution.

Cette erreur peut se produire uniquement si vous modifiez votre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestes manuellement ; vous ne devez pas rencontrer cette erreur si vous générez votre déploiement à l’aide de Visual Studio.

## <a name="specifying-individual-net-framework-assemblies-in-the-manifest"></a>Spécification des assemblys .NET Framework individuels dans le manifeste

Votre application ne sera pas chargé si vous avez modifié manuellement un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déploiement pour faire référence à une version antérieure d’un [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] assembly. Par exemple, si vous avez ajouté une référence à l’assembly System.Net pour une version de le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] avant la version spécifiée dans le manifeste, une erreur se produit. Dans général, vous ne devez pas essayer spécifier des références à personne [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] assemblys, comme la version de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] sur laquelle votre application s’exécute est spécifiée comme une dépendance dans le manifeste d’application.

## <a name="manifest-parsing-issues"></a>Problèmes d’analyse du manifeste

Les fichiers manifeste utilisés par [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sont des fichiers XML, et ils doivent être correctement constitué et valide : ils doivent respecter les règles de syntaxe XML et utiliser uniquement les éléments et attributs définis dans le schéma XML pertinent.

Un élément qui peut entraîner des problèmes dans un fichier manifeste consiste à sélectionner un nom pour votre application qui contient un caractère spécial, tel qu’une marque de guillemets simple ou double. Nom de l’application fait partie de son [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] identité. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] actuellement n’analyse pas les identités qui contiennent des caractères spéciaux. Si votre application ne parvient pas à activer, assurez-vous que vous avez sont à l’aide de caractères alphabétiques et numériques d’uniquement pour le nom et que vous tentez de déployer une nouvelle fois.

Si vous avez modifié manuellement vos manifestes de déploiement ou d’application, vous avez endommagés volontairement les. Un manifeste endommagé empêche une correct [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installation. Vous pouvez déboguer de telles erreurs au moment de l’exécution en cliquant sur **détails** sur la **erreur ClickOnce** boîte de dialogue et à lire le message d’erreur dans le journal. Le journal répertorie l’un des messages suivants :

- Obtenir une description de l’erreur de syntaxe et le numéro de ligne et position où l’erreur s’est produite.

- Le nom d’un élément ou attribut utilisé, contraire au schéma du manifeste. Si vous avez ajouté manuellement des XML à vos manifestes, vous devez comparer vos ajouts aux schémas de manifeste. Pour plus d’informations, consultez [le manifeste de déploiement ClickOnce](../deployment/clickonce-deployment-manifest.md) et [manifeste d’Application ClickOnce](../deployment/clickonce-application-manifest.md).

- Un conflit d’ID. Références de dépendance dans les manifestes de déploiement et d’application doivent être uniques à la fois dans leur `name` et `publicKeyToken` attributs. Si les deux attributs correspondent entre deux éléments d’un manifeste, l’analyse du manifeste ne réussira pas.

## <a name="precautions-when-manually-changing-manifests-or-applications"></a>Précautions lorsque vous modifiez manuellement les manifestes ou Applications

Lorsque vous mettez à jour un manifeste d’application, vous devez signer de nouveau le manifeste d’application et le manifeste de déploiement. Le manifeste de déploiement contient une référence au manifeste d’application qui inclut le hachage de ce fichier et sa signature numérique.

### <a name="precautions-with-deployment-provider-usage"></a>Précautions lors de l’utilisation du fournisseur de déploiement

Le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] le manifeste de déploiement contient un `deploymentProvider` propriété pointant vers le chemin d’accès complet de l’emplacement à partir de sur lequel l’application doit être installée et de maintenance :

```xml
<deploymentProvider codebase="http://myserver/myapp.application" />
```

Ce chemin d’accès est défini lorsque [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] crée l’application et est obligatoire pour les applications installées. Le chemin d’accès pointe vers l’emplacement standard où le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] programme d’installation va installer l’application à partir d’et rechercher des mises à jour. Si vous utilisez la **xcopy** commande pour copier un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application dans un emplacement différent, mais ne modifiez pas le `deploymentProvider` propriété, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sera toujours faire référence à l’emplacement d’origine lorsqu’il tente de télécharger le application.

Si vous souhaitez déplacer ou copier une application, vous devez également mettre à jour le `deploymentProvider` chemin d’accès, afin que le client installe réellement dans le nouvel emplacement. Ce chemin d’accès de mise à jour s’applique principalement si vous avez installé des applications. Pour les applications en ligne qui sont toujours lancées par l’URL d’origine, en définissant le `deploymentProvider` est facultatif. Si `deploymentProvider` est définie, elle est respectée ; sinon, l’URL utilisée pour démarrer l’application est utilisé en tant que l’URL de base pour télécharger les fichiers d’application.

> [!NOTE]
> Chaque fois que vous mettez à jour le manifeste vous devez également le signer à nouveau.

## <a name="see-also"></a>Voir aussi

[Dépannage des déploiements ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)  
[Sécurisation des applications ClickOnce](../deployment/securing-clickonce-applications.md)  
[Choix d’une stratégie de déploiement ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)