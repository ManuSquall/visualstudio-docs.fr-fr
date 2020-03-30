---
title: Déployer les applications ClickOnce sans re-signer
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, deploying without resigning
- ClickOnce deployment, without resigning
- application updates, ClickOnce
- update location [ClickOnce]
- deploymentProvider tag
- manifests [ClickOnce]
ms.assetid: 1218a98d-1ad5-4eef-95dd-0e0b3c44168c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89e1d7970b26d5ba9bd49090362a6a4e8c09f78d
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395318"
---
# <a name="deploy-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Déployer des applications ClickOnce pour les serveurs de test et de production sans démissionner
Cet article décrit une fonctionnalité de ClickOnce introduite dans la version .NET Framework 3.5 qui permet le déploiement d’applications ClickOnce à partir de plusieurs emplacements réseau sans re-signer ou modifier les manifestes ClickOnce.

> [!NOTE]
> La démission reste la méthode préférée pour déployer de nouvelles versions d’applications. Dans la mesure du possible, utilisez la méthode démissionnaire. Pour plus d’informations, consultez [*Mage.exe* (outil Manifest Generation and Editing)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

 Les développeurs tiers et les ISV peuvent adhérer à cette fonctionnalité, ce qui permet à leurs clients de mettre à jour leurs applications plus facilement. Cette fonctionnalité peut être utilisée dans les situations suivantes :

- Lors de la mise à jour d’une application, pas pour la première installation d’une application.

- Lorsqu’il n’y a qu’une seule configuration de l’application sur un ordinateur. Par exemple, si une application est configurée pour indiquer deux bases de données différentes, vous ne pouvez pas utiliser cette fonctionnalité.

## <a name="exclude-deploymentprovider-from-deployment-manifests"></a>Exclure le déploiementProvider des manifestes de déploiement
 Dans le cadre .NET 2.0 et le .NET Framework 3.0, toute application ClickOnce qui `deploymentProvider` s’installe sur le système pour la disponibilité hors ligne doit énumérer un manifeste de déploiement. L’endroit `deploymentProvider` est souvent appelé l’emplacement de mise à jour; c’est l’endroit où ClickOnce vérifie pour les mises à jour de l’application. Cette exigence, ainsi que la nécessité pour les éditeurs d’applications de signer leurs déploiements, a rendu difficile pour une entreprise de mettre à jour une application ClickOnce d’un fournisseur ou d’un autre tiers. Il est également plus difficile de déployer la même application à partir de plusieurs emplacements sur le même réseau.

 Avec les modifications apportées à ClickOnce dans le cadre .NET 3.5, il est possible pour un tiers de fournir une application ClickOnce à une autre organisation, qui peut ensuite déployer l’application sur son propre réseau.

 Afin de profiter de cette fonctionnalité, les développeurs `deploymentProvider` d’applications ClickOnce doivent exclure de leurs manifestes de déploiement. Cette exigence signifie que `-providerUrl` vous devez exclure l’argument lorsque vous créez des manifestes de déploiement avec Mage.exe. Ou, si vous généssez des manifestes de déploiement avec MageUI.exe, vous devez vous assurer que la boîte de texte **de localisation de lancement** sur **l’onglet Manifeste d’application** est laissée vide.

## <a name="deploymentprovider-and-application-updates"></a>déploiementProvider et mises à jour d’applications
 En commençant par le cadre .NET 3.5, `deploymentProvider` vous n’avez plus à spécifier un manifeste de déploiement dans votre manifeste de déploiement afin de déployer une application ClickOnce pour l’utilisation en ligne et hors ligne. Ce changement prend en charge le scénario où vous devez emballer et signer le déploiement vous-même, mais permet à d’autres entreprises de déployer l’application sur leurs réseaux.

 Le point important à retenir est `deploymentProvider` que les applications qui excluent un ne `deploymentProvider` peut pas changer leur emplacement d’installation pendant les mises à jour, jusqu’à ce qu’ils expédient une mise à jour qui inclut le tag à nouveau.

 Voici deux exemples pour clarifier ce point. Dans le premier exemple, vous publiez une `deploymentProvider` application ClickOnce qui n’a pas d’étiquette, et vous demandez aux utilisateurs de l’installer à partir de `http://www.adatum.com/MyApplication/`. Si vous décidez que vous souhaitez publier `http://subdomain.adatum.com/MyApplication/`la prochaine mise à jour de l’application `http://www.adatum.com/MyApplication/`à partir de , vous n’avez aucun moyen de le signifier dans le manifeste de déploiement qui réside dans . Vous pouvez faire l’une des deux choses:

- Dites à vos utilisateurs de désinstaller la version précédente et d’installer la nouvelle version à partir du nouvel emplacement.

- Inclure une `http://www.adatum.com/MyApplication/` mise à `deploymentProvider` jour `http://www.adatum.com/MyApplication/`sur qui comprend un pointage à . Puis, publier une `deploymentProvider` autre `http://subdomain.adatum.com/MyApplication/`mise à jour plus tard avec pointant vers .

  Dans le deuxième exemple, vous publiez une `deploymentProvider`application ClickOnce qui spécifie, et vous décidez ensuite de la supprimer. Une fois que `deploymentProvider` la nouvelle version sans est téléchargée vers les clients, vous `deploymentProvider` ne pouvez pas rediriger le chemin utilisé pour les mises à jour jusqu’à ce que vous libériez une version de votre application qui a restauré. Comme avec le `deploymentProvider` premier exemple, doit d’abord pointer vers l’emplacement de mise à jour en cours, pas votre nouvel emplacement. Dans ce cas, si vous `deploymentProvider` essayez d’insérer un qui se réfère à `http://subdomain.adatum.com/MyApplication/`, puis la prochaine mise à jour échoue.

## <a name="create-a-deployment"></a>Créer un déploiement
 Pour des conseils étape par étape sur la création de déploiements qui peuvent être déployés à partir de différents emplacements réseau, voir [Pas à pas: Déployer manuellement une application ClickOnce qui ne nécessite pas de re-signer et qui préserve les informations de marque](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md).

## <a name="see-also"></a>Voir aussi
- [*Mage.exe* (Manifeste Génération et outil d’édition)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [*MageUI.exe* (Manifeste Generation and Editing Tool, Graphical Client)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
