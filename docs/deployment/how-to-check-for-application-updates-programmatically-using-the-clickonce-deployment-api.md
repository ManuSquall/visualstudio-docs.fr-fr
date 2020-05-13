---
title: Mises à jour automatiques de l’application à l’aide de ClickOnce déploiement API
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- application updates
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9300fbf8b348b1016d36d414d17a66c45f6494b9
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444615"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>Guide pratique pour vérifier la disponibilité de mises à jour des applications par programmation à l’aide de l’API du déploiement ClickOnce
ClickOnce fournit deux façons de mettre à jour une application une fois qu’elle est déployée. Dans la première méthode, vous pouvez configurer le déploiement ClickOnce pour vérifier automatiquement les mises à jour à certains intervalles. Dans la deuxième méthode, vous pouvez <xref:System.Deployment.Application.ApplicationDeployment> écrire du code qui utilise la classe pour vérifier les mises à jour basées sur un événement, comme une demande d’utilisateur.

 Les procédures suivantes affichent un certain code pour effectuer une mise à jour programmatique et décrivent également comment configurer votre déploiement ClickOnce pour activer les vérifications de mise à jour programmatiques.

 Afin de mettre à jour une application ClickOnce programmatiquement, vous devez spécifier un emplacement pour les mises à jour. C’est ce qu’on appelle parfois un fournisseur de déploiement. Pour plus d’informations sur la configuration de cette propriété, voir [Choisissez une stratégie de mise à jour ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).

> [!NOTE]
> Vous pouvez également utiliser la technique décrite ci-dessous pour déployer votre application à partir d’un endroit, mais la mettre à jour à partir d’un autre. Pour plus d’informations, voir [Comment : Spécifier un autre emplacement pour les mises à jour de déploiement](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md).

### <a name="to-check-for-updates-programmatically"></a>Pour vérifier les mises à jour programmatiques

1. Créez une nouvelle application Windows Forms à l’aide de votre ligne de commande ou d’outils visuels préférés.

2. Créez n’importe quel bouton, élément de menu ou autre élément d’interface utilisateur que vous souhaitez que vos utilisateurs choisissent pour vérifier les mises à jour. À partir du gestionnaire d’événements de cet élément, appelez la méthode suivante pour vérifier et installer des mises à jour.

     [!code-csharp[ClickOnceAPI#6](../deployment/codesnippet/CSharp/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cs)]
     [!code-cpp[ClickOnceAPI#6](../deployment/codesnippet/CPP/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cpp)]
     [!code-vb[ClickOnceAPI#6](../deployment/codesnippet/VisualBasic/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.vb)]

3. Compilez votre demande.

### <a name="use-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Utilisez Mage.exe pour déployer une application qui vérifie les mises à jour programmatiques

- Suivez les instructions pour le déploiement de votre application à l’aide de Mage.exe comme expliqué dans [Pas à pas : déployez manuellement une application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Lorsque vous appelez Mage.exe pour générer le manifeste de `providerUrl`déploiement, assurez-vous d’utiliser l’interrupteur de ligne de commande, et de spécifier l’URL où ClickOnce devrait vérifier les mises à jour. Si votre application `http://www.adatum.com/MyApp`sera mise à jour à partir, par exemple, votre appel pour générer le manifeste de déploiement peut ressembler à ceci:

    ```cmd
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application
    ```

### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Utilisation de MageUI.exe pour déployer une application qui vérifie les mises à jour programmatiques

- Suivez les instructions pour le déploiement de votre application à l’aide de Mage.exe comme expliqué dans [Pas à pas : déployez manuellement une application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Sur l’onglet **Options de déploiement,** définissez le champ **de localisation de démarrage** sur le manifeste de l’application ClickOnce pour vérifier les mises à jour. Sur l’onglet **Options de mise à jour,** effacez **l’application This devrait vérifier les mises à jour** de la case à cocher.

## <a name="net-framework-security"></a>Sécurité du .NET Framework
 Votre demande doit avoir des autorisations pleine confiance pour utiliser la mise à jour programmatique.

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour spécifier un autre emplacement pour les mises à jour du déploiement](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)
- [Choisir une stratégie de mise à jour ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Publier des applications ClickOnce](../deployment/publishing-clickonce-applications.md)