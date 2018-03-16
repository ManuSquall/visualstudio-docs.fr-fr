---
title: "Configuration d’un dépôt Git dans Visual Studio pour Mac | Microsoft Docs"
description: Utilisation de Git et de Subversion dans Visual Studio pour Mac.
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: E992FA1D-B2AD-4A28-ADC6-47E4FC471060
ms.openlocfilehash: a8e32df2248f53a2b46a971b025b1138abba5101
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2018
---
# <a name="setting-up-a-git-repository"></a>Configuration d’un dépôt Git

Git est un système de gestion de versions distribué qui permet aux équipes de travailler simultanément sur les mêmes documents. Cela signifie qu’il existe un seul serveur contenant tous les fichiers, mais que quand un dépôt est extrait de cette source centrale, l’intégralité du dépôt est cloné localement sur votre machine.

Il existe de nombreux hôtes distants qui vous permettent de travailler avec Git pour la gestion de versions, mais le plus répandu est GitHub. L’exemple ci-dessous utilise un hôte GitHub, mais vous pouvez utiliser n’importe quel hôte Git pour la gestion de versions dans Visual Studio pour Mac.

Si vous voulez utiliser GitHub, veillez à disposer d’un compte créé et configuré avant de suivre les étapes dans cet article. 

## <a name="creating-a-remote-repo-on-github"></a>Création d’un dépôt distant sur GitHub

L’exemple ci-dessous utilise un hôte GitHub, mais vous pouvez utiliser n’importe quel hôte Git pour la gestion de versions dans Visual Studio pour Mac.

Pour configurer un dépôt Git, effectuez les étapes suivantes :

1. Créez un nouveau dépôt Git sur github.com :

    ![Créer un dépôt Git](media/version-control-git1-sml.png)

2. Définissez le nom, la description et la confidentialité du dépôt. N’initialisez **pas** le dépôt. Définissez .gitignore et la licence sur None :

    ![Définir les détails du dépôt Git](media/version-control-git2.png)

3. La page suivante vous permet de choisir d’afficher et de copier l’adresse HTTPS ou SSH vers le dépôt que vous avez créé :

    ![afficher et copier l’adresse](media/version-control-git3.png)

  Vous avez besoin de l’adresse HTTPS pour faire pointer Visual Studio pour Mac vers ce dépôt.


## <a name="publishing-an-existing-project"></a>Publication d’un projet existant

4. Revenez à votre projet ouvert dans Visual Studio pour Mac. 

5. Dans la barre de menus, sélectionnez **Gestion de version > Publier dans la gestion de version...** pour afficher la boîte de dialogue **Sélectionner un dépôt** :

    ![Démarrer l’extraction dans Visual Studio pour Mac](media/version-control-git4-sml.png)

6. Choisissez l’onglet **Dépôts inscrits** et cliquez sur le bouton **Ajouter** :

    ![](media/version-control-git5.png)

7. Entrez le nom du dépôt à afficher localement et collez l’URL de l’étape 3. La boîte de dialogue de configuration de votre dépôt doit être similaire à ceci. Cliquez sur OK : 

    ![Boîte de dialogue Entrer les détails git](media/version-control-git6.png)

    Notez qu’il est également possible d’utiliser le protocole SSH pour se connecter à Git.

8. Pour tenter de publier l’application sur Git, sélectionnez le dépôt et vérifiez que les deux champs texte **Nom du module** et **Message** sont renseignés :

    ![Essayer de publier le projet sur Git](media/version-control-git7.png)

9. Cliquez sur **OK** puis sur **Publier** dans la boîte de dialogue d’alerte.

10. Si vous n’avez pas déjà entré vos informations d’identification Git dans les préférences de Visual Studio pour Mac, entrez-les maintenant. Vous devez d’abord créer un jeton d’accès, qui est utilisé à la place d’un mot de passe. Si vous n’avez pas créé de jeton d’accès, suivez les étapes décrites dans la documentation Git [Jeton d’accès](https://help.github.com/articles/creating-an-access-token-for-command-line-use/).

11. Entrez le nom d’utilisateur et le jeton d’accès personnel, puis cliquez sur **OK** :

    ![Entrer un nom d’utilisateur et un mot de passe pour Git](media/version-control-git9-sml.png)

12. Après quelques secondes, la solution doit être publiée avec sa validation initiale. Vérifiez que c’est bien le cas en examinant l’élément de menu Gestion de version, qui doit maintenant contenir de nombreuses options : 

    ![Menu Gestion de version](media/version-control-git10.png)

13. Une fois que vous commencez à faire d’autres modifications, sélectionnez **Publier les modifications...** pour envoyer (push) les modifications au dépôt **distant**. Ceci permet à tous les utilisateurs appropriés de les voir sur github.com : 

    ![Envoyer (push) des modifications sur un dépôt distant](media/version-control-git11.png)

## <a name="publishing-a-new-project"></a>Publication d’un nouveau projet

La boîte de dialogue Nouveau projet peut être utilisé pour publier un nouveau projet en utilisant Git. Pour l’activer, cochez la case **Utiliser Git pour la gestion de version**, comme illustré dans la capture d’écran suivante. Ceci initialise votre dépôt et ajoute un fichier .gitignore facultatif :

![Envoyer (push) des modifications sur un dépôt distant](media/version-control-git12.png)

## <a name="checkout-an-existing-repository"></a>Extraire un dépôt existant

Il est très probable que vous devrez utiliser un dépôt GitHub qui existe uniquement à un emplacement distant, et non sur votre ordinateur local. Visual Studio pour Mac vous permet d’extraire ce dépôt rapidement. Suivez les étapes ci-dessous pour le cloner sur votre ordinateur :

1. Dans la barre de menus, sélectionnez **Gestion de version > Extraire** :

2. L’onglet **Se connecter au référentiel** s’affiche :

    ![Onglet Se connecter au référentiel avec les détails entrés](media/version-control-git13.png)

3. Dans la page GitHub du dépôt distant, appuyez sur le bouton **Cloner ou télécharger** et copiez l’URL fournie :

    ![url github affichée](media/version-control-git14.png)

4. Remplacez tout le texte du champ d’entrée **URL** sous l’onglet **Se connecter au référentiel**. La plupart des autres champs de cet onglet seront remplis pour vous, comme illustré par l’image de l’étape 2.

5. Entrez le répertoire dans lequel vous souhaitez cloner le dépôt et appuyez sur **Extraire**.

> [!NOTE]
Vous pouvez rencontrer des problèmes si le dépôt fait plus de 4 Go.

## <a name="troubleshooting"></a>Résolution des problèmes

Si vous avez des problèmes d’initialisation de votre projet avec un dépôt distant vide, vous pouvez essayer les étapes suivantes :

- Accédez au dossier de votre solution.
- Appuyez sur `Command + Shift + . ` pour afficher les fichiers et dossiers cachés.
- S’il existe un dossier **.git**, supprimez-le.
- S’il existe un fichier **gitignore**, supprimez-le.
- Appuyez sur `Command + Shift + . ` pour masquer les fichiers et les dossiers.
- Ouvrez votre solution dans Visual Studio pour Mac.
- Dans le panneau Solution, sélectionnez le nœud de votre solution.
- Accédez au menu Gestion de version et choisissez **Publier dans la gestion de version**.
- Suivez les étapes du didacticiel ci-dessus à partir de l’étape 6.