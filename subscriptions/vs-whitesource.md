---
title: Avantage WhiteSource Bolt
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 10/3/2017
Ms.topic: Get-Started-Article
Description: Learn how to activate the WhiteSource Bolt subscription included with your Visual Studio subscription.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: e8b5e08178ac35e57350052e6a9076dc0f80dca6
ms.sourcegitcommit: b7d3b90d0be597c9d01879338dd2678c881087ce
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
#  <a name="activating-the-whitesource-bolt-benefit-in-visual-studio-subscriptions"></a>Activation de l’avantage WhiteSource Bolt dans les abonnements Visual Studio

Détectez et corrigez les vulnérabilités open source, puis générez des rapports complets d’inventaire et de licence pour l’ensemble des composants open source de votre build.  Votre abonnement Enterprise inclut un abonnement gratuit de six mois. 

1.  Pour utiliser votre avantage WhiteSource Bolt, cliquez sur le lien **Obtenir un code** en bas de la vignette de l’avantage.    

    ![Vignette de l’avantage WhiteSource](_img\vs-whitesource\vs-whitesource-tile.png)

2.  Vous recevez une notification contenant votre code d’activation.  **Copiez le code dans votre Presse-papiers**, puis cliquez sur **Activer**. 

    ![Code de l’avantage WhiteSource ](_img\vs-whitesource\vs-whitesource-code.png)

3.  Dans la page web WhiteSource, cliquez sur le bouton **Activer** ou faites défiler la page jusqu’à la section **Activer votre compte**.  

    ![Activer l’avantage WhiteSource](_img\vs-whitesource\vs-whitesource-activate-page-cropped.png)

4.  Dans la section **Activer votre compte** de la page, vous êtes guidé pas à pas pour effectuer quatre étapes :
- [Installez](https://marketplace.visualstudio.com/items?itemName=whitesource.ws-bolt) l’extension WhiteSource Bolt à partir de Microsoft Visual Studio Marketplace. Si vous n’êtes pas autorisé à installer les extensions, consultez [cette page](https://www.visualstudio.com/en-us/docs/marketplace/get-vsts-extensions#request).

    Cliquez sur le bouton vert **Installer** si vous utilisez VSTS, ou sur le bouton **Télécharger** si vous utilisez Team Foundation Server.  Dans cet exemple, nous allons utiliser VSTS. 

    ![Avantage WhiteSource, Installer l’extension](_img\vs-whitesource\vs-whitesource-download-install.png)

- Ensuite, sélectionnez le compte VSTS à utiliser et cliquez sur **Confirmer**.  (Si vous n’avez pas encore installé VSTS, consultez la page [Avantages](https://my.visualstudio.com/benefits) et activez votre avantage VSTS.)

    ![Avantage WhiteSource, Confirmer le compte](_img\vs-whitesource\vs-whitesource-confirm-account.png)

- Vous recevez une confirmation indiquant que l’extension est installée et prête à être utilisée.  Cliquez sur **Démarrer** pour revenir à la page WhiteSource Bolt et continuer.  

    ![Avantage WhiteSource, Installation terminée](_img\vs-whitesource\vs-whitesource-install-complete.png)

5.  Ouvrez votre tableau de bord de projet Visual Studio Team Services (VSTS), cliquez dans le menu **Build et mise en production** et choisissez **WhiteSource Bolt**.

    ![Avantage WhiteSource, Ajouter l’extension](_img\vs-whitesource\vs-whitesource-installed-cropped.png)

6. Collez le code d’activation de la vignette de l’avantage WhiteSource Bolt, puis cliquez sur **Activer**. Chaque code d’activation fourni vous permet d’activer un seul projet. 

    ![Avantage WhiteSource, Code d’activation](_img\vs-whitesource\vs-whitesource-activate-code-cropped.png)

7.  Votre avantage est maintenant activé pour une durée de 180 jours restants dans votre abonnement. 
8.  Vous devez ensuite ajouter l’extension WhiteSource Bolt comme l’une de vos étapes de build.  Une vidéo disponible dans la [page WhiteSource Bolt](https://www.whitesourcesoftware.com/whitesource_bolt_visualstudio_2017/#activate) vous montre comment faire.  
9. Une fois que vous avez exécuté votre build, les rapports et tableaux de bord complets suivants sont automatiquement générés :
- Tableau de bord des failles de sécurité
- Rapport des failles de sécurité
- Rapport des bibliothèques obsolètes
- Tableau de bord des risques et de la conformité des licences
- Rapport d’inventaire
