---
title: "Configuration d’un dépôt Git dans Visual Studio pour Mac"
description: Utilisation de Git et de Subversion dans Visual Studio pour Mac.
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: E992FA1D-B2AD-4A28-ADC6-47E4FC471060
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: 9f25eda17648ba7eb3c264660ee0eb3b8eee166c
ms.contentlocale: fr-fr
ms.lasthandoff: 08/11/2017

---

# <a name="setting-up-a-git-repository"></a>Configuration d’un dépôt Git

GiT est un système de gestion de versions distribué qui permet aux équipes de travailler simultanément sur les mêmes documents. Cela signifie qu’il existe un seul serveur contenant tous les fichiers, mais que quand un dépôt est extrait de cette source centrale, l’intégralité du dépôt est cloné localement sur votre machine.

Il existe de nombreux hôtes distants qui vous permettent de travailler avec Git pour la gestion de versions, mais le plus répandu d’entre eux est GitHub. L’exemple ci-dessous utilise un hôte GitHub, mais vous pouvez utiliser n’importe quel hôte Git pour la gestion de versions dans Visual Studio pour Mac.

Si vous voulez utiliser GitHub, veillez à disposer d’un compte créé et configuré avant de suivre les étapes ci-dessous. 

## <a name="creating-a-remote-repo-on-github"></a>Création d’un dépôt distant sur GitHub

L’exemple ci-dessous utilise un hôte GitHub, mais vous pouvez utiliser n’importe quel hôte Git pour la gestion de versions dans Visual Studio pour Mac.

Pour configurer un dépôt Git, effectuez les étapes suivantes :

1. Créez un nouveau dépôt Git sur github.com :

    ![Créer un dépôt Git](media/version-control-git1-sml.png)

2. Définissez le nom, la description et la confidentialité du dépôt. N’initialisez **pas** le dépôt. Définissez .gitignore et la licence sur None :

    ![Définir les détails du dépôt Git](media/version-control-git2.png)

3. Plus loin, vous pouvez choisir d’afficher et de copier l’adresse HTTPS ou SSH vers le dépôt que vous venez de créer :

    ![Afficher et copier l’adresse](media/version-control-git3.png) Vous avez besoin de l’adresse HTTPS pour faire pointer Visual Studio pour Mac vers ce dépôt.


## <a name="publishing-an-existing-project"></a>Publication d’un projet existant

4. Revenez à votre projet ouvert dans Visual Studio pour Mac. 

5. Dans la barre de menus, sélectionnez **Gestion de version > Publier dans la gestion de version...** :

    ![Démarrer l’extraction dans Visual Studio pour Mac](media/version-control-git4-sml.png)

6. La boîte de dialogue **Sélectionner un dépôt** s’affiche. Choisissez l’onglet **Dépôts inscrits** et cliquez sur le bouton **Ajouter** :

    ![](media/version-control-git5.png)

7. Entrez le nom du dépôt à afficher localement et collez l’URL de l’étape 3. La boîte de dialogue de configuration de votre dépôt doit être similaire à ceci. Cliquez sur OK : 

    ![Boîte de dialogue Entrer les détails git](media/version-control-git6.png)

    Notez qu’il est également possible d’utiliser le protocole SSH pour se connecter à Git.

8. Pour tenter de publier l’application sur Git, sélectionnez le dépôt que vous venez de créer et vérifiez que les deux champs texte **Nom du module** et **Message** sont renseignés :

    ![Essayer de publier le projet sur Git](media/version-control-git7.png)

9. Cliquez sur **OK** puis sur **Publier** dans la boîte de dialogue d’alerte.

10. Si vous n’avez pas déjà entré vos informations d’identification Git dans les préférences de Visual Studio pour Mac, entrez-les maintenant. Vous devez d’abord créer un jeton d’accès, qui est utilisé à la place d’un mot de passe. Pour cela, suivez les étapes décrites dans la documentation [Access Token](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) de Git.

11. Entrez le nom d’utilisateur et le jeton d’accès personnel, puis cliquez sur **OK** :

    ![Entrer un nom d’utilisateur et un mot de passe pour Git](media/version-control-git9-sml.png)

12. Après quelques secondes, la solution doit être publiée avec sa validation initiale. Vérifiez que c’est bien le cas en examinant l’élément de menu Gestion de version, qui doit maintenant contenir de nombreuses options : 

    ![Menu Gestion de version](media/version-control-git10.png)

13. Une fois que vous commencez à faire d’autres modifications, sélectionnez **Publier les modifications...** pour envoyer (push) les modifications au dépôt **distant**. Ceci permet à tous les utilisateurs appropriés de les voir sur github.com : 

    ![Envoyer (push) des modifications sur un dépôt distant](media/version-control-git11.png)

## <a name="publishing-a-new-project"></a>Publication d’un nouveau projet

La boîte de dialogue Nouveau projet peut être utilisé pour publier un nouveau projet en utilisant Git. Pour l’activer, cochez la case **Utiliser Git pour la gestion de version**, comme illustré dans la capture d’écran suivante. Ceci initialise votre dépôt et ajoute un fichier .gitignore facultatif :

![Envoyer (push) des modifications sur un dépôt distant](media/version-control-git12.png)

## <a name="troubleshooting"></a>Résolution des problèmes

Si vous avez des problèmes d’initialisation de votre projet avec un dépôt distant vide, vous pouvez essayer les étapes suivantes :

- Accédez au dossier de votre solution.
- Appuyez sur `Command + Shift + . ` pour afficher les fichiers et dossiers cachés.
- S’il existe un dossier `.git`, supprimez-le.
- S’il existe un fichier `gitignore`, supprimez-le.
- Appuyez sur `Command + Shift + . ` pour masquer les fichiers et les dossiers.
- Ouvrez votre solution dans Visual Studio pour Mac.
- Dans le panneau Solution, sélectionnez le nœud de votre solution.
- Accédez au menu Gestion de version et choisissez **Publier dans la gestion de version**.
- Suivez les étapes du didacticiel ci-dessus à partir de l’étape 6.
