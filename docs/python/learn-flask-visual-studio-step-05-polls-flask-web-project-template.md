---
title: Tutoriel d’apprentissage de Flask dans Visual Studio - étape 5, modèle de projet de sondage
titleSuffix: ''
description: Une procédure pas à pas montrant les principes de base de Flask dans le contexte de projets Visual Studio, en particulier les fonctionnalités des modèles Projet web Flask de sondage et Projet web Flask/Jade de sondage.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
monikerRange: vs-2017
ms.workload:
- python
- data-science
ms.openlocfilehash: fd67e527ccf62de17dc15a5415f573c9622a51e9
ms.sourcegitcommit: f1dff6c4532c43b0444aa12ea57e90bb7dba6fba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805976"
---
# <a name="step-5-use-the-polls-flask-web-project-template"></a>Étape 5 : Utiliser le modèle de projet web Flask de sondage

**Étape précédente : [Utiliser le modèle Projet web Flask complet](learn-flask-visual-studio-step-04-full-flask-project-template.md)**

Une fois que vous avez compris le modèle « Projet web Flask » de Visual Studio, vous pouvez passer au troisième modèle Flask, « Projet web Flask de sondage », qui est créé à partir de la même base de code.

Dans cette section, vous apprenez comment :

> [!div class="checklist"]
> - Créer un projet à partir du modèle et initialiser la base de données (étape 5-1)
> - Comprendre les modèles de données (étape 5-2)
> - Comprendre les magasins de données sous-jacents (étape 5-3)
> - Comprendre les vues des détails et des résultats des sondages (étape 5-4)

