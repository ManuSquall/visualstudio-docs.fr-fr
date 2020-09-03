---
title: Déploiement d’applications ClickOnce pour des serveurs de test et de production sans resignature | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a8e41e67d5e2800acc41e1220fe632001420a274
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80395373"
---
# <a name="deploying-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Déploiement d'applications ClickOnce pour des serveurs de test et de production sans nouvelle signature
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette rubrique décrit une nouvelle fonctionnalité de ClickOnce introduite dans la version 3,5 de .NET Framework qui permet le déploiement d’applications ClickOnce à partir de plusieurs emplacements réseau sans avoir à resigner ou modifier les manifestes ClickOnce.  
  
> [!NOTE]
> La reconnexion est toujours la méthode recommandée pour déployer de nouvelles versions d’applications. Dans la mesure du possible, utilisez la méthode de resignature. Pour plus d’informations, consultez [Mage.exe (outil Manifest Generation and Editing)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1).  
  
 Les développeurs tiers et les éditeurs de logiciels indépendants peuvent s’abonner à cette fonctionnalité, ce qui permet aux clients de mettre à jour leurs applications plus facilement. Cette fonctionnalité peut être utilisée dans les situations suivantes :  
  
- Lors de la mise à jour d’une application, et non de la première installation d’une application.  
  
- Lorsqu’il n’existe qu’une seule configuration de l’application sur un ordinateur. Par exemple, si une application est configurée pour pointer vers deux bases de données différentes, vous ne pouvez pas utiliser cette fonctionnalité.  
  
## <a name="excluding-deploymentprovider-from-deployment-manifests"></a>Exclusion de deploymentProvider des manifestes de déploiement  
 Dans les .NET Framework 2,0 et .NET Framework 3,0, toute application ClickOnce installée sur le système pour la disponibilité hors connexion doit spécifier un `deploymentProvider` dans son manifeste de déploiement. `deploymentProvider`Est souvent désigné comme l’emplacement de la mise à jour ; il s’agit de l’emplacement dans lequel ClickOnce recherche les mises à jour d’application. Cette exigence, couplée à la nécessité pour les éditeurs d’applications de signer leurs déploiements, a rendu difficile pour une entreprise de mettre à jour une application ClickOnce auprès d’un fournisseur ou d’un tiers. Il est également plus difficile de déployer la même application à partir de plusieurs emplacements sur le même réseau.  
  
 Avec les modifications apportées à ClickOnce dans le .NET Framework 3,5, il est possible pour un tiers de fournir une application ClickOnce à une autre organisation, qui peut ensuite déployer l’application sur son propre réseau.  
  
 Pour tirer parti de cette fonctionnalité, les développeurs d’applications ClickOnce doivent exclure `deploymentProvider` de leurs manifestes de déploiement. Cela signifie que vous excluez l' `-providerUrl` argument lorsque vous créez des manifestes de déploiement avec Mage.exe, ou que la zone de texte **emplacement de lancement** sous l’onglet manifeste de l' **application** est vide si vous générez des manifestes de déploiement avec MageUI.exe.  
  
## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider et mises à jour d’application  
 À partir de la .NET Framework 3,5, vous n’avez plus besoin de spécifier un `deploymentProvider` dans votre manifeste de déploiement pour déployer une application ClickOnce pour l’utilisation en ligne et hors connexion. Cela prend en charge le scénario dans lequel vous devez empaqueter et signer le déploiement vous-même, tout en permettant à d’autres entreprises de déployer l’application sur leurs réseaux.  
  
 Le point essentiel à retenir est que les applications qui excluent un `deploymentProvider` ne peuvent pas modifier leur emplacement d’installation lors des mises à jour, jusqu’à ce qu’elles livrent à nouveau une mise à jour incluant la `deploymentProvider` balise.  
  
 Voici deux exemples pour clarifier ce point. Dans le premier exemple, vous publiez une application ClickOnce qui n’a pas de `deploymentProvider` balise, et vous demandez aux utilisateurs de l’installer à partir de `http://www.adatum.com/MyApplication/` . Si vous décidez de publier la prochaine mise à jour de l’application à partir de `http://subdomain.adatum.com/MyApplication/` , vous n’avez aucun moyen de le signaler dans le manifeste de déploiement qui réside dans `http://www.adatum.com/MyApplication/` . Vous pouvez effectuer l’une des deux opérations suivantes :  
  
- Demandez à vos utilisateurs de désinstaller la version précédente et d’installer la nouvelle version à partir du nouvel emplacement.  
  
- Incluez une mise à jour sur `http://www.adatum.com/MyApplication/` qui inclut un `deploymentProvider` pointant vers `http://www.adatum.com/MyApplication/` . Ensuite, publiez une autre mise à jour ultérieurement en `deploymentProvider` pointant sur `http://subdomain.adatum.com/MyApplication/` .  
  
  Dans le deuxième exemple, vous publiez une application ClickOnce qui spécifie `deploymentProvider` et vous décidez ensuite de la supprimer. Une fois que la nouvelle version n' `deploymentProvider` a pas été téléchargée sur les clients, vous ne pourrez pas rediriger le chemin d’accès utilisé pour les mises à jour tant que vous n’aurez pas libéré une version de votre application qui a été `deploymentProvider` restaurée. Comme dans le premier exemple, `deploymentProvider` doit pointer initialement sur l’emplacement de mise à jour actuel, et non sur votre nouvel emplacement. Dans ce cas, si vous tentez d’insérer un `deploymentProvider` qui fait référence à `http://subdomain.adatum.com/MyApplication/` , la mise à jour suivante échouera.  
  
## <a name="creating-a-deployment"></a>Création d’un déploiement  
 Pour obtenir des instructions pas à pas sur la création de déploiements pouvant être déployés à partir de différents emplacements réseau, consultez [procédure pas à pas : déploiement manuel d’une application ClickOnce qui ne nécessite pas de nouvelle signature et qui conserve les informations de personnalisation](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required?view=vs-2015).  
  
## <a name="see-also"></a>Voir aussi  
 [Mage.exe (Outil Manifest Generation and Editing)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI.exe (Outil Manifest Generation and Editing, client graphique)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)
