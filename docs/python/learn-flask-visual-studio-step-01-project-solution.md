---
title: Tutoriel d’apprentissage de Flask dans Visual Studio - étape  1, principes de base de Flask
titleSuffix: ''
description: Passage en revue des principes de base de Flask dans le contexte des projets Visual Studio, y compris des conditions préalables, de Git et des environnements virtuels.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 018b9a6707ea46a9b1c46f820faf7bd47dac1ff9
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809896"
---
# <a name="tutorial-get-started-with-the-flask-web-framework-in-visual-studio"></a>Tutoriel : Bien démarrer avec le framework web Flask dans Visual Studio

[Flask](https://palletsprojects.com/p/flask/) est un framework Python léger pour les applications web, qui fournit les éléments de base pour le routage d’URL et le rendu de page.

Flask est appelée une « micro-infrastructure », car elle ne fournit pas directement des fonctionnalités comme validation de formulaire, l’abstraction des bases de données, l’authentification, etc. Au lieu de cela, ces fonctionnalités sont fournies par des packages Python spéciaux, appelés des *extensions* Flask. Les extensions s’intègrent de façon transparente à Flask : ils apparaissent donc comme s’ils faisaient partie de Flask lui-même. Par exemple, Flask ne fournit pas lui-même un moteur de modèle de page. La création de modèles est fournie par des extensions comme Jinja et Jade, comme illustré dans ce tutoriel.

Dans ce tutoriel, vous allez apprendre à :

> [!div class="checklist"]
> - Créer un projet Flask de base dans un dépôt Git en utilisant le modèle « Projet web Flask vide » (étape 1)
> - Créer une application Flask d’une seule page et afficher cette page en utilisant un modèle (étape 2)
> - prendre en charge les fichiers statiques, ajouter des pages et utiliser l’héritage du modèle (étape 3) ;
> - Utiliser le modèle Projet web Flask pour créer une application de plusieurs pages et une conception réactive (étape 4)
> - Utiliser le modèle Projet web Flask de sondages pour créer une application de sondages qui utilise différentes options de stockage (Stockage Azure, MongoDB ou en mémoire)

Au cours de ces étapes, vous créez une même solution Visual Studio qui contient trois projets distincts. Vous créez le projet en utilisant différents modèles de projet Flask qui sont inclus dans Visual Studio. Conserver les projets dans la même solution vous pouvez permet de basculer facilement entre différents fichiers pour effectuer des comparaisons.

> [!Note]
> Ce tutoriel diffère de [Flask - Démarrage rapide](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json) en cela que vous en apprenez plus sur Flask et que vous découvrez comment utiliser les différents modèles de projet Flask qui constituent un point de départ plus avancé pour vos propres projets. Par exemple, les modèles de projet installent automatiquement le package Flask lors de la création d’un projet, ce qui vous évite de devoir l’installer manuellement, comme expliqué dans le guide de démarrage rapide.

## <a name="prerequisites"></a>Prérequis

- Visual Studio 2017 ou ultérieur sur Windows avec les options suivantes :
  - La charge de travail **Développement Python** (onglet **Charge de travail** dans le programme d’installation). Pour obtenir des instructions, consultez [Installer la prise en charge de Python dans Visual Studio](installing-python-support-in-visual-studio.md).
  - **Git pour Windows** et **Extension GitHub pour Visual Studio** sous l’onglet **Composants individuels** sous **Outils de code**.

Les modèles de projet Flask sont inclus dans toutes les versions antérieures de Python Tools pour Visual Studio, même si des détails peuvent différer de ce qui est décrit dans ce tutoriel.

Le développement Python n’est actuellement pas pris en charge dans Visual Studio pour Mac. Sur Mac et Linux, utilisez [l’extension Python dans Visual Studio Code](https://code.visualstudio.com/docs/python/python-tutorial).

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>Étape 1-1 : créer un projet et une solution Visual Studio

1. Dans Visual Studio, sélectionnez **fichier**  >  **nouveau**  >  **projet**, recherchez « fiole », puis sélectionnez le modèle de **projet Web flacon vide** . (Le modèle est également disponible sous **python**  >  **Web** dans la liste de gauche.)

    ![Boîte de dialogue Nouveau projet dans Visual Studio pour le projet web Flask vide](media/flask/step01-new-blank-project.png)

1. Dans les champs en bas de la boîte de dialogue, entrez les informations suivantes (comme indiqué dans le graphique précédent), puis sélectionnez **OK** :

    - **Nom**: définissez le nom du projet Visual Studio sur **BasicProject**. Ce nom est également utilisé pour le projet Flask.
    - **Emplacement** : spécifiez un emplacement où créer la solution et le projet Visual Studio.
    - **Nom de la solution** : défini sur **LearningFlask**, qui convient pour la solution en tant que conteneur pour plusieurs projets de ce tutoriel.
    - **Créer un répertoire pour la solution** : laissez cette option activée (par défaut).
    - **Créez un référentiel Git** : sélectionnez cette option (qui est clairement par défaut), afin que Visual Studio crée un référentiel Git local lorsqu’il crée la solution. Si vous ne voyez pas cette option, exécutez le programme d’installation de Visual Studio et ajoutez **Git pour Windows** et **Extension GitHub pour Visual Studio** sous l’onglet **Composants individuels** sous **Outils de code**.

1. Après quelques instants, Visual Studio vous invite à saisir un dialogue indiquant que **ce projet nécessite des packages externes** (voir ci-dessous). Cette boîte de dialogue s’affiche, car le modèle inclut un fichier *requirements.txt* référençant le dernier package Flask 1.x. (Sélectionnez **Afficher les packages requis** pour voir les dépendances exactes.)

    ![Invite indiquant que le projet requiert des packages externes](media/tutorials-common/step01-requirements-prompt-install-myself.png)

1. Sélectionnez l’option **I will install them myself**. Vous créez brièvement l’environnement virtuel pour vous assurer qu’il est exclu du contrôle de code source. (L’environnement peut toujours être créé à partir de *requirements.txt*.)

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>Étape 1-2 : examiner les contrôles Git et publiez sur un référentiel distant

Étant donné que vous avez sélectionné **Créer un référentiel Git** dans la boîte de dialogue **Nouveau projet**, le projet est déjà validé par le contrôle de code source local dès que le processus de création est terminé. À cette étape, vous vous familiarisez avec les contrôles Git de Visual Studio et la fenêtre **Team Explorer** dans laquelle vous travaillez avec le contrôle de code source.

1. Examinez les contrôles Git dans le coin inférieur de la fenêtre principale de Visual Studio. De gauche à droite, ces contrôles montrent les validations inactives, les modifications non validées, le nom du référentiel et la branche actuelle :

    ![Contrôles GIT dans la fenêtre Visual Studio](media/flask/step01-git-controls.png)

    > [!Note]
    > Si vous ne sélectionnez pas **Créer un référentiel Git** dans la boîte de dialogue **Nouveau projet**, les contrôles Git affichent seulement une commande **Ajouter au contrôle de code source** qui crée un référentiel local.
    >
    > ![Ajouter au contrôle de code Source s’affiche dans Visual Studio si vous n’avez pas créé de référentiel.](media/tutorials-common/step01-git-add-to-source-control.png)

1. Lorsque vous sélectionnez le bouton Modifications, Visual Studio ouvre sa fenêtre **Team Explorer** à la page **Modifications** page. Étant donné que le projet nouvellement créé est déjà automatiquement validé dans le contrôle de code source, vous ne voyez pas de modifications en attente.

    ![Fenêtre Team Explorer à la page Modifications](media/flask/step01-team-explorer-changes.png)

1. Dans la barre d’état de Visual Studio, sélectionnez le bouton validations non Pushed (flèche haut avec **2**) pour ouvrir la page **synchronisation** dans **Team Explorer**. Étant donné que vous avez uniquement un référentiel local, la page fournit des options simples pour publier le référentiel sur les différents référentiels à distance.

    ![La fenêtre Team Explorer affiche les options de référentiels disponibles pour le contrôle de code source.](media/flask/step01-team-explorer.png)

    Vous pouvez choisir le service souhaité pour vos propres projets. Ce tutoriel montre l’utilisation de GitHub, où l’exemple de code terminé pour le tutoriel est conservé dans le dépôt [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask).

1. Lors de la sélection d’un des contrôles **Publication**, **Team Explorer** vous invite à obtenir plus d’informations. Par exemple, lors de la publication de l’exemple de ce tutoriel, le référentiel proprement dit a dû être créé en premier, auquel cas l’option **Push sur référentiel distant** a été utilisée avec l’URL du référentiel.

    ![Fenêtre Team Explorer pour pousser vers un référentiel distant existant](media/flask/step01-push-to-github.png)

    Si vous n’avez pas de dépôt existant, les options **Publier sur GitHub** et **Envoyer (push) sur Azure DevOps** vous permettent d’en créer un directement dans Visual Studio.

1. Au cours de ce tutoriel, prenez l’habitude d’utiliser périodiquement les contrôles dans Visual Studio pour valider et envoyer des modifications. Ce tutoriel vous le rappellera aux endroits appropriés.

> [!Tip]
> Pour naviguer rapidement dans **Team Explorer**, sélectionnez l’en-tête (qui lit les **modifications** ou **envoie** les images ci-dessus) pour afficher un menu contextuel des pages disponibles.

### <a name="question-what-are-some-advantages-of-using-source-control-from-the-beginning-of-a-project"></a>Question : Quels sont les avantages de l’utilisation du contrôle de code source dès le début d’un projet ?

Réponse : Tout d’abord, l’utilisation du contrôle de code source dès le début, en particulier si vous utilisez également un référentiel distant, assure une sauvegarde hors site régulière de votre projet. Contrairement au maintien d’un projet uniquement sur un système de fichiers local, le contrôle de code source fournit également un historique complet des modifications et permet de revenir facilement à un état précédent d’un seul fichier ou de tout le projet. L’historique des modifications aide à déterminer la cause des régressions (échecs de test). Par ailleurs, le contrôle de code source est essentiel si plusieurs personnes travaillent sur un projet, car il gère les remplacements et permet la résolution des conflits. Enfin, grâce au contrôle de code source, qui est fondamentalement une forme d’automatisation, vous êtes bien préparés à l’automatisation de la génération, des tests et de la gestion des versions. Il s’agit bien là de la première étape de l’utilisation de DevOps pour un projet, et étant donné qu’il y a peu d’obstacles à l’entrée, il n’y a vraiment aucune raison de ne pas utiliser le contrôle de code source dès le début.

Pour poursuivre la discussion sur le contrôle de code source comme méthode d’automatisation, consultez Pour obtenir des informations supplémentaires sur le contrôle de code source en tant qu’automation, consultez [La Source de vérité : le rôle des référentiels dans DevOps](/archive/msdn-magazine/2016/september/mobile-devops-the-source-of-truth-the-role-of-repositories-in-devops), un article de MSDN Magazine écrit pour les applications mobiles qui s’applique également aux applications web.

### <a name="question-can-i-prevent-visual-studio-from-auto-committing-a-new-project"></a>Question : Puis-je empêcher Visual Studio de valider automatiquement un nouveau projet ?

Réponse : Oui. Pour désactiver la validation automatique, accédez à la page **Paramètres** dans **Team Explorer**, sélectionnez **Git** > **Paramètres globaux**, désactivez l’option intitulée **Valider les modifications après une fusion par défaut**, puis sélectionnez **Mise à jour**.

## <a name="step-1-3-create-the-virtual-environment-and-exclude-it-from-source-control"></a>Étape 1-3 : créer l’environnement virtuel et l’exclure du contrôle de code source

Maintenant que vous avez configuré le contrôle de code source pour votre projet, vous pouvez créer l’environnement virtuel avec les packages Flask nécessaires pour le projet. Vous pouvez ensuite utiliser **Team Explorer** pour exclure le dossier de l’environnement du contrôle de code source.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Environnements Python** et sélectionnez **Ajouter un environnement virtuel**.

    ![Ajouter la commande Environnement virtuel dans l’Explorateur de solutions](media/flask/step01-add-virtual-environment-command.png)

1. La boîte de dialogue **Ajouter un environnement virtuel** s’affiche avec un message indiquant **que nous avons trouvé un fichier de requirements.txt.** Ce message indique que Visual Studio utilise ce fichier pour configurer l’environnement virtuel.

    ![Ajouter un environnement virtuel avec un message de requirements.txt](media/tutorials-common/step01-add-virtual-environment-found-requirements.png)

1. Cliquez sur **Créer** pour accepter les valeurs par défaut. (Vous pouvez modifier le nom de l’environnement virtuel si vous le souhaitez, ce qui modifie uniquement le nom du sous-dossier, mais `env` est une convention standard.)

1. Donnez votre consentement aux privilèges d’administrateur si vous y êtes invité, puis patientez quelques minutes pendant que Visual Studio télécharge et installe les packages, ce qui pour Flask et ses dépendances signifie décompresser environ un millier de fichiers dans plus de 100 sous-dossiers. Vous pouvez consulter la progression dans la fenêtre **Sortie** de Visual Studio. Pendant que vous patientez, réfléchissez aux sections de questions ci-dessous. Vous pouvez également voir une description des dépendances de Flask dans la page [Installation de Flask](https://flask.palletsprojects.com/en/1.0.x/installation/#installation) (flask.pcocoo.org).

1. Sur les contrôles Git de Visual Studio (sur la barre d’état), sélectionnez l’indicateur de modifications (affichant **99&#42;**), ce qui ouvre la page **Modifications** de **Team Explorer**.

    La création de l’environnement virtuel a entraîné des centaines de modifications, mais il n’est pas nécessaire de les inclure dans le contrôle de code source, car vous (ou toute autre personne clonant le projet) pouvez toujours recréer l’environnement à partir de *requirements.txt*.

    Pour exclure l’environnement virtuel, cliquez avec le bouton droit sur le dossier **env** et sélectionnez **Ignorer ces éléments locaux**.

    ![Ignorer un environnement virtuel dans les modifications du contrôle de code source](media/flask/step01-ignore-local-items.png)

1. Après l’exclusion de l’environnement virtuel, les seules modifications restantes sont dans le fichier projet et dans *.gitignore*. Le fichier *.gitignore* contient une entrée ajoutée pour le dossier de l’environnement virtuel. Vous pouvez double-cliquer sur le fichier pour voir la différence.

1. Entrez un message de validation et sélectionnez le bouton **Valider tout**, puis envoyez les validations à votre référentiel distant si vous le souhaitez.

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>Question : Pourquoi créer un environnement virtuel ?

Réponse : Un environnement virtuel est un excellent moyen d’isoler les dépendances exactes de votre application. Cette isolation évite les conflits dans un environnement Python global et facilite les tests et la collaboration. Au fil du temps, quand vous développez une application, vous introduisez invariablement de nombreux packages Python très utiles. En conservant les packages dans un environnement virtuel spécifique au projet, vous pouvez facilement mettre à jour le fichier *requirements.txt* du projet qui décrit cet environnement, ce qui est inclus dans le contrôle de code source. Quand le projet est copié vers d’autres ordinateurs, dont des serveurs de builds, des serveurs de déploiement et d’autres ordinateurs de développement, il est facile de recréer l’environnement uniquement avec *requirements.txt* (c’est la raison pour laquelle l’environnement n’a pas besoin d’être dans le contrôle de code source). Pour plus d’informations, consultez [Utiliser des environnements virtuels](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>Question : Comment supprimer un environnement virtuel déjà validé par le contrôle de code source ?

Réponse : tout d’abord, modifiez votre fichier *.gitignore* pour exclure le dossier : recherchez la section à la fin avec le commentaire `# Python Tools for Visual Studio (PTVS)` et ajoutez une nouvelle ligne pour le dossier d’environnement virtuel, par exemple `/BasicProject/env`. (Étant donné que Visual Studio n’affiche pas le fichier dans l’**Explorateur de solutions**, ouvrez-le directement avec la commande de menu **Fichier** > **Ouvrir** > ** Fichier**. Vous pouvez également ouvrir le fichier à partir de **Team Explorer** : dans la page **Paramètres**, sélectionnez **Paramètres du dépôt**, accédez à la section**Ignorer et fichiers d’attributs**, puis sélectionnez le lien **Modifier** situé en regard de **.gitignore**.)

Ensuite, ouvrez une fenêtre Commande, accédez au dossier, par exemple *BasicProject*, qui contient le dossier d’environnement virtuel, par exemple *env*, et exécutez `git rm -r env`. Validez ensuite ces modifications depuis la ligne de commande (`git commit -m 'Remove venv'`), ou depuis la page **Modifications** de **Team Explorer**.

## <a name="step-1-4-examine-the-boilerplate-code"></a>Étape 1-4 : examiner le code réutilisable

1. Une fois la création du projet terminée, vous voyez la solution et le projet dans **l’Explorateur de solutions**, où le projet contient seulement deux fichiers, *app.py* et *requirements.txt* :

    ![Fichiers du projet Flask vide dans l’Explorateur de solutions](media/flask/step01-blank-flask-project-in-solution-explorer.png)

1. Comme indiqué précédemment, le fichier *requirements.txt* spécifie la dépendance du package Flask. C’est ce fichier qui vous invite à créer un environnement virtuel lors de la création du projet.

1. Le fichier *requirements.txt* contient trois parties. Il y a d’abord une instruction `import` pour Flask, la création d’une instance de la classe `Flask`, qui est affectée à la variable `app`, puis l’affectation d’une variable `wsgi_app` (qui est utile lors du déploiement sur un hôte web, mais n’est pas utilisée pour l’instant) :

    ```python
    from flask import Flask
    app = Flask(__name__)

    # Make the WSGI interface available at the top level so wfastcgi can get it.
    wsgi_app = app.wsgi_app
    ```

1. La deuxième partie, à la fin du fichier, est du code facultatif qui démarre le serveur de développement Flask avec des valeurs d’hôte et de port spécifiques provenant de variables d’environnement (les valeurs par défaut sont : localhost:5555) :

    ```python
    if __name__ == '__main__':
        import os
        HOST = os.environ.get('SERVER_HOST', 'localhost')
        try:
            PORT = int(os.environ.get('SERVER_PORT', '5555'))
        except ValueError:
            PORT = 5555
        app.run(HOST, PORT)
    ```

1. La troisième partie est constituée de code qui affecte une fonction à une route d’URL, ce qui signifie que la fonction fournit la ressource identifiée par l’URL. Vous définissez des routes avec le décorateur `@app.route` de Flask, dont l’argument est l’URL relative à partir de la racine du site. Comme vous pouvez le voir dans le code, la fonction retourne ici une chaîne de texte, ce qui est suffisant pour être rendu dans un navigateur. Dans les étapes qui suivent, vous affichez des pages plus riches avec du code HTML.

    ```python
    @app.route('/')
    def hello():
        """Renders a sample page."""
        return "Hello World!"
    ```

### <a name="question-what-is-the-purpose-of-the-__name__-argument-to-the-flask-class"></a>Question : À quoi sert l’argument __name__ de la classe Flask ?

Réponse : L’argument est le nom du module ou du package de l’application, et il indique à Flask où rechercher les modèles, les fichiers statiques et d’autres ressources qui appartiennent à l’application. Pour les applications contenues dans un seul module, `__name__` est toujours la valeur appropriée. Il est également important pour les extensions qui ont besoin d’informations de débogage. Pour plus d’informations et des arguments supplémentaires, consultez la [documentation sur la classe Flask](https://flask.palletsprojects.com/en/1.0.x/api/#flask.Flask) (flask.pocoo.org).

### <a name="question-can-a-function-have-more-than-one-route-decorator"></a>Question : Une fonction peut-elle avoir plusieurs décorateurs de routes ?

Réponse : Oui, vous pouvez utiliser autant de décorateurs que vous le souhaitez si la même fonction sert plusieurs routes. Par exemple, pour utiliser la fonction `hello` à la fois pour « / » et pour « /hello », utilisez le code suivant :

```python
@app.route('/')
@app.route('/hello')
def hello():
    """Renders a sample page."""
    return "Hello World!"
```

<a name="qa-url-variables"></a>

### <a name="question-how-does-flask-work-with-variable-url-routes-and-query-parameters"></a>Question : Comment Flask fonctionne-t-il avec les routes d’URL et les paramètres de requête des variables ?

Réponse : Dans une route, vous marquez toutes les variables avec `<variable_name>`, et Flask passe la variable à la fonction en utilisant un argument nommé. La variable peut faire partie du chemin de l’URL ou d’un paramètre de requête. Par exemple, une route sous la forme `'/hello/<name>` génère un argument de chaîne appelé `name` pour la fonction, et l’utilisation de `?message=<msg>` dans la route analyse la valeur donnée pour le paramètre de requête "message=" et le passe à la fonction en tant que `msg` :

```python
@app.route('/hello/<name>?message=<msg>')
def hello(name, msg):
    return "Hello " + name + "! Message is " + msg + "."
```

Pour changer the type, préfixez la variable avec `int`, `float`, `path` (qui accepte des barres obliques pour délimiter les noms de dossier) et `uuid`. Pour plus d’informations, consultez [Règles des variables](https://flask.palletsprojects.com/en/1.0.x/quickstart/#variable-rules) dans la documentation de Flask.

Les paramètres de requête sont également disponibles via la propriété `request.args`, en particulier via la méthode`request.args.get`. Pour plus d’informations, consultez [L’objet Request](https://flask.palletsprojects.com/en/1.0.x/quickstart/#the-request-object) dans la documentation de Flask.

### <a name="question-can-visual-studio-generate-a-requirementstxt-file-from-a-virtual-environment-after-i-install-other-packages"></a>Question : Est-ce que Visual Studio peut générer un fichier requirements.txt à partir d’un environnement virtuel après l’installation d’autres packages ?

Réponse : Oui. Développez le nœud **Environnements Python**, cliquez avec le bouton droit sur votre environnement virtuel, puis sélectionnez la commande **Générer requirements.txt**. Il est bon d’utiliser régulièrement cette commande quand vous modifiez l’environnement, et d’envoyer les modifications à *requirements.txt* pour le contrôle de code source ainsi que d’autres modifications de code qui dépendent de cet environnement. Si vous configurez l’intégration continue sur un serveur de builds, vous devez générer le fichier et valider les modifications chaque fois que vous modifiez l’environnement.

## <a name="step-1-5-run-the-project"></a>Étape 1-5 : Exécuter le projet

1. Dans Visual Studio, sélectionnez **Déboguer**  >  **Démarrer le débogage** (**F5**) ou utilisez le bouton **serveur Web** dans la barre d’outils (le navigateur que vous voyez peut varier) :

    ![Exécuter le bouton de la barre d’outils du serveur Web dans Visual Studio](media/tutorials-common/run-web-server-toolbar-button.png)

1. Les deux commandes affectent un numéro de port aléatoire à la variable d’environnement PORT, puis exécute `python app.py`. Le code démarre l’application en utilisant ce port dans le serveur de développement de Flask. Si Visual Studio indique **Impossible de démarrer le débogueur** avec un message informant de l’absence d’un fichier de démarrage, cliquez avec le bouton droit sur **app.py** dans **l’Explorateur de solutions** et sélectionnez **Définir comme fichier de démarrage**.

1. Quand le serveur démarre, une fenêtre de console s’ouvre et affiche le journal du serveur. Visual Studio ouvre alors automatiquement un navigateur sur `http://localhost:<port>`, où vous devez normalement voir le message rendu par la fonction `hello` :

    ![Vue par défaut du projet Flask](media/flask/step01-first-run-success.png)

1. Lorsque vous avez terminé, arrêtez le serveur en fermant la fenêtre de la console, ou en utilisant la commande **Déboguer**  >  **arrêter le débogage** dans Visual Studio.

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>Question : Quelle est la différence entre les commandes de menu Déboguer et les commandes de serveur dans le sous-menu Python du projet ?

Réponse : en plus des commandes de menu **Déboguer** et des boutons de barre d’outils, vous pouvez également lancer le serveur avec les commandes **Python** > **Exécuter le serveur** ou **Python** > **Exécuter le serveur de débogage** dans le menu contextuel du projet. Les deux commandes ouvrent une fenêtre de console dans laquelle vous voyez l’URL locale (localhost:port) du serveur en cours d’exécution. Toutefois, vous devez ouvrir manuellement un navigateur avec cette URL, et l’exécution du serveur de débogage n’entraîne pas le démarrage automatique du débogueur Visual Studio. Vous pouvez joindre un débogueur au processus en cours d’exécution ultérieurement, si vous le souhaitez, à l’aide de la commande **Déboguer**  >  **attacher au processus** .

## <a name="next-steps"></a>Étapes suivantes

À ce stade, le projet Flask de base contient le code de démarrage et le code de page dans le même fichier. Il est préférable de séparer ces deux problèmes, et également de séparer le code HTML et les données en utilisant des modèles.

> [!div class="nextstepaction"]
> [Créer une application Flask avec des vues et des modèles de pages](learn-flask-visual-studio-step-02-create-app.md)

## <a name="go-deeper"></a>Approfondir la question

- [Flask - Démarrage rapide](https://flask.palletsprojects.com/en/1.0.x/quickstart/) (flask.pocoo.org)
- Code source du tutoriel sur GitHub : [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)