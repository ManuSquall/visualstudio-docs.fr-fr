---
title: Configuration d’un dépôt Git
description: Utilisation de Git et de Subversion dans Visual Studio pour Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 02/15/2018
ms.assetid: E992FA1D-B2AD-4A28-ADC6-47E4FC471060
ms.topic: how-to
ms.openlocfilehash: c226e1a8160d0eb1321d244b26177119ec3a5846
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238554"
---
# <a name="set-up-a-git-repository"></a>Configurer un dépôt Git

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

Si vous avez un projet qui _n’est pas_ déjà dans la gestion de versions, effectuez les étapes suivantes pour le configurer dans Git :

1. Sélectionnez le nom de la solution à partir du Panneau Solutions dans Visual Studio pour Mac.

2. Dans la barre de menus, sélectionnez **Gestion de versions > Publier dans la gestion de versions** pour afficher la boîte de dialogue **Sélectionner un dépôt** :

    ![Démarrer l’extraction dans Visual Studio pour Mac](media/version-control-git4-sml.png)

    Si cet élément de menu est grisé dans le menu, vérifiez que vous avez sélectionné le nom de la solution.

3. Choisissez l’onglet **Dépôts inscrits** et cliquez sur le bouton **Ajouter** :

    ![L’onglet dépôts inscrits de la boîte de dialogue Sélectionner le référentiel contient des boutons ajouter, supprimer et modifier, ainsi que des zones pour le nom et le message du module.](media/version-control-git5.png)

4. Entrez le nom du dépôt à afficher localement et collez l’URL de l’étape 3. La boîte de dialogue de configuration de votre dépôt doit être similaire à ceci. Cliquez sur OK :

    ![Boîte de dialogue Entrer les détails git](media/version-control-git6.png)

    Il est également possible d’utiliser le protocole SSH pour la connexion à Git.

5. Pour tenter de publier l’application sur git, sélectionnez le référentiel et assurez-vous que les champs **nom du module** et texte du **message** sont renseignés :

    ![Essayer de publier le projet sur Git](media/version-control-git7.png)

6. Cliquez sur **OK** puis sur **Publier** dans la boîte de dialogue d’alerte.

7. Dans la fenêtre **Informations d’identification Git**, entrez votre nom d’utilisateur et votre mot de passe GitHub. 

