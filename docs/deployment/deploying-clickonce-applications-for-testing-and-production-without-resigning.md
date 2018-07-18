---
title: Déploiement d’Applications ClickOnce pour les tests et les serveurs de Production sans nouvelle signature | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 57b4761ed7f0b223e459fc1ac77ad93c546e02dc
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34266187"
---
# <a name="deploying-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Déploiement d'applications ClickOnce pour des serveurs de test et de production sans nouvelle signature
Cet article décrit une fonctionnalité de ClickOnce présentée dans le .NET Framework version 3.5 qui permet le déploiement d’applications ClickOnce à partir de plusieurs emplacements réseau sans nouvelle signature ni modification ClickOnce manifestes.  
  
> [!NOTE]
>  Nouvelle signature est toujours la méthode recommandée pour le déploiement de nouvelles versions des applications. Si possible, utilisez cette méthode. Pour plus d’informations, consultez [Mage.exe (outil Manifest Generation and Editing)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).  
  
 Des développeurs tiers et éditeurs de logiciels indépendants peuvent s’abonner à cette fonctionnalité, facilitant ainsi à leurs clients mettre à jour leurs applications. Cette fonctionnalité peut être utilisée dans les situations suivantes :  
  
-   Lors de la mise à jour d’une application, pas pour la première installation d’une application.  
  
-   Lorsqu’il n'existe qu’une seule configuration de l’application sur un ordinateur. Par exemple, si une application est configurée pour pointer vers deux bases de données, vous ne pouvez pas utiliser cette fonctionnalité.  
  
## <a name="excluding-deploymentprovider-from-deployment-manifests"></a>Exclusion de deploymentProvider de manifestes de déploiement  
 Dans le .NET Framework 2.0 et .NET Framework 3.0, toute application ClickOnce installée sur le système pour la disponibilité hors connexion doit répertorier une `deploymentProvider` dans son manifeste de déploiement. Le `deploymentProvider` est souvent appelé à l’emplacement de la mise à jour ; il s’agit de l’emplacement où ClickOnce vérifie les mises à jour de l’application. Cette exigence, ainsi que la nécessité pour les éditeurs d’applications de signer leurs déploiements, rendait difficile pour une société de mettre à jour une application ClickOnce à partir d’un fournisseur ou d’autres tiers. Il rend également plus difficile de déployer la même application à partir de plusieurs emplacements sur le même réseau.  
  
 Les modifications qui ont été apportées à ClickOnce dans .NET Framework 3.5, il est possible pour un tiers fournir une application ClickOnce à une autre organisation, qui peut alors déployer l’application sur son propre réseau.  
  
 Pour tirer parti de cette fonctionnalité, les développeurs d’applications ClickOnce doivent exclure `deploymentProvider` à partir de leur déploiement manifestes. Cela signifie que vous devez exclure le `-providerUrl` manifestes d’argument lorsque vous créez le déploiement avec Mage.exe. Ou, si vous générez des manifestes de déploiement avec MageUI.exe, vous devez vous assurer que le **Launch Location** zone de texte sur le **manifeste d’Application** onglet est vide.  
  
## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider et mises à jour de l’Application  
 À compter de .NET Framework 3.5, vous n’est plus obligé de spécifier un `deploymentProvider` dans votre manifeste de déploiement pour déployer une application ClickOnce pour l’utilisation en ligne et hors connexion. Cette modification prend en charge le scénario où vous devez empaqueter et signer vous-même le déploiement, mais autoriser d’autres sociétés pour déployer l’application sur leurs réseaux.  
  
 Le point important à retenir est que les applications qui excluent un `deploymentProvider` Impossible de modifier leur emplacement d’installation pendant les mises à jour, jusqu'à ce qu’ils sont fournis à une mise à jour qui inclut le `deploymentProvider` à nouveau la balise.  
  
 Voici deux exemples pour préciser ce point. Dans le premier exemple, vous publiez une application ClickOnce qui n’a aucun `deploymentProvider` balise et vous demandez aux utilisateurs de l’installer à partir de http://www.adatum.com/MyApplication/. Si vous décidez de publier la prochaine mise à jour de l’application à partir de http://subdomain.adatum.com/MyApplication/, vous n’avez aucun moyen de ce qui signifie cela dans le manifeste de déploiement qui réside dans http://www.adatum.com/MyApplication/. Vous pouvez effectuer une des deux choses :  
  
-   Dites à vos utilisateurs à désinstaller la version précédente et installer la nouvelle version dans le nouvel emplacement.  
  
-   Inclure une mise à jour sur http://www.adatum.com/MyApplication/ qui inclut un `deploymentProvider` pointant vers http://www.adatum.com/MyApplication/. Ensuite, diffuser une autre mise à jour ultérieurement avec `deploymentProvider` pointant vers http://subdomain.adatum.com/MyApplication/.  
  
 Dans le deuxième exemple, vous publiez une application ClickOnce qui spécifie `deploymentProvider`, et que vous décidez de le supprimer. Une fois la nouvelle version sans `deploymentProvider` est téléchargé sur les clients, vous ne peut pas rediriger le chemin d’accès utilisé pour les mises à jour jusqu'à ce que vous publiez une version de votre application a `deploymentProvider` restaurée. Comme avec le premier exemple, `deploymentProvider` doit pointer initialement à l’emplacement actuel de la mise à jour, pas le nouvel emplacement. Dans ce cas, si vous tentez d’insérer un `deploymentProvider` qui fait référence à http://subdomain.adatum.com/MyApplication/, la prochaine mise à jour échoue.  
  
## <a name="creating-a-deployment"></a>Création d’un déploiement  
 Pour des instructions étape par étape sur la création de déploiements qui peuvent être déployés à partir de différents emplacements réseau, consultez [procédure pas à pas : déploiement manuel d’une Application ClickOnce qui est non nécessitent nouvelle signature et qui conserve les informations sur le logo](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Mage.exe (outil Manifest Generation and Editing)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [MageUI.exe (outil Manifest Generation and Editing, client graphique)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)