---
title: Sécurité/contrôle de version/problèmes de manifeste (ClickOnce)
description: Découvrez les problèmes liés à la sécurité ClickOnce, au contrôle de version de l’application et à la syntaxe du manifeste et à la sémantique qui peuvent provoquer le non-respect d’un déploiement ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 55758f67c845cbf753d51ebfb94b87af6cf55cde
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877627"
---
# <a name="security-versioning-and-manifest-issues-in-clickonce-deployments"></a>Problèmes liés à la sécurité, à la gestion de version et aux manifestes dans les déploiements ClickOnce

Il existe divers problèmes liés à la sécurité, au contrôle de version de l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application, à la syntaxe du manifeste et à la sémantique qui peuvent provoquer l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] échec du déploiement.

## <a name="clickonce-and-windows-vista-user-account-control"></a>Contrôle de compte d’utilisateur ClickOnce et Windows Vista

Dans [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] , les applications s’exécutent par défaut en tant qu’utilisateur standard, même si l’utilisateur actuel est connecté avec un compte disposant d’autorisations d’administrateur. Si une application doit exécuter une action qui requiert des autorisations d’administrateur, elle indique au système d’exploitation qu’elle invite ensuite l’utilisateur à entrer ses informations d’identification d’administrateur. Cette fonctionnalité, appelée contrôle de compte d’utilisateur (UAC, User Account Control), empêche les applications d’apporter des modifications qui peuvent affecter l’ensemble du système d’exploitation sans l’approbation explicite d’un utilisateur. Les applications Windows déclarent qu’elles nécessitent cette élévation d’autorisations en spécifiant l' `requestedExecutionLevel` attribut dans la `trustInfo` section de leur manifeste d’application.

