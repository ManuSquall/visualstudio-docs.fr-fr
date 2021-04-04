---
title: Mises à jour automatiques des applications à l’aide de l’API de déploiement ClickOnce
description: Apprenez à écrire du code dans ClickOnce qui utilise la classe ApplicationDeployment pour rechercher les mises à jour en fonction d’un événement, tel qu’une demande de l’utilisateur.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: db82151b7fd4dbe894cecf8fbf5f5b64cb2f5919
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106213938"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>Guide pratique pour vérifier la disponibilité de mises à jour des applications par programmation à l’aide de l’API du déploiement ClickOnce
ClickOnce offre deux moyens de mettre à jour une application une fois qu’elle est déployée. Dans la première méthode, vous pouvez configurer le déploiement ClickOnce pour vérifier automatiquement les mises à jour à certains intervalles. Dans la deuxième méthode, vous pouvez écrire du code qui utilise la <xref:System.Deployment.Application.ApplicationDeployment> classe pour rechercher les mises à jour en fonction d’un événement, tel qu’une demande de l’utilisateur.

 Les procédures suivantes montrent du code pour effectuer une mise à jour par programmation et décrivent également comment configurer votre déploiement ClickOnce pour activer les vérifications de mise à jour par programmation.

 Pour mettre à jour une application ClickOnce par programme, vous devez spécifier un emplacement pour les mises à jour. On parle parfois de fournisseur de déploiement. Pour plus d’informations sur la définition de cette propriété, consultez [choisir une stratégie de mise à jour ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).

> [!NOTE]
> Vous pouvez également utiliser la technique décrite ci-dessous pour déployer votre application à partir d’un emplacement, mais la mettre à jour à partir d’une autre. Pour plus d’informations, consultez [Comment : spécifier un autre emplacement pour les mises à jour de déploiement](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md).

### <a name="to-check-for-updates-programmatically"></a>Pour rechercher des mises à jour par programmation

1. Créez une application Windows Forms à l’aide de vos outils en ligne de commande ou visuels préférés.

2. Créez le bouton, l’élément de menu ou tout autre élément d’interface utilisateur que vous souhaitez que vos utilisateurs sélectionnent pour rechercher les mises à jour. À partir du gestionnaire d’événements de cet élément, appelez la méthode suivante pour rechercher et installer les mises à jour.

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnceAPI/CS/Form1.cs" id="Snippet6":::
    :::code language="cpp" source="../snippets/cpp/VS_Snippets_Winforms/ClickOnceAPI/cpp/form1.cpp" id="Snippet6":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceAPI/VB/Form1.vb" id="Snippet6":::

3. Compilez votre application.

### <a name="use-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Utiliser Mage.exe pour déployer une application qui recherche des mises à jour par programmation

- Suivez les instructions de déploiement de votre application à l’aide de Mage.exe, comme expliqué dans [procédure pas à pas : déployer manuellement une application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Quand vous appelez Mage.exe pour générer le manifeste de déploiement, assurez-vous d’utiliser le commutateur de ligne de commande `providerUrl` et de spécifier l’URL à laquelle ClickOnce doit rechercher les mises à jour. Si votre application effectue une mise à jour à partir de `http://www.adatum.com/MyApp` , par exemple, votre appel pour générer le manifeste de déploiement peut se présenter comme suit :

    ```cmd
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application
    ```

### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Utilisation de MageUI.exe pour déployer une application qui recherche des mises à jour par programmation

- Suivez les instructions de déploiement de votre application à l’aide de Mage.exe, comme expliqué dans [procédure pas à pas : déployer manuellement une application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Sous l’onglet **options de déploiement** , définissez le champ emplacement de **départ** sur le manifeste d’application ClickOnce doit vérifier les mises à jour. Sous l’onglet **options de mise à jour** , désactivez la case à cocher **cette application doit vérifier les mises à jour** .

## <a name="net-framework-security"></a>Sécurité du .NET Framework
 Votre application doit avoir des autorisations de confiance totale pour utiliser la mise à jour par programmation.

## <a name="see-also"></a>Voir aussi
- [Procédure : spécifier un autre emplacement pour les mises à jour du déploiement](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)
- [Choisir une stratégie de mise à jour ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Publier des applications ClickOnce](../deployment/publishing-clickonce-applications.md)