> [!NOTE]
> Si l’authentification à 2 facteurs (2FA) est activée pour votre compte, vous devez créer un jeton d’accès, lequel est utilisé à la place d’un mot de passe. Si vous n’avez pas créé de jeton d’accès, suivez les étapes décrites dans la documentation Git [Jeton d’accès](https://help.github.com/articles/creating-an-access-token-for-command-line-use/).

8. Entrez le nom d’utilisateur et le jeton d’accès personnel, puis cliquez sur **OK** :

    ![Entrer un nom d’utilisateur et un mot de passe pour Git](media/version-control-git9-sml.png)

9. Après quelques secondes, la solution doit être publiée avec sa validation initiale. Vérifiez que c’est bien le cas en examinant l’élément de menu Gestion de version, qui doit maintenant contenir de nombreuses options :

    ![Menu Gestion de version](media/version-control-git10.png)

10. Une fois que vous commencez à procéder à d’autres modifications, sélectionnez **Envoyer les modifications** pour envoyer (push) les modifications au référentiel **distant**. Ceci permet à tous les utilisateurs appropriés de les voir sur github.com :

    ![Envoyer (push) des modifications sur un dépôt distant](media/version-control-git11.png)

## <a name="publishing-a-new-project"></a>Publication d’un nouveau projet

La boîte de dialogue Nouveau projet permet de créer un projet avec un dépôt git local. Pour l’activer, cochez la case **Utiliser git pour la gestion de version**, comme le montre la capture d’écran suivante. Ceci initialise votre dépôt et ajoute un fichier .gitignore facultatif :

![Créer un projet avec la prise en charge de git](media/version-control-git-publish-new1.png)

Suivez les étapes ci-dessous pour envoyer (push) votre nouveau dépôt local vers un nouveau dépôt GitHub :

> [!NOTE]
> Si vous n’avez pas déjà créé un dépôt GitHub, consultez la section [Création d’un dépôt distant sur GitHub](#creating-a-remote-repo-on-github).

1. Créez votre première validation en accédant à **Gestion de version > Examiner la solution et valider** dans la barre de menus.

2. Sous l’onglet État, choisissez **Valider** dans le coin supérieur gauche.

3. Écrivez un message de validation, par exemple « Première validation », puis cliquez sur **Valider** :

    ![Valider les modifications initiales apportées au dépôt git](media/version-control-git-publish-new2.png)

4. Ensuite, dans la barre de menus, accédez à **Gestion de version > Gérer les branches et les dépôts distants**.

5. Accédez à l’onglet **Sources distantes**, puis cliquez sur **Ajouter**.

6. Dans la fenêtre **Source distante**, ajoutez les détails du dépôt GitHub que vous avez créé précédemment, puis cliquez sur **OK** :

    ![Configurer des sources distantes pour le dépôt git](media/version-control-git-publish-new3.png)

7. Fermez la fenêtre **Configuration du dépôt Git** puis, dans la barre de menus, accédez à **Gestion de version > Effectuer une opération Push sur les modifications**.

8. Dans la fenêtre **Effectuer une opération Push vers le référentiel**, cliquez sur le bouton **Effectuer une opération Push sur les modifications** :

    ![Envoyer (push) les modifications vers le dépôt distant](media/version-control-git-publish-new4.png)

9. Quand vous y êtes invité, entrez vos nom d’utilisateur et mot de passe GitHub.

> [!NOTE]
> Si l’authentification à 2 facteurs (2FA) est activée pour votre compte, vous devez créer un jeton d’accès, lequel est utilisé à la place d’un mot de passe. Si vous n’avez pas créé de jeton d’accès, suivez les étapes décrites dans la documentation Git [Jeton d’accès](https://help.github.com/articles/creating-an-access-token-for-command-line-use/).

Visual Studio pour Mac enverra désormais les modifications à votre dépôt distant GitHub (push) :

![Confirmation de l’exécution de l’opération Push](media/version-control-git11.png)

## <a name="check-out-an-existing-repository"></a>Extraire un dépôt existant

Vous serez probablement obligé d’utiliser un dépôt GitHub qui existe uniquement à un emplacement distant, et non sur votre machine locale. Visual Studio pour Mac vous permet d’extraire ce dépôt rapidement. Suivez les étapes ci-dessous pour le cloner sur votre ordinateur :

1. Dans la barre de menus, sélectionnez **contrôle de Version > Checkout**:

2. L’onglet **Se connecter au référentiel** s’affiche :

    ![Onglet Se connecter au référentiel avec les détails entrés](media/version-control-git13.png)

3. Dans la page GitHub du dépôt distant, appuyez sur le bouton **Cloner ou télécharger** et copiez l’URL fournie :

    ![url github affichée](media/version-control-git14.png)

4. Remplacez tout le texte dans le champ d’entrée d' **URL** sous l’onglet **se connecter au référentiel** . La plupart des autres champs de cet onglet sont renseignés pour vous, comme illustré dans l’image de l’étape #2.

5. Entrez le répertoire dans lequel vous souhaitez cloner le dépôt et appuyez sur **Extraire**.

> [!NOTE]
> Vous risquez de rencontrer des problèmes si le dépôt fait plus de 4 Go.

## <a name="troubleshooting"></a>Résolution des problèmes

Si vous avez des problèmes d’initialisation de votre projet avec un dépôt distant vide, vous pouvez essayer les étapes suivantes :

1. Accédez au dossier de votre solution.
1. Appuyez sur **Commande + Maj + .** pour afficher les fichiers et dossiers cachés.
1. S’il existe un dossier **.git**, supprimez-le.
1. S’il existe un fichier **gitignore**, supprimez-le.
1. Appuyez sur **Commande + Maj + .** pour masquer les fichiers et les dossiers.
1. Ouvrez votre solution dans Visual Studio pour Mac.
1. Dans le Panneau Solutions, sélectionnez le nœud de votre solution.
1. Accédez au menu Gestion de version et choisissez **Publier dans la gestion de version**.
1. Suivez les étapes du didacticiel ci-dessus à partir de l’étape 6.

## <a name="see-also"></a>Voir aussi

- [Gestion de versions dans Visual Studio (sur Windows)](/visualstudio/version-control/)
