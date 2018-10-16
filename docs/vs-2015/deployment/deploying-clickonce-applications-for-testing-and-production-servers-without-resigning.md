---
title: Déploiement d’Applications ClickOnce pour le test et les serveurs de Production sans nouvelle signature | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 146a525394b51f71f470f1246610a855d968dddc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49180217"
---
# <a name="deploying-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Déploiement d'applications ClickOnce pour des serveurs de test et de production sans nouvelle signature
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette rubrique présente une nouvelle fonctionnalité de ClickOnce présentée dans le .NET Framework version 3.5 qui permet le déploiement d’applications ClickOnce à partir de plusieurs emplacements réseau sans nouvelle signature ni modification ClickOnce manifestes.  
  
> [!NOTE]
>  Nouvelle signature est toujours la méthode recommandée pour le déploiement de nouvelles versions d’applications. Si possible, utilisez cette méthode. Pour plus d’informations, consultez [Mage.exe (outil Manifest Generation and Editing)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1).  
  
 Les développeurs tiers et éditeurs de logiciels peuvent participer à cette fonctionnalité, ce qui facilite pour leurs clients à mettre à jour leurs applications. Cette fonctionnalité peut être utilisée dans les situations suivantes :  
  
-   Lors de la mise à jour une application, pas la première installation d’une application.  
  
-   Lorsqu’il n'existe qu’une seule configuration de l’application sur un ordinateur. Par exemple, si une application est configurée pour pointer vers les deux bases de données, vous ne pouvez pas utiliser cette fonctionnalité.  
  
## <a name="excluding-deploymentprovider-from-deployment-manifests"></a>Exclusion de deploymentProvider de manifestes de déploiement  
 Dans le .NET Framework 2.0 et .NET Framework 3.0, toute application ClickOnce installée sur le système pour la disponibilité hors connexion doit spécifier un `deploymentProvider` dans son manifeste de déploiement. Le `deploymentProvider` est souvent appelé à l’emplacement de la mise à jour ; il est l’emplacement dans lequel ClickOnce recherchera les mises à jour de l’application. Cette exigence, associée à la nécessité pour les éditeurs d’applications se connectent leurs déploiements, rendait difficile pour une entreprise mettre à jour une application ClickOnce à partir d’un fournisseur ou d’autres fournisseurs tiers. Elle rend également plus difficile à déployer la même application à partir de plusieurs emplacements sur le même réseau.  
  
 Avec les modifications qui ont été apportées à ClickOnce dans .NET Framework 3.5, il est possible pour un tiers fournir une application ClickOnce à une autre organisation, qui peut alors déployer l’application sur son propre réseau.  
  
 Pour tirer parti de cette fonctionnalité, les développeurs d’applications ClickOnce doivent exclure `deploymentProvider` à partir de leur déploiement manifestes. Cela signifie exclure le `-providerUrl` manifestes d’argument lorsque vous créez le déploiement avec Mage.exe, ou s’assurer que le **lancer un emplacement** zone de texte sur le **manifeste d’Application** onglet est vide si vous Générez des manifestes de déploiement avec MageUI.exe.  
  
## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider et mises à jour de l’Application  
 À compter de .NET Framework 3.5, vous n’est plus obligé de spécifier un `deploymentProvider` dans votre manifeste de déploiement pour déployer une application ClickOnce pour l’utilisation en ligne et hors connexion. Cela prend en charge le scénario où vous devez empaqueter et signer vous-même le déploiement, mais autoriser d’autres entreprises déployer l’application sur leurs réseaux.  
  
 Le point clé à retenir est que les applications qui excluent un `deploymentProvider` Impossible de modifier leur emplacement d’installation pendant les mises à jour, jusqu'à ce qu’elles sont fournies dans une mise à jour qui inclut le `deploymentProvider` baliser à nouveau.  
  
 Voici deux exemples pour clarifier ce point. Dans le premier exemple, vous publiez une application ClickOnce qui n’a aucun `deploymentProvider` balise et vous demandez aux utilisateurs d’installer à partir http://www.adatum.com/MyApplication/. Si vous décidez de publier la prochaine mise à jour de l’application à partir de http://subdomain.adatum.com/MyApplication/, vous n’avez aucun moyen de ce qui signifie dans le manifeste de déploiement qui se trouve dans http://www.adatum.com/MyApplication/. Vous pouvez effectuer une des deux opérations :  
  
-   Indiquer à vos utilisateurs pour désinstaller la version précédente et installer la nouvelle version à partir du nouvel emplacement.  
  
-   Inclure une mise à jour sur http://www.adatum.com/MyApplication/ qui inclut un `deploymentProvider` pointant vers http://www.adatum.com/MyApplication/. Relâchez une autre mise à jour plus tard avec `deploymentProvider` pointant vers http://subdomain.adatum.com/MyApplication/.  
  
 Dans le deuxième exemple, vous publiez une application ClickOnce qui spécifie `deploymentProvider`, et vous décidez ensuite de le supprimer. Une fois la nouvelle version sans `deploymentProvider` a été téléchargée aux clients, vous ne pourrez pas rediriger le chemin d’accès utilisé pour les mises à jour jusqu'à ce que vous publiez une version de votre application a `deploymentProvider` restauré. Comme avec le premier exemple, `deploymentProvider` doit pointer initialement à l’emplacement actuel de la mise à jour, pas votre nouvel emplacement. Dans ce cas, si vous tentez d’insérer un `deploymentProvider` qui fait référence à http://subdomain.adatum.com/MyApplication/, la prochaine mise à jour échoue.  
  
## <a name="creating-a-deployment"></a>Création d’un déploiement  
 Pour obtenir des instructions étape par étape sur la création de déploiements qui peuvent être déployés à partir de différents emplacements réseau, consultez [procédure pas à pas : déploiement manuel d’une Application ClickOnce qui est pas exiger nouvelle signature et qui conserve les informations sur le logo](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Mage.exe (outil Manifest Generation and Editing)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI.exe (outil Manifest Generation and Editing, client graphique)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)



