---
title: 'Tutoriel : Découvrez Django dans Visual Studio, étape 1'
description: Une procédure pas à pas des notions fondamentales de Django dans le cadre de projets Visual Studio, qui montre la prise en charge du développement de Django par Visual Studio.
ms.date: 08/13/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 882a355742a100f7a105abab541832f86740afe7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942737"
---
# <a name="tutorial-get-started-with-the-django-web-framework-in-visual-studio"></a>Tutoriel : Bien démarrer avec le framework web Django dans Visual Studio

[Django](https://www.djangoproject.com/) est un framework Python général conçu pour un développement web rapide, sécurisé et scalable. Ce tutoriel explore l’infrastructure Django dans le contexte des modèles de projet fournis par Visual Studio pour rationaliser la création d’applications web basées sur Django.

Dans ce didacticiel, vous apprendrez à :

> [!div class="checklist"]
> - créer un projet Django de base dans un référentiel Git à l’aide du modèle « Projet web Django vide » (étape 1) ;
> - créer une application Django d’une page et à afficher cette page à l’aide d’un modèle (étape 2) ;
> - prendre en charge les fichiers statiques, ajouter des pages et utiliser l’héritage du modèle (étape 3) ;
> - utiliser le modèle de projet Web de Django pour créer une application de plusieurs pages et une conception réactive (étape 4) ;
> - authentifier les utilisateurs (étape 5) ;
> - utiliser le modèle de sondages du projet web Django pour créer une application utilisant des modèles des migrations de bases de données et des personnalisations de l’interface d’administration (étape 6).

## <a name="prerequisites"></a>Prérequis

- Visual Studio 2017 sur Windows avec les options suivantes :
  - La charge de travail **Développement Python** (onglet **Charge de travail** dans le programme d’installation). Pour obtenir des instructions, consultez [Installer la prise en charge de Python dans Visual Studio](installing-python-support-in-visual-studio.md).
  - **Git pour Windows** et **Extension GitHub pour Visual Studio** sous l’onglet **Composants individuels** sous **Outils de code**.

Les modèles de projets Django sont également inclus dans toutes les versions précédentes de Python Tools pour Visual Studio, même si certains détails peuvent être différents de ceux traités dans ce tutoriel (en particulier dans les versions antérieures de l’infrastructure Django).

Le développement Python n’est actuellement pas pris en charge dans Visual Studio pour Mac. Sur Mac et Linux, utilisez [l’extension Python dans Visual Studio Code](https://code.visualstudio.com/docs/python/python-tutorial).

### <a name="visual-studio-projects-and-django-projects"></a>« Projets Visual Studio » et « Projets Django »

Dans la terminologie de Django, un « projet Django » est composé de plusieurs fichiers de configuration au niveau du site, ainsi que d’une ou plusieurs « applications » que vous déployez sur un hôte web pour créer une application web complète. Un projet Django peut contenir plusieurs applications, et la même application peut se trouver dans plusieurs projets Django.

Un projet Visual Studio peut, quant à lui, contenir le projet Django, ainsi que plusieurs applications. Par souci de simplicité, chaque fois que ce tutoriel fait juste référence à un « projet », il s’agit du projet Visual Studio. Lorsqu’il fait référence à la partie « projet Django » de l’application web, le terme « Projet Django » est spécifiquement utilisé.

Au cours de ce tutoriel, vous allez créer une solution Visual Studio unique qui contient trois projets Django distincts contenant pour leur part chacun une seule application Django. Conserver les projets dans la même solution vous pouvez permet de basculer facilement entre différents fichiers pour effectuer des comparaisons.

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>Étape 1-1 : créer un projet et une solution Visual Studio

Lorsque vous travaillez avec Django à partir de la ligne de commande, vous commencez généralement un projet en exécutant la commande `django-admin startproject <project_name>`. Dans Visual Studio, l’utilisation du modèle « Projet web Django vide » fournit la même structure dans un projet et dans une solution Visual Studio.

1. Dans Visual Studio, sélectionnez **Fichier** > **Nouveau** > **Projet**, recherchez « Django », puis sélectionnez le modèle **Projet web Django vide**. (Le modèle se trouve également sous **Python** > **Web** dans la liste de gauche.)

    ![Nouvelle boîte de dialogue de projet dans Visual Studio pour le projet web Django vide](media/django/step01-new-blank-project.png)

1. Dans les champs en bas de la boîte de dialogue, entrez les informations suivantes (comme indiqué dans le graphique précédent), puis sélectionnez **OK** :

    - **Nom** : définissez le nom du projet Visual Studio sur **BasicProject**. Par défaut, ce nom est également utilisé pour le projet Django.
    - **Emplacement** : spécifiez un emplacement où créer la solution et le projet Visual Studio.
    - **Solution** : laissez l’option **Créer une solution** par défaut pour ce contrôle.
    - **Nom de la solution** : valeur **LearningDjango**, qui convient pour la solution en tant que conteneur pour plusieurs projets de ce tutoriel.
    - **Créer un répertoire pour la solution** : laissez cette option activée (par défaut).
    - **Créez un référentiel Git** : sélectionnez cette option (qui est clairement par défaut), afin que Visual Studio crée un référentiel Git local lorsqu’il crée la solution. Si vous ne voyez pas cette option, exécutez le programme d’installation de Visual Studio 2017 et ajoutez **Git pour Windows** et **Extension GitHub pour Visual Studio** sous l’onglet **Composants individuels** sous **Outils de code**.

1. Au bout d’un moment, Visual Studio affiche une boîte de dialogue indiquant **Des packages externes sont nécessaires pour ce projet** (voir plus bas). Cette boîte de dialogue s’affiche, car le modèle inclut un fichier *requirements.txt* référençant le dernier package Django 1.x. (Sélectionnez **Afficher les packages requis** pour voir les dépendances exactes.)

    ![Invite indiquant que le projet requiert des packages externes](media/django/step01-requirements-prompt-install-myself.png)

1. Sélectionnez l’option **I will install them myself**. Vous créez brièvement l’environnement virtuel pour vous assurer qu’il est exclu du contrôle de code source. (L’environnement peut toujours être créé à partir de *requirements.txt*.)

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>Étape 1-2 : examiner les contrôles Git et publiez sur un référentiel distant

Étant donné que vous avez sélectionné **Créer un référentiel Git** dans la boîte de dialogue **Nouveau projet**, le projet est déjà validé par le contrôle de code source local dès que le processus de création est terminé. À cette étape, vous vous familiarisez avec les contrôles Git de Visual Studio et la fenêtre **Team Explorer** dans laquelle vous travaillez avec le contrôle de code source.

1. Examinez les contrôles Git dans le coin inférieur de la fenêtre principale de Visual Studio. De gauche à droite, ces contrôles montrent les validations inactives, les modifications non validées, le nom du référentiel et la branche actuelle :

    ![Contrôles GIT dans la fenêtre Visual Studio](media/django/step01-git-controls.png)

    > [!Note]
    > Si vous ne sélectionnez pas **Créer un référentiel Git** dans la boîte de dialogue **Nouveau projet**, les contrôles Git affichent seulement une commande **Ajouter au contrôle de code source** qui crée un référentiel local.
    >
    > ![Ajouter au contrôle de code Source s’affiche dans Visual Studio si vous n’avez pas créé de référentiel.](media/django/step01-git-add-to-source-control.png)

1. Lorsque vous sélectionnez le bouton Modifications, Visual Studio ouvre sa fenêtre **Team Explorer** à la page **Modifications** page. Étant donné que le projet nouvellement créé est déjà automatiquement validé dans le contrôle de code source, vous ne voyez pas de modifications en attente.

    ![Fenêtre Team Explorer à la page Modifications](media/django/step01-team-explorer-changes.png)

1. Dans la barre d’état de Visual Studio, sélectionnez le bouton des validations n’ayant pas fait l’objet d’un Push (flèche haut avec **2**) pour ouvrir la page **Synchronisation** dans **Team Explorer**. Étant donné que vous avez uniquement un référentiel local, la page fournit des options simples pour publier le référentiel sur les différents référentiels à distance.

    ![La fenêtre Team Explorer affiche les options de référentiels disponibles pour le contrôle de code source.](media/django/step01-team-explorer.png)

    Vous pouvez choisir le service souhaité pour vos propres projets. Ce tutoriel montre comment utiliser GitHub. L’exemple de code terminé est conservé dans le dépôt [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django).

1. Lors de la sélection d’un des contrôles **Publication**, **Team Explorer** vous invite à obtenir plus d’informations. Par exemple, lors de la publication de l’exemple de ce tutoriel, le référentiel proprement dit a dû être créé en premier, auquel cas l’option **Push sur référentiel distant** a été utilisée avec l’URL du référentiel.

    ![Fenêtre Team Explorer pour pousser vers un référentiel distant existant](media/django/step01-push-to-github.png)

    Si vous n’avez pas de dépôt existant, les options **Publier sur GitHub** et **Envoyer (push) sur Azure DevOps** vous permettent d’en créer un directement dans Visual Studio.

1. Au cours de ce tutoriel, prenez l’habitude d’utiliser périodiquement les contrôles dans Visual Studio pour valider et envoyer des modifications. Ce tutoriel vous le rappellera aux endroits appropriés.

> [!Tip]
> Pour naviguer rapidement dans **Team Explorer**, sélectionnez l’en-tête (qui s’appelle **Modifications** ou **Push** dans les images ci-dessus) pour afficher un menu contextuel des pages disponibles.

### <a name="question-what-are-some-advantages-of-using-source-control-from-the-beginning-of-a-project"></a>Question : Quels sont les avantages de l’utilisation du contrôle de code source dès le début d’un projet ?

Réponse : Tout d’abord, l’utilisation du contrôle de code source dès le début, en particulier si vous utilisez également un référentiel distant, assure une sauvegarde hors site régulière de votre projet. Contrairement au maintien d’un projet uniquement sur un système de fichiers local, le contrôle de code source fournit également un historique complet des modifications et permet de revenir facilement à un état précédent d’un seul fichier ou de tout le projet. L’historique des modifications aide à déterminer la cause des régressions (échecs de test). Par ailleurs, le contrôle de code source est essentiel si plusieurs personnes travaillent sur un projet, car il gère les remplacements et permet la résolution des conflits. Enfin, grâce au contrôle de code source, qui est fondamentalement une forme d’automatisation, vous êtes bien préparés à l’automatisation de la génération, des tests et de la gestion des versions. Il s’agit bien là de la première étape de l’utilisation de DevOps pour un projet, et étant donné qu’il y a peu d’obstacles à l’entrée, il n’y a vraiment aucune raison de ne pas utiliser le contrôle de code source dès le début.

Pour poursuivre la discussion sur le contrôle de code source comme méthode d’automatisation, consultez Pour obtenir des informations supplémentaires sur le contrôle de code source en tant qu’automation, consultez [La Source de vérité : le rôle des référentiels dans DevOps](https://msdn.microsoft.com/magazine/mt763232), un article de MSDN Magazine écrit pour les applications mobiles qui s’applique également aux applications web.

### <a name="question-can-i-prevent-visual-studio-from-auto-committing-a-new-project"></a>Question : Puis-je empêcher Visual Studio de valider automatiquement un nouveau projet ?

Réponse : Oui. Pour désactiver la validation automatique, accédez à la page **Paramètres** dans **Team Explorer**, sélectionnez **Git** > **Paramètres globaux**, désactivez l’option intitulée **Valider les modifications après une fusion par défaut**, puis sélectionnez **Mise à jour**.

## <a name="step-1-3-create-the-virtual-environment-and-exclude-it-from-source-control"></a>Étape 1-3 : créer l’environnement virtuel et l’exclure du contrôle de code source

Maintenant que vous avez configuré le contrôle de code source pour votre projet, vous pouvez créer l’environnement virtuel qui contient les packages Django nécessaires pour le projet. Vous pouvez ensuite utiliser **Team Explorer** pour exclure le dossier de l’environnement du contrôle de code source.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Environnements Python** et sélectionnez **Ajouter un environnement virtuel**.

    ![Ajouter la commande Environnement virtuel dans l’Explorateur de solutions](media/django/step01-add-virtual-environment-command.png)

1. Une boîte de dialogue **Ajouter un environnement virtuel** s’affiche avec un message indiquant **Nous avons trouvé un fichier requirements.txt.** Ce message indique que Visual Studio utilise ce fichier pour configurer l’environnement virtuel.

    ![Ajouter un environnement virtuel avec un message de requirements.txt](media/django/step01-add-virtual-environment-found-requirements.png)

1. Cliquez sur **Créer** pour accepter les valeurs par défaut. (Vous pouvez modifier le nom de l’environnement virtuel si vous le souhaitez, ce qui modifie uniquement le nom du sous-dossier, mais `env` est une convention standard.)

1. Donnez votre consentement aux privilèges d’administrateur si vous y êtes invité, puis patientez quelques minutes pendant que Visual Studio télécharge et installe les packages, ce qui, pour Django, équivaut à développer plusieurs milliers de fichiers dans autant de sous-dossiers ! Vous pouvez consulter la progression dans la fenêtre **Sortie** de Visual Studio. Pendant que vous patientez, réfléchissez aux sections de questions ci-dessous.

1. Sur les contrôles Git de Visual Studio (dans la barre d’état), sélectionnez l’indicateur de modifications (affichant **99&#42;**), ce qui ouvre la page **Modifications** de **Team Explorer**.

    La création de l’environnement virtuel a entraîné des milliers de modifications, mais il n’est pas nécessaire de les inclure dans le contrôle de code source, car vous (ou toute autre personne clonant le projet) pouvez toujours recréer l’environnement à partir de *requirements.txt*.

    Pour exclure l’environnement virtuel, cliquez avec le bouton droit sur le dossier **env** et sélectionnez **Ignorer ces éléments locaux**.

    ![Ignorer un environnement virtuel dans les modifications du contrôle de code source](media/django/step01-ignore-local-items.png)

1. Après l’exclusion de l’environnement virtuel, les seules modifications restantes sont dans le fichier projet et dans *.gitignore*. Le fichier *.gitignore* contient une entrée ajoutée pour le dossier de l’environnement virtuel. Vous pouvez double-cliquer sur le fichier pour voir la différence.

1. Entrez un message de validation et sélectionnez le bouton **Valider tout**, puis envoyez les validations à votre référentiel distant si vous le souhaitez.

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>Question : Pourquoi créer un environnement virtuel ?

Réponse : Un environnement virtuel est un excellent moyen d’isoler les dépendances exactes de votre application. Cette isolation évite les conflits dans un environnement Python global et facilite les tests et la collaboration. Au fil du temps, quand vous développez une application, vous introduisez invariablement de nombreux packages Python très utiles. En conservant les packages dans un environnement virtuel spécifique au projet, vous pouvez facilement mettre à jour le fichier *requirements.txt* du projet qui décrit cet environnement, ce qui est inclus dans le contrôle de code source. Quand le projet est copié vers d’autres ordinateurs, dont des serveurs de builds, des serveurs de déploiement et d’autres ordinateurs de développement, il est facile de recréer l’environnement uniquement avec *requirements.txt* (c’est la raison pour laquelle l’environnement n’a pas besoin d’être dans le contrôle de code source). Pour plus d’informations, consultez [Utiliser des environnements virtuels](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>Question : Comment supprimer un environnement virtuel déjà validé par le contrôle de code source ?

Réponse : tout d’abord, modifiez votre fichier *.gitignore* pour exclure le dossier : recherchez la section à la fin avec le commentaire `# Python Tools for Visual Studio (PTVS)` et ajoutez une nouvelle ligne pour le dossier d’environnement virtuel, par exemple `/BasicProject/env`. (Étant donné que Visual Studio n’affiche pas le fichier dans l’**Explorateur de solutions**, ouvrez-le directement avec la commande de menu **Fichier** > **Ouvrir**  >   **Fichier**. Vous pouvez également ouvrir le fichier à partir de **Team Explorer** : dans la page **Paramètres**, sélectionnez **Paramètres du dépôt**, accédez à la section**Ignorer et fichiers d’attributs**, puis sélectionnez le lien **Modifier** situé en regard de **.gitignore**.)

Ensuite, ouvrez une fenêtre Commande, accédez au dossier, par exemple *BasicProject*, qui contient le dossier d’environnement virtuel, par exemple *env*, et exécutez `git rm -r env`. Validez ensuite ces modifications depuis la ligne de commande (`git commit -m 'Remove venv'`), ou depuis la page **Modifications** de **Team Explorer**.

## <a name="step-1-4-examine-the-boilerplate-code"></a>Étape 1-4 : examiner le code réutilisable

Une fois la création du projet terminée, examinez le code de projet Django réutilisable (qui est à nouveau le même que celui généré par la commande CLI `django-admin startproject <project_name>`).

1. Dans la racine de votre projet figure *manage.py*, l’utilitaire d’administration de ligne de commande Django automatiquement défini par Visual Studio en tant que fichier de démarrage du projet. Vous exécutez l’utilitaire sur la ligne de commande avec `python manage.py <command> [options]`. Pour les tâches Django courantes, Visual Studio fournit des commandes de menu pratiques. Cliquez avec le bouton droit sur le projet dans l’**Explorateur de solutions**, puis sélectionnez **Python** pour voir la liste. Vous rencontrerez certaines de ces commandes pendant ce tutoriel.

    ![Commandes Django dans le menu contextuel d’un projet Python](media/django/step01-django-commands-menu.png)

2. Votre projet contient un dossier qui porte le même nom que le projet. Il contient les fichiers projet Django de base :

   - *__init.py* : un fichier vide qui indique à Python que ce dossier est un package Python.
   - *wsgi.py* : un point d’entrée pour les serveurs web compatibles WSGI afin de traiter votre projet. Vous ne toucherez généralement pas à ce fichier, qui assure les raccordements des serveurs web de production.
   - *settings.py* : contient les paramètres du projet Django, que vous modifiez au cours du développement d’une application web.
   - *urls.py* : contient une table des matières pour le projet Django, que vous modifiez également au cours du développement.

     ![Fichiers du projet Django dans l’Explorateur de solutions](media/django/step01-django-project-in-solution-explorer.png)

3. Comme indiqué précédemment, le modèle Visual Studio ajoute également un fichier *requirements.txt* à votre projet en spécifiant la dépendance du package Django. C’est ce fichier qui vous invite à créer un environnement virtuel lors de la création du projet.

### <a name="question-can-visual-studio-generate-a-requirementstxt-file-from-a-virtual-environment-after-i-install-other-packages"></a>Question : Est-ce que Visual Studio peut générer un fichier requirements.txt à partir d’un environnement virtuel après l’installation d’autres packages ?

Réponse : Oui. Développez le nœud **Environnements Python**, cliquez avec le bouton droit sur votre environnement virtuel, puis sélectionnez la commande **Générer requirements.txt**. Il est bon d’utiliser régulièrement cette commande quand vous modifiez l’environnement, et d’envoyer les modifications à *requirements.txt* pour le contrôle de code source ainsi que d’autres modifications de code qui dépendent de cet environnement. Si vous configurez l’intégration continue sur un serveur de builds, vous devez générer le fichier et valider les modifications chaque fois que vous modifiez l’environnement.

## <a name="step-1-5-run-the-empty-django-project"></a>Étape 1-5 : exécuter le projet Django vide

1. Dans Visual Studio, sélectionnez **Déboguer** > **Démarrer le débogage** (**F5**) ou utilisez le bouton **Serveur web** dans la barre d’outils (le navigateur affiché peut varier) :

    ![Exécuter le bouton de la barre d’outils du serveur Web dans Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Exécuter le serveur revient à exécuter la commande `manage.py runserver <port>`, qui lance le serveur de développement intégré de Django. Si Visual Studio indique **Impossible de démarrer le débogueur** avec un message informant de l’absence d’un fichier de démarrage, cliquez avec le bouton droit sur **manage.py** dans **l’Explorateur de solutions** et sélectionnez **Définir comme fichier de démarrage**.

1. Lorsque vous démarrez le serveur, une fenêtre de console contenant également le journal du serveur s’affiche. Visual Studio ouvre automatiquement un navigateur pour accéder à `http://localhost:<port>`. Étant donné que le projet Django n’a aucune application, Django affiche uniquement une page par défaut pour confirmer que ce que vous avez jusqu'à présent fonctionne correctement :

    ![Affichage par défaut du projet Django](media/django/step01-first-run-success.png)

1. Lorsque vous avez terminé, arrêtez le serveur en fermant la fenêtre de console, ou à l’aide de la commande **Déboguer** > **Arrêter le débogage** dans Visual Studio.

### <a name="question-is-django-a-web-server-as-well-as-a-framework"></a>Question : Django est-il à la fois un serveur web et une infrastructure ?

Réponse : oui et non. Django a un serveur web intégré qui est utilisé à des fins de développement. Ce serveur web est utilisé lorsque vous exécutez l’application web localement, par exemple lors d’un débogage dans Visual Studio. Cependant, lorsque vous déployez sur un hôte web, Django utilise le serveur web de l’hôte à la place. Le module *wsgi.py* dans le projet Django prend en charge le raccordement aux serveurs de production.

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>Question : Quelle est la différence entre les commandes de menu Déboguer et les commandes de serveur dans le sous-menu Python du projet ?

Réponse : en plus des commandes de menu **Déboguer** et des boutons de barre d’outils, vous pouvez également lancer le serveur avec les commandes **Python** > **Exécuter le serveur** ou **Python** > **Exécuter le serveur de débogage** dans le menu contextuel du projet. Les deux commandes ouvrent une fenêtre de console dans laquelle vous voyez l’URL locale (localhost:port) du serveur en cours d’exécution. Toutefois, vous devez ouvrir manuellement un navigateur avec cette URL, et l’exécution du serveur de débogage n’entraîne pas le démarrage automatique du débogueur Visual Studio. Vous pourrez attacher un débogueur au processus en cours d’exécution plus tard si vous le souhaitez, avec la commande **Déboguer** > **Attacher au processus**.

## <a name="next-steps"></a>Étapes suivantes

À ce stade, le projet de base Django ne contient pas d’applications. Vous créerez une application à l’étape suivante. Étant donné que vous travaillez généralement plutôt avec des applications Django qu’avec le projet Django, vous n’avez pas besoin d’en savoir plus sur les fichiers réutilisables pour le moment.

> [!div class="nextstepaction"]
> [Créer une application Django avec des affichages et des modèles de pages ](learn-django-in-visual-studio-step-02-create-an-app.md)

## <a name="go-deeper"></a>Approfondir la question

- Code de projet Django : [Écrire votre première application Django, 1ère partie](https://docs.djangoproject.com/en/2.0/intro/tutorial01/) (docs.djangoproject.com)
- Utilitaire d’administration : [django-admin et manage.py](https://docs.djangoproject.com/en/2.0/ref/django-admin/) (docs.djangoproject.com)
- Code source du tutoriel sur GitHub : [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