En raison du risque d’exposition des applications aux attaques d’élévation de sécurité, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] les applications ne peuvent pas demander d’élévation d’autorisations si le contrôle de compte d’utilisateur est activé pour le client. Toute [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application qui tente de définir son `requestedExecutionLevel` attribut sur `requireAdministrator` ou ne `highestAvailable` s’installe pas sur [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] .

Dans certains cas, votre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application peut tenter de s’exécuter avec des autorisations d’administrateur en raison de la logique de détection du programme d’installation sur [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] . Dans ce cas, vous pouvez définir l' `requestedExecutionLevel` attribut dans le manifeste de l’application sur `asInvoker` . Cela entraînera l’exécution de l’application elle-même sans élévation. [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] ajoute automatiquement cet attribut à tous les manifestes d’application.

Si vous développez une application qui requiert des autorisations d’administrateur pour toute la durée de vie de l’application, vous devez envisager de déployer l’application à l’aide de la technologie Windows Installer (MSI) à la place. Pour plus d’informations, consultez [principes de base de Windows Installer](../extensibility/internals/windows-installer-basics.md).

## <a name="online-application-quotas-and-partial-trust-applications"></a>Quotas d’application en ligne et applications de confiance partielle

Si votre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application s’exécute en ligne au lieu d’une installation, elle doit tenir dans le quota réservé aux applications en ligne. En outre, une application réseau qui s’exécute en confiance partielle, par exemple avec un ensemble limité d’autorisations de sécurité, ne peut pas être supérieure à la moitié de la taille de quota.

Pour plus d’informations et pour obtenir des instructions sur la façon de modifier le quota d’applications en ligne, consultez [vue d’ensemble du cache ClickOnce](../deployment/clickonce-cache-overview.md).

## <a name="versioning-issues"></a>Problèmes de gestion des versions

Vous pouvez rencontrer des problèmes si vous assignez des noms forts à votre assembly et que vous incrémentez le numéro de version de l’assembly pour refléter une mise à jour d’application. Tout assembly compilé avec une référence à un assembly avec nom fort doit lui-même être recompilé, sinon l’assembly tente de faire référence à l’ancienne version. L’assembly va essayer cela, car l’assembly utilise l’ancienne valeur de la version dans sa demande de liaison.

Par exemple, imaginons que vous ayez un assembly avec nom fort dans son propre projet avec la version 1.0.0.0. Après avoir compilé l’assembly, vous l’ajoutez en tant que référence au projet qui contient votre application principale. Si vous mettez à jour l’assembly, incrémentez la version à 1.0.0.1 et essayez de la déployer sans recompiler également l’application, l’application ne sera pas en mesure de charger l’assembly au moment de l’exécution.

Cette erreur peut se produire uniquement si vous modifiez vos [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestes manuellement. vous ne devriez pas rencontrer cette erreur si vous générez votre déploiement à l’aide de Visual Studio.

## <a name="specify-individual-net-framework-assemblies-in-the-manifest"></a>Spécifier des assemblys .NET Framework individuels dans le manifeste

Le chargement de votre application échoue si vous avez modifié manuellement un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déploiement pour référencer une version antérieure d’un assembly de .NET Framework. Par exemple, si vous avez ajouté une référence à l’assembly System.Net pour une version de la .NET Framework antérieure à la version spécifiée dans le manifeste, une erreur se produit. En général, vous ne devez pas tenter de spécifier des références à des assemblys .NET Framework individuels, car la version de la .NET Framework par rapport à laquelle votre application s’exécute est spécifiée en tant que dépendance dans le manifeste de l’application.

## <a name="manifest-parsing-issues"></a>Problèmes d’analyse du manifeste

Les fichiers manifestes utilisés par [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sont des fichiers XML et doivent être correctement formés et valides : ils doivent respecter les règles de syntaxe XML et utiliser uniquement les éléments et les attributs définis dans le schéma XML approprié.

Un fichier de manifeste peut être à l’origine d’un problème en sélectionnant un nom pour votre application qui contient un caractère spécial, tel qu’un guillemet simple ou double. Le nom de l’application fait partie de son [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] identité. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] actuellement, n’analyse pas les identités qui contiennent des caractères spéciaux. Si votre application ne parvient pas à s’activer, assurez-vous que vous utilisez uniquement des caractères alphabétiques et numériques pour le nom, puis essayez de la déployer à nouveau.

Si vous avez modifié manuellement vos manifestes de déploiement ou d’application, vous pouvez les corrompre involontairement. Le manifeste endommagé empêchera une installation correcte [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Vous pouvez déboguer ces erreurs au moment de l’exécution en cliquant sur **Détails** dans la boîte de dialogue **erreur ClickOnce** et en lisant le message d’erreur dans le journal. Le journal affiche l’un des messages suivants :

- Une description de l’erreur de syntaxe, ainsi que le numéro de ligne et la position du caractère où l’erreur s’est produite.

- Nom d’un élément ou d’un attribut utilisé en violation du schéma du manifeste. Si vous avez ajouté manuellement du code XML à vos manifestes, vous devrez comparer vos ajouts aux schémas de manifeste. Pour plus d’informations, consultez [manifeste de déploiement ClickOnce](../deployment/clickonce-deployment-manifest.md) et [manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md).

- Conflit d’ID. Les références de dépendance dans les manifestes de déploiement et d’application doivent être uniques dans leurs `name` `publicKeyToken` attributs et. Si les deux attributs correspondent entre deux éléments dans un manifeste, l’analyse du manifeste échoue.

## <a name="precautions-when-manually-changing-manifests-or-applications"></a>Précautions lors de la modification manuelle de manifestes ou d’applications

Lorsque vous mettez à jour un manifeste d’application, vous devez signer à nouveau le manifeste de l’application et le manifeste de déploiement. Le manifeste de déploiement contient une référence au manifeste d’application qui inclut le hachage de ce fichier et sa signature numérique.

### <a name="precautions-with-deployment-provider-usage"></a>Précautions avec l’utilisation du fournisseur de déploiement

Le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifeste de déploiement a une `deploymentProvider` propriété qui pointe vers le chemin d’accès complet de l’emplacement à partir duquel l’application doit être installée et desservie :

```xml
<deploymentProvider codebase="http://myserver/myapp.application" />
```

Ce chemin d’accès est défini lors [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] de la création de l’application et est obligatoire pour les applications installées. Le chemin d’accès pointe vers l’emplacement standard [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] à partir duquel le programme d’installation installe l’application et recherche les mises à jour. Si vous utilisez la commande **xcopy** pour copier une [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application vers un autre emplacement, mais que vous ne modifiez pas la `deploymentProvider` propriété, fait [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] toujours référence à l’emplacement d’origine lorsqu’elle tente de télécharger l’application.

Si vous souhaitez déplacer ou copier une application, vous devez également mettre à jour le `deploymentProvider` chemin d’accès, afin que le client s’installe à partir du nouvel emplacement. La mise à jour de ce chemin d’accès est principalement un problème si vous avez installé des applications. Pour les applications en ligne qui sont toujours lancées par le biais de l’URL d’origine, la définition de `deploymentProvider` est facultative. Si `deploymentProvider` est défini, il sera respecté ; dans le cas contraire, l’URL utilisée pour démarrer l’application sera utilisée comme URL de base pour télécharger les fichiers d’application.

> [!NOTE]
> Chaque fois que vous mettez à jour le manifeste, vous devez également le signer à nouveau.

## <a name="see-also"></a>Voir aussi

[Résoudre les problèmes liés aux déploiements ClickOnce](../deployment/troubleshooting-clickonce-deployments.md) 
 [Sécuriser les applications ClickOnce](../deployment/securing-clickonce-applications.md) 
 [Choisir une stratégie de déploiement ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