Visual Studio fournit aussi un projet à partir du modèle « Projet web Flask/Jade de sondage » qui produit une application identique, mais utilise l’extension Jade pour le moteur de création de modèles Jinja. Pour plus d’informations, consultez [Étape 4 - Le modèle de projet web Flask/Jade](learn-flask-visual-studio-step-04-full-flask-project-template.md#the-flaskjade-web-project-template).

## <a name="step-5-1-create-the-project"></a>Étape 5-1 : Créer le projet

1. Dans Visual Studio, accédez à **Explorateur de solutions**, cliquez avec le bouton droit sur la solution **LearningFlask** créée précédemment dans ce didacticiel, puis sélectionnez **Ajouter**  >  **un nouveau projet**. (Sinon, si vous souhaitez utiliser une nouvelle solution, sélectionnez **fichier**  >  **Nouveau**  >  **Projet** à la place.)

1. Dans la boîte de dialogue Nouveau projet, recherchez et sélectionnez le modèle de **projet Web de la fiole sondages** , appelez le projet « FlaskPolls », puis sélectionnez **OK**.

1. Comme les autres modèles de projet dans Visual Studio, le modèle « Projet web Flask de sondage » inclut un fichier *requirements.txt*. Visual Studio vous demande où installer ces dépendances. Choisissez l’option, **Installer dans un environnement virtuel** et dans la boîte de dialogue **Ajouter un environnement virtuel**, sélectionnez **Créer** pour accepter les valeurs par défaut. (Ce modèle nécessite Flask, ainsi que les packages azure-storage et pymongo ; le modèle « Projet web Flask/Jade de sondage » nécessite aussi pyjade.)

1. Définissez le projet **FlaskPolls** comme valeur par défaut pour la solution Visual Studio en cliquant avec le bouton droit sur ce projet dans **Explorateur de solutions** et en sélectionnant **définir comme projet de démarrage**. Le projet de start-up, affiché en gras est ce qui est exécuté lorsque vous démarrez le débogueur.

1. Sélectionnez **Déboguer**  >  **Démarrer le débogage** (**F5**) ou utilisez le bouton **serveur Web** dans la barre d’outils pour exécuter le serveur :

    ![Exécuter le bouton de la barre d’outils du serveur Web dans Visual Studio](media/django/run-web-server-toolbar-button.png)

1. L’application créée par le modèle dispose de trois pages, Accueil, À propos et Contact, entre lesquelles vous naviguez à l’aide de la barre de navigation supérieure. Prenez une minute ou deux pour examiner les différentes parties de l’application (les pages About et Contact sont très similaires à celles du « Projet web Flask » et ne sont pas abordées plus en détail).

    ![Vue complète de l’application Projet web Flask de sondage](media/flask/step06-full-app-view.png)

1. Dans la page d’accueil, le bouton **Create Sample Polls** (Créer des exemples de sondages) initialise le magasin de données de l’application avec trois sondages différents qui sont décrits dans la page *models/samples.json*. Par défaut, l’application utilise une base de données en mémoire (comme montré dans la page About), qui est réinitialisée à chaque redémarrage de l’application. L’application contient également le code nécessaire pour fonctionner avec Stockage Azure et MongoDB, comme décrit plus loin dans cet article.

1. Une fois que vous avez initialisé le magasin de données, vous pouvez voter dans les différents sondages comme indiqué sur la page d’accueil (la barre de navigation et le pied de page sont omis par souci de concision) :

    ![Vue de l’application Polls une fois que le magasin de données est initialisé](media/flask/step06-polls-initialized.png)

1. Le fait de sélectionner un sondage affiche ses choix spécifiques :

    ![Interface de vote pour un sondage](media/flask/step06-polls-voting-interface.png)

1. Une fois que vous votez, l’application affiche une page de résultats et vous permet de revoter :

    ![Vue des résultats après le vote](media/flask/step06-polls-results.png)

1. Vous pouvez laisser l’application s’exécuter pour les sections qui suivent.

    Si vous souhaitez arrêter l’application et [valider des modifications dans le contrôle de code source](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control), ouvrez tout d’abord la page **Modifications** dans **Team Explorer**, cliquez avec le bouton droit sur le dossier de l’environnement virtuel (probablement **env**), puis sélectionnez **Ignorer ces éléments locaux**.

### <a name="examine-the-project-contents"></a>Examiner le contenu du projet

Comme mentionné précédemment. la majorité de ce qui se trouve dans un projet créé à partir du modèle « Projet web Flask de sondage » (et du modèle « Projet web Flask/Jade de sondage ») devrait vous être familière si vous avez exploré les autres modèles de projet dans Visual Studio. Les étapes supplémentaires dans cet article résument les modifications plus importantes et les ajouts, à savoir les modèles de données et les vues supplémentaires.

## <a name="step-5-2-understand-the-data-models"></a>Étape 5-2 : Comprendre les modèles de données

Les modèles de données de l’application sont des classes python nommées Poll et Choice, qui sont définies dans *Models/ \_ \_ init \_ \_ . py*. Une instance de Poll représente une question, pour laquelle une collection d’instances de Choice représente les réponses disponibles. Une instance de Poll gère également le nombre total de voix (pour tous les choix) et une méthode pour calculer des statistiques qui sont utilisées pour générer des vues :

```python
class Poll(object):
    """A poll object for use in the application views and repository."""
    def __init__(self, key=u'', text=u''):
        """Initializes the poll."""
        self.key = key
        self.text = text
        self.choices = []
        self.total_votes = None

    def calculate_stats(self):
        """Calculates some statistics for use in the application views."""
        total = 0
        for choice in self.choices:
            total += choice.votes
        for choice in self.choices:
            choice.votes_percentage = choice.votes / float(total) * 100 \
                if total > 0 else 0
        self.total_votes = total

class Choice(object):
    """A poll choice object for use in the application views and repository."""
    def __init__(self, key=u'', text=u'', votes=0):
        """Initializes the poll choice."""
        self.key = key
        self.text = text
        self.votes = votes
        self.votes_percentage = None
```

Ces modèles de données sont des abstractions génériques qui permettent aux vues de l’application d’utiliser différents types de magasins de données sous-jacents, qui sont décrits dans l’étape suivante.

## <a name="step-5-3-understand-the-backing-data-stores"></a>Étape 5-3 : Comprendre les magasins de données sous-jacents

L’application créée par le modèle « Projet web Flask de sondage » peut s’exécuter sur une banque de données en mémoire, sur Stockage Table Azure ou sur une base de données MongoDB.

Le mécanisme de stockage des données fonctionne comme suit :

1. Le type de dépôt est spécifié via la variable d’environnement `REPOSITORY_NAME`, qui peut être définie sur « memory », « azuretablestore » ou « mongodb ». Le code dans *settings.py* récupère le nom, en utilisant « memory » par défaut. Si vous voulez changer le magasin sous-jacent, vous devez définir la variable d’environnement et redémarrer l’application.

    ```python
    from os import environ
    REPOSITORY_NAME = environ.get('REPOSITORY_NAME', 'memory')
    ```

1. Le code de *settings.py* initialise ensuite un objet `REPOSITORY_SETTINGS`. Si vous voulez utiliser le magasin de tables Azure ou MongoDB, vous devez d’abord initialiser ces magasins de données ailleurs, puis définir les variables d’environnement nécessaires qui indiquent à l’application comment se connecter au magasin :

    ```python
    if REPOSITORY_NAME == 'azuretablestorage':
        REPOSITORY_SETTINGS = {
            'STORAGE_NAME': environ.get('STORAGE_NAME', ''),
            'STORAGE_KEY': environ.get('STORAGE_KEY', ''),
            'STORAGE_TABLE_POLL': environ.get('STORAGE_TABLE_POLL', 'polls'),
            'STORAGE_TABLE_CHOICE': environ.get('STORAGE_TABLE_CHOICE', 'choices'),
        }
    elif REPOSITORY_NAME == 'mongodb':
        REPOSITORY_SETTINGS = {
            'MONGODB_HOST': environ.get('MONGODB_HOST', None),
            'MONGODB_DATABASE': environ.get('MONGODB_DATABASE', 'polls'),
            'MONGODB_COLLECTION': environ.get('MONGODB_COLLECTION', 'polls'),
        }
    elif REPOSITORY_NAME == 'memory':
        REPOSITORY_SETTINGS = {}
    else:
        raise ValueError('Unknown repository.')
    ```

1. Dans *views.py*, l’application appelle une méthode de fabrique pour initialiser un objet `Repository` avec le nom et les paramètres du magasin de données :

    ```python
    from FlaskPolls.models import PollNotFound
    from FlaskPolls.models.factory import create_repository
    from FlaskPolls.settings import REPOSITORY_NAME, REPOSITORY_SETTINGS

    repository = create_repository(REPOSITORY_NAME, REPOSITORY_SETTINGS)
    ```

1. La méthode `factory.create_repository` se trouve dans *models\factory.py*, qui importe simplement le module du dépôt approprié, puis crée une instance de `Repository` :

    ```python
    def create_repository(name, settings):
        """Creates a repository from its name and settings. The settings
        is a dictionary where the keys are different for every type of repository.
        See each repository for details on the required settings."""
        if name == 'azuretablestorage':
            from .azuretablestorage import Repository
        elif name == 'mongodb':
            from .mongodb import Repository
        elif name == 'memory':
            from .memory import Repository
        else:
            raise ValueError('Unknown repository.')

        return Repository(settings)
    ```

1. Les implémentations de la classe `Repository` qui sont propres à chaque magasin de données se trouvent dans *models\azuretablestorage.py*, *models\mongodb.py* et *models\memory.py*. L’implémentation Stockage Azure utilise le package azure-storage ; l’implémentation MongoDB utilise le package pymongo. Comme indiqué à l’étape 5-1, les deux packages sont inclus dans le fichier *requirements.txt* du modèle de projet. L’exploration des détails est laissée au lecteur à titre d’exercice.

En bref, la classe `Repository` abstrait les spécificités du magasin de données, et l’application utilise des variables d’environnement au moment de l’exécution pour sélectionner et configurer celle des trois implémentations à utiliser.

Les étapes suivantes ajoutent la prise en charge d’un magasin de données autre que les trois magasins fournis par le modèle de projet (si vous le souhaitez) :

1. Copiez *memory.py* dans un nouveau fichier de façon à disposer de l’interface de base pour la classe `Repository`.
1. Modifiez l’implémentation de la classe en fonction du magasin de données que vous utilisez.
1. Modifiez *factory.py* en y ajoutant un autre cas `elif` qui reconnaît le nom du magasin de données que vous avez ajouté et qui importe le module approprié.
1. Modifiez *settings.py* de façon à reconnaître un autre nom dans la variable d’environnement `REPOSITORY_NAME` et à initialiser `REPOSITORY_SETTINGS` en conséquence.

### <a name="seed-the-data-store-from-samplesjson"></a>Amorcer le magasin de données à partir de samples.json

Au départ, tout magasin de données choisi ne contient aucune interrogation, de sorte que la page d’origine de l’application affiche le message **aucune interrogation disponible** avec le bouton **créer des exemples d’interrogations** . Cependant, une fois que vous avez sélectionné le bouton, la vue change et montre les sondages disponibles. Ce changement se produit via des balises conditionnelles dans *templates\index.html* (certaines lignes vides sont omises par souci de concision) :

```html
{% extends "layout.html" %}
{% block content %}
<h2>{{title}}.</h2>

{% if polls %}
<table class="table table-hover">
    <tbody>
        {% for poll in polls %}
        <tr>
            <td>
                <a href="/poll/{{poll.key}}">{{poll.text}}</a>
            </td>
        </tr>
        {% endfor %}
    </tbody>
</table>
{% else %}
<p>No polls available.</p>
<br />
<form action="/seed" method="post">
    <button class="btn btn-primary" type="submit">Create Sample Polls</button>
</form>
{% endif %}
{% endblock %}
```

La variable `polls` du modèle provient d’un appel à `repository.get_polls`, qui ne retourne rien jusqu’à ce que le magasin de données soit initialisé.

Le fait de sélectionner le bouton **Create Sample Polls** vous fait accéder à l’URL /seed. Le gestionnaire pour cette route est défini dans *views.py* :

```python
@app.route('/seed', methods=['POST'])
def seed():
    """Seeds the database with sample polls."""
    repository.add_sample_polls()
    return redirect('/')
```

L’appel à `repository.add_sample_polls()` aboutit à une des implémentations de `Repository` spécifique au magasin de données choisi. Chaque implémentation appelle la `_load_samples_json` méthode trouvée dans *Models \_ \_ init \_ \_ . py* pour charger le *models\samples.jssur* le fichier en mémoire, puis itère au sein de ces données pour créer les `Poll` objets et nécessaires `Choice` dans le magasin de données.

Une fois ce processus terminé, l’instruction `redirect('/')` de la méthode `seed` revient à la page d’accueil. Comme `repository.get_polls` retourne maintenant un objet de données, les balises conditionnelles dans *templates\index.html* affichent maintenant une table contenant les sondages.

### <a name="question-how-does-one-add-new-polls-to-the-app"></a>Question : Comment ajouter de nouveaux sondages à l’application ?

Réponse : L’application telle qu’elle est fournie via le modèle de projet n’inclut pas de fonctionnalité pour ajouter ou modifier des sondages. Vous pouvez modifier *models\samples.json* pour créer des données d’initialisation, mais cela signifierait une réinitialisation du magasin de données. Pour implémenter des fonctionnalités de modification, vous devez étendre l’interface de la classe `Repository` avec des méthodes pour créer les instances nécessaires de `Choice` et de `Poll`, puis implémenter une interface utilisateur dans des pages supplémentaires qui utilisent ces méthodes.

## <a name="step-5-4-understand-the-poll-detail-and-results-views"></a>Étape 5-5-4 : Comprendre les vues des détails et des résultats des sondages

La plupart des vues générées par les modèles « Projet web Flask de sondage » et « Projet web Flask/Jade de sondage », comme les vues des pages About et Contact, sont très similaires aux vues créées par le modèle « Projet web Flask » (ou « Projet web Flask/Jade ») avec lequel vous avez travaillé précédemment dans ce tutoriel. Dans la section précédente, vous avez également découvert comment la page d’accueil est implémentée pour afficher le bouton d’initialisation ou la liste des sondages.

Il reste ici à examiner les vues des votes (détails) et des résultats d’un sondage individuel.

Lorsque vous sélectionnez un sondage à partir de la page d’origine, l’application accède à l’URL/Poll/ \<key\> où *clé* est l’identificateur unique d’une interrogation. Dans *views.py*, vous pouvez voir que la fonction `details` doit gérer ce routage d’URL pour les requêtes GET et POST. Vous pouvez également voir que l’utilisation de `<key>` dans la route de l’URL mappe toutes les routes de ce formulaire à la même fonction et génère un argument du même nom pour la fonction :

```python
@app.route('/poll/<key>', methods=['GET', 'POST'])
def details(key):
    """Renders the poll details page."""
    error_message = ''
    if request.method == 'POST':
        try:
            choice_key = request.form['choice']
            repository.increment_vote(key, choice_key)
            return redirect('/results/{0}'.format(key))
        except KeyError:
            error_message = 'Please make a selection.'

    return render_template(
        'details.html',
        title='Poll',
        year=datetime.now().year,
        poll=repository.get_poll(key),
        error_message=error_message,
    )
```

Pour afficher un sondage (requêtes GET), cette fonction appelle simplement *templates\details.html*, qui boucle sur le tableau `choices` du sondage, en créant une case d’option pour chaque choix.

```html
{% extends "layout.html" %}

{% block content %}

<h2>{{poll.text}}</h2>
<br />

{% if error_message %}
<p class="text-danger">{{error_message}}</p>
{% endif %}

<form action="/poll/{{poll.key}}" method="post">
    {% for choice in poll.choices %}
    <div class="radio">
        <label>
            <input type="radio" name="choice" id="choice{{choice.key}}" value="{{choice.key}}" />
            {{ choice.text }}
        </label>
    </div>
    {% endfor %}
    <br />
    <button class="btn btn-primary" type="submit">Vote</button>
</form>

{% endblock %}
```

Comme le bouton **Vote** (Voter) est associé à `type="submit"`, le fait de le sélectionner génère une requête POST sur la même URL qui est routée une fois de plus vers la fonction `details`. Cette fois, cependant, il extrait le choix à partir des données de formulaire et redirige vers/Results/ \<choice\> .

L' \<key\> URL/Results/est ensuite routée vers la `results` fonction dans *views.py*, qui appelle ensuite la méthode de l’interrogation `calculate_stats` et utilise *templates\results.html* pour le rendu :

```python
@app.route('/results/<key>')
def results(key):
    """Renders the results page."""
    poll = repository.get_poll(key)
    poll.calculate_stats()
    return render_template(
        'results.html',
        title='Results',
        year=datetime.now().year,
        poll=poll,
    )
```

Le modèle *results.html* boucle quant à lui simplement dans les choix du sondage et génère une barre de progression pour chacun d’eux :

```html
{% extends "layout.html" %}

{% block content %}

<h2>{{poll.text}}</h2>
<br />

{% for choice in poll.choices %}
<div class="row">
    <div class="col-sm-5">{{choice.text}}</div>
    <div class="col-sm-5">
        <div class="progress">
            <div class="progress-bar" role="progressbar" aria-valuenow="{{choice.votes}}" aria-valuemin="0" aria-valuemax="{{poll.total_votes}}" style="width: {{choice.votes_percentage}}%;">
                {{choice.votes}}
            </div>
        </div>
    </div>
</div>
{% endfor %}

<br />
<a class="btn btn-primary" href="/poll/{{poll.key}}">Vote again?</a>

{% endblock %}
```

## <a name="next-steps"></a>Étapes suivantes

> [!Note]
> Si vous validez votre solution Visual Studio lors du contrôle de code source pendant ce tutoriel, c’est le bon moment pour effectuer une autre validation. Votre solution doit correspondre au code source du tutoriel sur GitHub : [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask).

Vous avez maintenant parcouru l’intégralité des modèles « Projet web Flask vide », « Projet web Flask[/Jade] » et « Projet web Flask[/Jade] de sondage » dans Visual Studio. Vous avez découvert tous les concepts de base de Flask, comme l’utilisation de vues, de modèles et du routage, et vous avez vu comment utiliser des magasins de données sous-jacents. Vous devez maintenant être en mesure de commencer à créer vous-même une application web avec les vues et les modèles dont vous avez besoin.

L’exécution d’une application web sur votre ordinateur de développement n’est qu’une étape de la mise de l’application à la disposition de vos clients. Les étapes suivantes peuvent inclure les tâches suivantes :

- Déployer l’application web sur un serveur de production, tels qu’Azure App Service. Voir [Publier sur Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md).

- Ajoutez une implémentation du dépôt qui utilise un autre magasin de données de niveau production, comme PostgreSQL, MySQL et SQL Server (chacun pouvant être hébergé sur Azure). Vous pouvez aussi utiliser [Azure SDK pour Python](/azure/python/) pour travailler avec des services de stockage Azure, comme Stockage Table ou Stockage Blob, ainsi que Cosmos DB.

- Configurez un pipeline d’intégration continue ou de déploiement continu sur un service comme Azure DevOps. En plus de l’utilisation du contrôle de code source (via Azure Repos, GitHub ou ailleurs), vous pouvez configurer un projet Azure DevOps pour exécuter automatiquement vos tests unitaires, dans le cadre des prérequis à la mise en production. Vous pouvez également configurer le pipeline pour effectuer le déploiement sur un serveur de préproduction pour des tests supplémentaires, avant le déploiement en production. Par ailleurs, Azure DevOps s’intègre aux solutions de supervision comme App Insights, et termine le cycle avec des outils de planification agile. Pour plus d’informations, consultez [Créer un pipeline CI/CD pour Python avec Azure DevOps Projects](/azure/devops-project/azure-devops-project-python?view=vsts&preserve-view=true), ainsi que la [documentation générale sur Azure DevOps ](/azure/devops/?view=vsts&preserve-view=true).
