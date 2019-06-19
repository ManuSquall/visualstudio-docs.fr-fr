---
title: Avantage WhiteSource Bolt | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 12/19/2018
ms.topic: conceptual
description: Découvrez comment activer l’abonnement WhiteSource Bolt inclus dans votre abonnement Visual Studio.
searchscope: VS Subscription
ms.openlocfilehash: 773284a163004958dbf89aea871414105792b338
ms.sourcegitcommit: 91c7f1b525e0c22d938bc4080ba4ceac2483474f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67031933"
---
# <a name="whitesource-bolt-in-visual-studio-subscriptions"></a>WhiteSource Bolt dans les abonnements Visual Studio

Détectez et corrigez les vulnérabilités open source, puis générez des rapports complets d’inventaire et de licence pour l’ensemble des composants open source de votre build. Certains abonnements Visual Studio incluent un accès gratuit pendant six mois.

## <a name="activation-steps"></a>Étapes d’activation

1. Pour activer votre avantage WhiteSource Bolt, connectez-vous à [https://my.visualstudio.com/benefits](https://my.visualstudio.com/benefits?wt.mc_id=o~msft~docs).

2. Recherchez la vignette WhiteSource Bolt dans la section Outils et cliquez sur le lien **Obtenir le code** en bas de la vignette de l’avantage.
   > [!div class="mx-imgBorder"]
   > ![Vignette de l’avantage WhiteSource](_img/vs-whitesource/vs-whitesource-tile.png)

3. Vous recevez une notification contenant votre code d’activation.  **Copiez le code dans votre Presse-papiers**, puis cliquez sur **Activer**.
   > [!div class="mx-imgBorder"]
   > ![Code de l’avantage WhiteSource](_img/vs-whitesource/vs-whitesource-code.png)

4. Dans la page web WhiteSource, cliquez sur le bouton **Activer** ou faites défiler la page jusqu’à la section **Activer votre compte**.
   > [!div class="mx-imgBorder"]
   > ![Activer l’avantage WhiteSource](_img/vs-whitesource/vs-whitesource-activate-page-cropped.png)

5. Dans la section **Activer votre compte** de la page, vous êtes guidé pas à pas pour effectuer quatre étapes :

   - [Installez](https://marketplace.visualstudio.com/items?itemName=whitesource.ws-bolt) l’extension WhiteSource Bolt à partir de Microsoft Visual Studio Marketplace. Si vous n’êtes pas autorisé à installer des extensions, consultez [Installer des extensions gratuites pour Azure DevOps Services](/azure/devops/marketplace/install-vsts-extension?view=vsts).

Cliquez sur le bouton vert **Installer** si vous utilisez Azure DevOps Services, ou sur le bouton **Télécharger** si vous utilisez Team Foundation Server.  Pour cet exemple, nous allons utiliser Azure DevOps Services.
> [!div class="mx-imgBorder"]
> ![Avantage WhiteSource, Installer l’extension](_img/vs-whitesource/vs-whitesource-download-install.png)

- Ensuite, sélectionnez l’organisation Azure DevOps que vous souhaitez utiliser et cliquez sur **Confirmer**.  (Si vous n’avez pas encore configuré Azure DevOps Services, visitez la page [Avantages](https://my.visualstudio.com/benefits) et activez votre avantage Azure DevOps Services.)

> [!div class="mx-imgBorder"]
> ![Avantage WhiteSource, Confirmer le compte](_img/vs-whitesource/vs-whitesource-confirm-account.png)

- Vous recevez une confirmation indiquant que l’extension est installée et prête à être utilisée.  Cliquez sur **Démarrer** pour revenir à la page WhiteSource Bolt et continuer.
> [!div class="mx-imgBorder"]
> ![Avantage WhiteSource, Installation effectuée](_img/vs-whitesource/vs-whitesource-install-complete.png)

5. Ouvrez votre tableau de bord de projet Azure DevOps, cliquez sur le menu **Azure Pipelines** et choisissez **WhiteSource Bolt**.
   > [!div class="mx-imgBorder"]
   > ![Avantage WhiteSource, Ajouter l’extension](_img/vs-whitesource/vs-whitesource-installed-cropped.png)

6. Collez le code d’activation de la vignette de l’avantage WhiteSource Bolt, puis cliquez sur **Activer**. Chaque code d’activation fourni vous permet d’activer un seul projet.
   > [!div class="mx-imgBorder"]
   > ![Avantage WhiteSource, Code d’activation](_img/vs-whitesource/vs-whitesource-activate-code-cropped.png)

7. Votre avantage est maintenant activé pour une durée de 180 jours restants dans votre abonnement.

8. Vous devez ensuite ajouter l’extension WhiteSource Bolt comme l’une de vos étapes de build.  Une vidéo disponible dans la [page WhiteSource Bolt](https://www.whitesourcesoftware.com/whitesource_bolt_visualstudio_2017/#activate) vous montre comment faire.

9. Une fois que vous avez exécuté votre build, les rapports et tableaux de bord complets suivants sont automatiquement générés :
    - Tableau de bord des failles de sécurité
    - Rapport des failles de sécurité
    - Rapport des bibliothèques obsolètes
    - Tableau de bord des risques et de la conformité des licences
    - Rapport d’inventaire

## <a name="eligibility"></a>Éligibilité

| Niveau d'abonnement                                                 |     Canaux                                            | Avantage                                                          | Renouvelable ?    |
|--------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------------|---------------|
| Visual Studio Enterprise (Standard)   | Licences en volume, Azure, Détail, NFR sélectif<sup>1</sup> | 6 mois       |  Oui          |
| Visual Studio Professional (Standard) | Licences en volume, Azure, Détail                                       | Non disponible                                                           |NA         |
| Visual Studio Test Professional (Standard)                         | Licences en volume, Détail                                              | Non disponible                                             |  NA         |
| Plateformes MSDN (Standard)                                          | Licences en volume, Détail                                              | Non disponible                                              | NA         |
| Visual Studio Enterprise, Visual Studio Professional (cloud mensuel) | Azure                                       | Non disponible                                                           |NA|
||

<sup>1</sup>  *Inclut :  Microsoft Partner Network (Enterprise).  Exclut : autres NFR (revente interdite), VSIP (Visual Studio Industry Partner), FTE, MCT Software & Services Developer, BizSpark, Imagine, MVP (Most Valuable Professional), RD (Regional Director), MCT Software & Services, Microsoft Partner Network (Professional).*

> [!NOTE]
> Microsoft ne propose plus d’abonnements annuels Visual Studio Professional et Visual Studio Enterprise dans les abonnements cloud. L’expérience des clients n’en sera pas altérée ; il leur sera par ailleurs toujours possible de renouveler, d’augmenter, de diminuer ou d’annuler leur abonnement. Nous encourageons les nouveaux clients à accéder à [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) pour explorer les différentes options d’achat de Visual Studio.

Vous n’êtes pas sûr de l’abonnement que vous utilisez ?  Connectez-vous à [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) pour voir tous les abonnements attribués à votre adresse e-mail. Si vous ne retrouvez pas tous vos abonnements, certains ont peut-être été attribués à une autre adresse e-mail.  Dans ce cas, vous devez vous connecter via l’adresse e-mail correspondante pour afficher ces abonnements.

## <a name="support-resources"></a>Ressources de support

- Besoin d’aide avec WhiteSource Bolt ?  Conversez en direct avec un représentant WhiteSource Bolt sur https://www.whitesourcesoftware.com/vse_whitesource_bolt/
- Pour obtenir de l’aide concernant les ventes, les abonnements, les comptes et la facturation des abonnements Visual Studio, contactez le [support des abonnements](https://visualstudio.microsoft.com/subscriptions/support/) Visual Studio.
- Vous avez des questions concernant l’IDE Visual Studio, Azure DevOps Services, ou d’autres produits ou services Visual Studio ?  Consultez le [support Visual Studio](https://visualstudio.microsoft.com/support/).