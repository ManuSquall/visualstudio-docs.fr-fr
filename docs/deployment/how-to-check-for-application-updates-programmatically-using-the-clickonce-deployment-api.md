---
title: "Comment : rechercher les mises à jour de l’Application par programme à l’aide de l’API du déploiement ClickOnce | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- application updates
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
caps.latest.revision: "9"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 9b240bcdcc576e7ace85e766b54e5cd70e4e5503
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>Comment : vérifier la disponibilité de mises à jour des applications par programme à l'aide de l'API du déploiement ClickOnce
ClickOnce fournit deux façons de mettre à jour une application après son déploiement. Dans la première méthode, vous pouvez configurer le déploiement ClickOnce pour vérifier automatiquement les mises à jour à intervalles réguliers. Dans la deuxième méthode, vous pouvez écrire du code qui utilise le <xref:System.Deployment.Application.ApplicationDeployment> classe pour rechercher les mises à jour basée sur un événement, telle qu’une demande de l’utilisateur.  
  
 Les procédures suivantes affichent du code pour effectuer une mise à jour par programmation et décrivent également comment configurer votre déploiement de ClickOnce pour activer les vérifications de la mise à jour par programmation.  
  
 Pour mettre à jour une application ClickOnce par programme, vous devez spécifier un emplacement pour les mises à jour. Cela est parfois en tant que fournisseur de déploiement. Pour plus d’informations sur la définition de cette propriété, consultez [choix d’une stratégie de mise à jour ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
> [!NOTE]
>  Vous pouvez également utiliser la technique décrite ci-dessous pour déployer votre application à partir d’un emplacement, mais mettre à jour à partir d’un autre. Pour plus d’informations, consultez [Comment : spécifier un autre emplacement pour le déploiement des mises à jour](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md).  
  
### <a name="to-check-for-updates-programmatically"></a>Pour vérifier les mises à jour par programme  
  
1.  Créer une nouvelle application Windows Forms à l’aide de vos outils de ligne de commande ou visual préférés.  
  
2.  Créer le bouton, l’élément de menu, ou autre élément d’interface utilisateur vous permet de vérifier les mises à jour à vos utilisateurs. À partir du Gestionnaire d’événements de cet élément, appelez la méthode suivante pour vérifier et installer les mises à jour.  
  
     [!code-csharp[ClickOnceAPI#6](../deployment/codesnippet/CSharp/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cs)]
     [!code-cpp[ClickOnceAPI#6](../deployment/codesnippet/CPP/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cpp)]
     [!code-vb[ClickOnceAPI#6](../deployment/codesnippet/VisualBasic/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.vb)]  
  
3.  Compilez votre application.  
  
### <a name="using-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>À l’aide de Mage.exe pour déployer une application qui vérifie les mises à jour par programme  
  
-   Suivez les instructions pour le déploiement de votre application à l’aide de Mage.exe comme expliqué dans [procédure pas à pas : déploiement manuel d’une Application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Lorsque vous appelez Mage.exe pour générer le manifeste de déploiement, assurez-vous d’utiliser le commutateur de ligne de commande `providerUrl`et pour spécifier l’URL où ClickOnce doit rechercher des mises à jour. Si votre application met à jour à partir de [http://www.adatum.com/MyApp](http://www.adatum.com/MyApp), par exemple, votre appel pour générer le manifeste de déploiement peut se présenter comme suit :  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application  
    ```  
  
### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>À l’aide de MageUI.exe pour déployer une application qui vérifie les mises à jour par programme  
  
-   Suivez les instructions pour le déploiement de votre application à l’aide de Mage.exe comme expliqué dans [procédure pas à pas : déploiement manuel d’une Application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Sur le **Options de déploiement** onglet, définissez la **Start Location** champ au manifeste d’application ClickOnce doit rechercher des mises à jour. Sur le **les Options de mise à jour** onglet, désactivez le **cette application doit rechercher des mises à jour** case à cocher.  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Votre application doit avoir des autorisations de confiance totale pour utiliser la mise à jour par programmation.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : spécifier un autre emplacement pour le déploiement des mises à jour](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)   
 [Choix d’une stratégie de mise à jour ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md)