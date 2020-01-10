---
title: Tutoriel d’apprentissage de Django dans Visual Studio - étape 6, modèle de projet Sondage
titleSuffix: ''
description: Une procédure pas à pas des principes de base de Django dans le contexte de projets Visual Studio, en particulier les fonctionnalités du modèle de projet web Django telles que la personnalisation de l’administration.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: c1fe3db702508267e96dc79f2f789a17a7edf98b
ms.sourcegitcommit: 789430e18dfe8e5f7db19273e7298af2f078c0dc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75755577"
---
# <a name="step-6-use-the-polls-django-web-project-template"></a>Étape 6 : Utiliser le modèle Sondages du projet web Django

**Étape précédente : [authentifier les utilisateurs dans Django](learn-django-in-visual-studio-step-05-django-authentication.md)**

Une fois que vous avez compris le modèle « Projet web Django » de Visual Studio, vous pouvez vous consacrer au troisième modèle Django, le « Projet web Django de sondage », qui est basé sur le même code et montre comment travailler avec une base de données.

Dans cette section, vous apprenez comment :

> [!div class="checklist"]
> - créer un projet à partir du modèle et initialiser la base de données (étape 6-1) ;
> - comprendre les modèles de données (étape 6-2) ;
> - appliquer des migrations (étape 6-3) ;
> - comprendre les affichages et les modèles de page créés par le modèle de projet (étape 6-4) ;
> - créer une interface d’administration personnalisée (étape 6-5).

Un projet créé à l’aide de ce modèle est similaire à ce que vous pouvez obtenir en suivant le didacticiel [écriture de votre première application Django](https://docs.djangoproject.com/en/2.0/intro/tutorial01/) dans la documentation Django. L’application Web se compose d’un site public qui permet aux utilisateurs d’afficher les sondages et de voter, ainsi qu’une interface d’administration personnalisée via laquelle vous pouvez gérer les sondages. Il utilise le même système d’authentification que le modèle « Projet web de Django » et utilise plus la base de données en implémentant des modèles Django comme parcourus dans les sections suivantes.

## <a name="step-6-1-create-the-project-and-initialize-the-database"></a>Étape 6-1 : créer le projet et d’initialiser la base de données

1. Dans Visual Studio, accédez à **Explorateur de solutions**, cliquez avec le bouton droit sur la solution **LearningDjango** créée précédemment dans ce tutoriel, puis sélectionnez **Ajouter** > **Nouveau projet**. (Ou bien, si vous souhaitez utiliser une nouvelle solution, sélectionnez **Fichier** > **Nouveau** > **Projet** à la place.)

1. Dans la boîte de dialogue Nouveau projet, recherchez et sélectionnez le modèle **Projet web Django de sondage**, appelez le projet « DjangoPolls » et sélectionnez **OK**.

1. Comme les autres modèles de projet dans Visual Studio, le modèle « Projet web Django de sondage » inclut un fichier *requirements.txt*. Des invites de Visual Studio vous demanderont où installer ces dépendances. Choisissez l’option, **Installer dans un environnement virtuel** et dans la boîte de dialogue **Ajouter un environnement virtuel**, sélectionnez **Créer** pour accepter les valeurs par défaut.

1. Une fois la configuration de l’environnement virtuel terminée par Python, suivez les instructions dans la liste affichée *readme.html* pour initialiser la base de données et créer un superutilisateur Django (autrement dit, un administrateur). Les étapes à suivre sont les suivantes : commencez par cliquer avec le bouton droit sur le projet **DjangoPolls** dans **l’Explorateur de solutions**, puis sélectionnez la commande **Python** > **Django – Migrer**, recliquez avec le bouton droit sur le projet, sélectionnez la commande **Python** > **Django – Créer un superutilisateur** et suivez les invites. (Si vous essayez d’abord de créer un superutilisateur, vous verrez une erreur, car la base de données n’a pas été initialisée.)

1. Définissez le projet **DjangoPolls** en tant que projet par défaut pour la solution Visual Studio en cliquant avec le bouton droit sur ce projet dans **l’Explorateur de solutions** et en sélectionnant **Définir en tant que projet de démarrage**. Le projet de start-up, affiché en gras est ce qui est exécuté lorsque vous démarrez le débogueur.

1. Sélectionnez **Déboguer** > **Démarrer le débogage** (**F5**) ou utilisez le bouton **Serveur Web** dans la barre d’outils pour exécuter le serveur :

    ![Exécuter le bouton de la barre d’outils du serveur Web dans Visual Studio](media/django/run-web-server-toolbar-button.png)

1. L’application créée par le modèle dispose de trois pages, Accueil, À propos et Contact, entre lesquelles vous naviguez à l’aide de la barre de navigation supérieure. Prenez une minute ou deux pour examiner les différentes parties de l’application (les pages À propos et Contact sont très similaires à celles du « Projet web Django » et ne sont pas abordées plus en détail).

    ![Affichage complet du navigateur de l’application du Projet web Django de sondage](media/django/step06-full-app-view.png)

1. Sélectionnez également le lien **Administration** dans la barre de navigation, qui affiche un écran de connexion pour montrer que l’interface d’administration est accessible uniquement à des administrateurs authentifiés. Utilisez les informations d’identification de superutilisateur, et vous êtes redirigé vers la page « / admin », qui est activée par défaut lors de l’utilisation de ce modèle de projet.

    ![Affichage complet de l’administration de l’application du Projet web Django de sondage](media/django/step06-polls-administrative-interface.png)

1. Vous pouvez laisser l’application s’exécuter pour les sections qui suivent.

    Si vous souhaitez arrêter l’application et [valider des modifications dans le contrôle de code source](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control), ouvrez tout d’abord la page **Modifications** dans **Team Explorer**, cliquez avec le bouton droit sur le dossier de l’environnement virtuel (probablement **env**), puis sélectionnez **Ignorer ces éléments locaux**.

### <a name="examine-the-project-contents"></a>Examiner le contenu du projet

Comme mentionné précédemment. La majorité de ce qui se trouve dans un projet créé à partir du modèle « Projet web Django de sondage » devrait vous être familière si vous avez exploré les modèles de projet dans Visual Studio. Les étapes supplémentaires dans cet article résument les modifications plus importantes et les ajouts, à savoir les modèles de données et les vues supplémentaires.

### <a name="question-what-does-the-django-migrate-command-do"></a>Question : Que fait la commande Django – Migrer ?

Réponse : La commande **Django – Migrer** exécute en particulier la commande `manage.py migrate`, qui exécute dans le dossier *app/migrations* tous les scripts qui ne l’ont pas été précédemment. Dans ce cas, la commande exécute le script *0001_initial.py* dans ce dossier pour configurer le schéma nécessaire dans la base de données.

Le script de migration proprement dit est créé par la commande `manage.py makemigrations`, qui analyse le fichier *models.py* de l’application, le compare à l’état actuel de la base de données, puis génère les scripts nécessaires pour migrer le schéma de base de données afin de faire correspondre les modèles actuels. Cette fonctionnalité de Django est très performante si vous mettez à jour et modifiez vos modèles au fur et à mesure. En générant et en exécutant des migrations, vous synchronisez facilement les modèles et la base de données.

Vous travaillerez sur une migration à l’étape 6-3 plus loin dans cet article.

## <a name="step-6-2-understand-data-models"></a>Étape 6-2 : comprendre les modèles de données

Les modèles de l’application nommés Poll et Choice, sont définis dans *app/models.py*. Chacun est une classe Python dérivée de `django.db.models.Model` et utilisant les méthodes de la classe `models`, telles que `CharField` et `IntegerField`, pour définir dans le modèle des champs mappés aux colonnes de la base de données.

```python
from django.db import models
from django.db.models import Sum

class Poll(models.Model):
    """A poll object for use in the application views and repository."""
    text = models.CharField(max_length=200)
    pub_date = models.DateTimeField('date published')

    def total_votes(self):
        """Calculates the total number of votes for this poll."""
        return self.choice_set.aggregate(Sum('votes'))['votes__sum']

    def __unicode__(self):
        """Returns a string representation of a poll."""
        return self.text

class Choice(models.Model):
    """A poll choice object for use in the application views and repository."""
    poll = models.ForeignKey(Poll)
    text = models.CharField(max_length=200)
    votes = models.IntegerField(default=0)

    def votes_percentage(self):
        """Calculates the percentage of votes for this choice."""
        total = self.poll.total_votes()
        return self.votes / float(total) * 100 if total > 0 else 0

    def __unicode__(self):
        """Returns a string representation of a choice."""
        return self.text
```

Comme vous pouvez le voir, un sondage conserve une description dans son champ `text` et une date de publication dans `pub_date`. Ces champs sont les seuls qui existent pour l’interrogation dans la base de données ; le champ `total_votes` est calculé au moment de l’exécution.

Un choix est lié à un sondage via le champ `poll`, contient une description dans `text`et un décompte de ce choix dans `votes`. Le champ `votes_percentage` est calculé au moment de l’exécution et est introuvable dans la base de données.

La liste complète des types de champ est `CharField` (texte limité) `TextField` (texte illimité), `EmailField`, `URLField`, `DateTimeField`, `IntegerField`, `DecimalField`, `BooleanField`, `ForeignKey` et `ManyToMany`. Chaque champ utilise certains attributs, tels que `max_length`. L’attribut `blank=True` signifie que le champ est facultatif ; `null=true` signifie qu’une valeur est facultative. Il existe également un attribut `choices` qui les valeurs à des valeurs dans un tableau de valeur de données/des tuples de valeurs affichées. (Consultez la [Référence de champ de modèle](https://docs.djangoproject.com/en/2.0/ref/models/fields/) dans la documentation Django.)

Vous pouvez vérifier exactement ce qui est stocké dans la base de données en examinant le fichier *db.sqlite3* dans le projet à l’aide d’un outil tel que le [navigateur SQLite](https://sqlitebrowser.org/). Dans la base de données, vous voyez qu’un champ de clé étrangère comme `poll` dans le modèle Choice est stocké en tant que `poll_id`; Django gère le mappage automatiquement.

En général, l’utilisation de votre base de données dans Django signifie l’utilisation exclusive par le biais de vos modèles, afin que Django puisse gérer la base de données sous-jacente en votre nom.

### <a name="seed-the-database-from-samplesjson"></a>Amorcer la base de données à partir de samples.json

Au départ, la base de données ne contient aucun sondage. Vous pouvez utiliser l’interface d’administration sous l’URL « /admin » pour ajouter des sondages manuellement, et vous pouvez aussi visiter la page « /seed » sur le site en cours d’exécution pour amorcer la base de données avec des sondages définis dans le fichier *samples.json* de l’application.

Le fichier *urls.py* du projet Django a un modèle d’URL ajouté, `url(r'^seed$', app.views.seed, name='seed'),`. L’affichage `seed` dans *app/views.py* charge le fichier *samples.json* et crée les objets de modèle nécessaires. Django crée ensuite automatiquement les enregistrements correspondants dans la base de données sous-jacente.

Notez l’utilisation de l’élément décoratif `@login_required` afin d’indiquer le niveau d’autorisation pour l’affichage.

```python
@login_required
def seed(request):
    """Seeds the database with sample polls."""
    samples_path = path.join(path.dirname(__file__), 'samples.json')
    with open(samples_path, 'r') as samples_file:
        samples_polls = json.load(samples_file)

    for sample_poll in samples_polls:
        poll = Poll()
        poll.text = sample_poll['text']
        poll.pub_date = timezone.now()
        poll.save()

        for sample_choice in sample_poll['choices']:
            choice = Choice()
            choice.poll = poll
            choice.text = sample_choice
            choice.votes = 0
            choice.save()

    return HttpResponseRedirect(reverse('app:home'))
```

Pour voir l’effet, commencez par exécuter l’application pour vérifier qu’aucun sondage n’existe encore. Accédez ensuite à l’URL « / seed » et, lorsque l’application revient à la page d’accueil, vous devez voir que des sondages sont maintenant disponibles. Là encore, n’hésitez pas à examiner le fichier brut *db.sqlite3* avec un outil tel que le [navigateur SQLite](https://sqlitebrowser.org/).

![Application de projet web Django de sondage avec base de données amorcée](media/django/step06-app-with-seeded-database.png)

### <a name="question-is-it-possible-to-initialize-the-database-using-the-django-administrative-utility"></a>Question : Peut-on initialiser la base de données avec l’utilitaire d’administration Django ?

Réponse : Oui, vous pouvez utiliser la [commande django-admin loaddata](https://docs.djangoproject.com/en/2.0/ref/django-admin/#loaddata) pour accomplir la même tâche que la page d’amorçage dans l’application. Lorsque vous travaillez sur une application web complète, vous pouvez utiliser une combinaison des deux méthodes : initialisation d’une base de données à partir de la ligne de commande, puis conversion de la page d’amorçage de départ en API à laquelle vous pouvez envoyer n’importe quel autre fichier JSON arbitraire au lieu de vous appuyer sur un fichier codé en dur.

## <a name="step-6-3-use-migrations"></a>Étape 6-3 : utiliser les migrations

Quand vous avez exécuté la commande `manage.py makemigrations` (à l’aide du menu contextuel dans Visual Studio) après avoir créé le projet, Django a créé le fichier *app/migrations/0001_initial.py*. Ce fichier contient un script qui crée les tables de base de données initiale.

Étant donné que vous allez inévitablement modifier vos modèles au fil du temps, Django facilite le maintien à jour du schéma de base de données sous-jacente avec ces modèles. Le workflow général est le suivant :

1. Apporter des modifications aux modèles dans votre fichier *models.py*.
1. Dans Visual Studio, cliquez avec le bouton droit sur le projet dans **l’Explorateur de solutions** et sélectionnez la commande **Python** > **Django – Migrer**. Comme décrit précédemment, cette commande génère des scripts dans *app/migrations* pour migrer la base de données de son état actuel vers le nouvel état.
1. Pour appliquer les scripts à la base de données, cliquez à nouveau avec le bouton droit sur le projet et sélectionnez **Python** > **Django – Migrer**.

Django suit les migrations déjà appliquées à chaque base de données et applique donc les migrations nécessaires lorsque vous exécutez la commande Migrer. Si vous créez une base de données vide, par exemple, l’exécution de la commande de migration la mettra à jour avec vos modèles actuels en appliquant chaque script de migration. De même, si vous effectuez plusieurs modifications de modèle et générez des migrations sur un ordinateur de développement, vous pouvez ensuite appliquer les migrations cumulatives à votre base de données de production en exécutant la commande de migration sur votre serveur de production. Django applique à nouveau uniquement les scripts de migration qui ont été générés depuis la dernière migration de la base de données de production.

Pour voir l’effet de la modification d’un modèle, essayez de suivre les étapes suivantes :

1. Ajoutez un champ d’auteur facultatif pour le modèle Poll dans *app/models.py* en ajoutant la ligne suivante après le champ `pub_date` afin d’ajouter un champ `author` facultatif :

    ```python
    author = models.CharField(max_length=100, blank=True)
    ```

1. Enregistrez le fichier, cliquez avec le bouton droit sur le projet **DjangoPolls** dans **l’Explorateur de solutions** et sélectionnez la commande **Python** > **Django – Migrer**.
1. Sélectionnez la commande **Projet** > **Afficher tous les fichiers** pour afficher le script qui vient d’être généré dans le dossier **migrations**, dont le nom commence par **002_auto_** . Cliquez avec le bouton droit sur ce fichier et sélectionnez **Inclure dans le projet**. Vous pouvez ensuite sélectionner à nouveau **Projet** > **Afficher tous les fichiers** pour restaurer l’affichage d’origine. (Consultez la deuxième question ci-dessous pour plus d’informations sur cette étape.)
1. Si vous le souhaitez, ouvrez ce fichier pour examiner comment Django écrit la modification de l’état du modèle précédent vers le nouvel état.
1. Cliquez à nouveau avec le bouton droit sur le projet Visual Studio et sélectionnez **Python** > **Django – Migrer** pour appliquer les modifications à la base de données.
1. Si vous le souhaitez, ouvrez la base de données dans une visionneuse appropriée pour confirmer la modification.

En général, fonctionnalité de migration de Django signifie que vous ne devez jamais gérer votre schéma de base de données manuellement. Vous devez juste apporter des modifications à vos modèles, générer les scripts de migration et les appliquer à l’aide de la commande de migration.

### <a name="question-what-happens-if-i-forget-to-run-the-migrate-command-after-making-changes-to-models"></a>Question : Que se passe-t-il si j’ai oublié d’exécuter la commande de migration après avoir modifié des modèles ?

Réponse : si les modèles ne correspondent pas à ce qui se trouve dans la base de données, Django échoue au moment de l’exécution avec les exceptions appropriées. Par exemple, si vous oubliez de migrer la modification de modèle indiquée dans la section précédente, vous voyez une erreur **no such column: app_poll.author** :

![Erreur affichée quand une modification de modèle n’a pas été migrée](media/django/step06-exception-when-forgetting-to-migrate.png).

### <a name="question-why-doesnt-solution-explorer-show-newly-generated-scripts-after-running-django-make-migrations"></a>Question : Pourquoi l’Explorateur de solutions n’affiche-t-il pas des scripts qui viennent d’être générés après l’exécution de Django – Migrer ?

Réponse : Bien que les nouveaux scripts générés existent dans le dossier *app/migrations* et soient appliqués quand vous exécutez la commande **Django – Migrer**, ils n’apparaissent pas automatiquement dans **l’Explorateur de solutions**, car ils n’ont pas été ajoutés au projet Visual Studio. Pour les rendre visibles, sélectionnez d’abord la commande de menu **Projet** > **Afficher tous les fichiers** ou le bouton de barre d’outils encadré dans l’image ci-dessous. Suite à cette commande, **l’Explorateur de solutions** affiche tous les fichiers dans le dossier du projet, avec une icône en pointillés qui entoure les éléments qui n’ont pas été ajoutés au projet proprement dit. Cliquez sur les fichiers que vous souhaitez ajouter, puis sélectionnez **Inclure dans le projet**, ce qui les inclut également dans le contrôle de code source avec votre prochaine validation.

![Commande Inclure dans le projet dans l’Explorateur de solutions](media/django/step06-include-migrations-script-in-project.png)

### <a name="question-can-i-see-what-migrations-would-be-applied-before-running-the-migrate-command"></a>Question : Puis-je voir quelles migrations seront appliquées avant d’exécuter la commande de migration ?

Réponse : Oui, utilisez la [commande django-admin showmigrations](https://docs.djangoproject.com/en/2.0/ref/django-admin/#showmigrations).

## <a name="step-6-4-understand-the-views-and-page-templates-created-by-the-project-template"></a>Étape 6-4 : comprendre les affichages et les modèles de page créés par le modèle de projet

La plupart des vues générés par le modèle « Projet Django web projet de sondage », telles que les vues des pages À propos et Contact, sont très similaires aux vues créées par le modèle « Projet Django web » avec lequel vous avez travaillé avec précédemment dans ce tutoriel. La différence dans l’application de sondage est que sa page d’accueil utilise les modèles, de même que plusieurs pages ajoutées pour le vote et pour l’affichage des résultats du sondage.

Pour commencer, la première ligne du tableau `urlpatterns` du fichier *urls.py* du projet Django est plus qu’un simple routage vers un affichage de l’application. Au lieu de cela, elle extrait dans le propre fichier *urls.py* de l’application :

```python
from django.conf.urls import url, include
import app.views

urlpatterns = [
    url(r'^', include('app.urls', namespace="app")),
    # ..
]
```

Le fichier *app/urls.py* contient alors du code de routage plus intéressant (commentaires explicatifs ajoutés) :

```python
urlpatterns = [
    # Home page routing
    url(r'^$',
        app.views.PollListView.as_view(
            queryset=Poll.objects.order_by('-pub_date')[:5],
            context_object_name='latest_poll_list',
            template_name='app/index.html',),
        name='home'),

    # Routing for a poll page, which use URLs in the form <poll_id>/,
    # where the id number is captured as a group named "pk".
    url(r'^(?P<pk>\d+)/$',
        app.views.PollDetailView.as_view(
            template_name='app/details.html'),
        name='detail'),

    # Routing for <poll_id>/results pages, again using a capture group
    # named pk.
    url(r'^(?P<pk>\d+)/results/$',
        app.views.PollResultsView.as_view(
            template_name='app/results.html'),
        name='results'),

    # Routing for <poll_id>/vote pages, with the capture group named
    # poll_id this time, which becomes an argument passed to the view.
    url(r'^(?P<poll_id>\d+)/vote/$', app.views.vote, name='vote'),
]
```

Si vous n’êtes pas familiarisé avec les expressions régulières plus complexes utilisées ici, vous pouvez coller l’expression dans [regex101.com](https://regex101.com/) pour obtenir une explication dans un langage simple. (Vous devrez placer en échappement les barres obliques `/` en les faisant précéder d’une barre oblique inverse, `\` ; l’échappement n’est pas nécessaire dans Python en raison du préfixe `r` dans la chaîne, qui signifie « raw »).

Dans Django, la syntaxe `?P<name>pattern` crée un groupe nommé `name`, qui sert d’argument aux affichages dans leur ordre d’apparition. Dans le code indiqué précédemment, `PollsDetailView` et `PollsResultsView` reçoivent un argument nommé `pk`, et `app.views.vote` reçoit un argument nommé `poll_id`.

Vous pouvez également voir que la plupart des affichages ne sont pas uniquement des références directes simplement à une fonction d’affichage dans *app/views.py*. Au lieu de cela, la majorité d’entre eux fait référence à une classe dans ce même fichier dérivé de `django.views.generic.ListView` ou de `django.views.generic.DetailView`. Les classes de base fournissent les méthodes `as_view`, qui se servent d’un argument `template_name` pour identifier le modèle. La classe de base `ListView` utilisée pour la page d’accueil attend également une propriété `queryset` contenant les données et une propriété `context_object_name` avec le nom de variable avec lequel vous souhaitez faire référence aux données dans le modèle, ici `latest_poll_list`.

Maintenant, vous pouvez examiner le `PollListView` pour la page d’accueil, qui est défini comme suit dans *app/views.py* :

```python
class PollListView(ListView):
    """Renders the home page, with a list of all polls."""
    model = Poll

    def get_context_data(self, **kwargs):
        context = super(PollListView, self).get_context_data(**kwargs)
        context['title'] = 'Polls'
        context['year'] = datetime.now().year
        return context
```

Tout ce qui est effectué ici sert à identifier le modèle avec lequel l’affichage fonctionne (sondage) et remplace la méthode `get_context_data` pour ajouter les valeurs `title` et `year` au contexte.

Le cœur du modèle (*templates/app/index.html*) est le suivant :

```html
{% if latest_poll_list %}
<table class="table table-hover">
    <tbody>
        {% for poll in latest_poll_list %}
        <tr>
            <td>
                <a href="{% url 'app:detail' poll.id %}">{{poll.text}}</a>
            </td>
        </tr>
        {% endfor %}
    </tbody>
</table>
{% else %}
<!-- ... other content omitted ... -->
{% endif %}
```

En réalité, le modèle reçoit la liste des objets de sondage dans `latest_poll_list`, puis parcourt cette liste pour créer une ligne de table qui contient un lien vers chaque sondage à l’aide de la valeur `text` du sondage. Dans la balise `{% url %}`, « app:detail » fait référence au modèle d’url dans *app/urls.py*, nommé « detail », à l’aide de `poll.id` comme argument. Ceci a pour effet est que Django crée une URL en utilisant le modèle approprié et l’utilise pour le lien. Ce bit de vérification future de signifie que vous pouvez modifier ce modèle d’URL à tout moment et que les liens générés sont automatiquement mis à jour pour correspondre.

Les classes `PollDetailView` et `PollResultsView` dans *app/views.py* (non illustré ici) sont presque identiques à `PollListView`, à la seule différence qu’elles sont dérivées de `DetailView` à la place. Leurs modèles respectifs, *app/templates/details.html* et *app/templates/results.html*, placent ensuite les champs appropriés à partir des modèles dans différents contrôles HTML. Un élément unique dans *details.html* est que les choix pour une interrogation sont contenus dans un formulaire HTML qui, quand il est envoyé, effectue un POST à destination de l’URL /vote. Comme indiqué précédemment, ce modèle d’URL est routé vers `app.views.vote`, qui est implémenté comme suit (notez l’argument `poll_id`, qui est à nouveau un groupe nommé dans l’expression régulière utilisé dans le routage de cet affichage) :

```python
def vote(request, poll_id):
    """Handles voting. Validates input and updates the repository."""
    poll = get_object_or_404(Poll, pk=poll_id)
    try:
        selected_choice = poll.choice_set.get(pk=request.POST['choice'])
    except (KeyError, Choice.DoesNotExist):
        return render(request, 'app/details.html', {
            'title': 'Poll',
            'year': datetime.now().year,
            'poll': poll,
            'error_message': "Please make a selection.",
    })
    else:
        selected_choice.votes += 1
        selected_choice.save()
        return HttpResponseRedirect(reverse('app:results', args=(poll.id,)))
```

Ici, l’affichage n’a pas son propre modèle correspondant, comme les autres pages. Au lieu de cela, il valide le sondage sélectionné, indiquant une erreur 404 si le sondage n’existe pas (au cas où un utilisateur entrerait une URL telle que « vote/1a2b3c »). Il vérifie ensuite que le choix de vote est valide pour le sondage. Si ce n’est pas le cas, le bloc `except` affiche simplement à nouveau la page de détails avec un message d’erreur. Si le choix est valide, l’affichage comptabilise le vote et redirige vers la page de résultats.

## <a name="step-6-5-create-a-custom-administration-interface"></a>Étape 6-5 : créer une interface d’administration personnalisée

Les derniers éléments du modèle « Projet Django web de sondage » sont des extensions personnalisées de l’interface d’administration Django par défaut, comme indiqué plus haut dans cet article sous l’étape 6-1. L’interface par défaut est exclusivement destinée à l’utilisateur et à la gestion des groupes. Le modèle de projet Sondage ajoute des fonctionnalités qui vous permettent de gérer également des sondages.

Tout d’abord, les modèles d’URL dans le fichier *urls.py* du projet Django inclut `url(r'^admin/', include(admin.site.urls)),` par défaut ; le modèle « admin/doc » est également inclus, mais sous forme de commentaire.

L’application contient alors le fichier *admin.py*, que Django exécute automatiquement quand vous accédez à l’interface d’administration grâce à l’inclusion de `django.contrib.admin` dans le tableau `INSTALLED_APPS` de *settings.py*. Le code dans ce fichier, tel que fourni par le modèle de projet, est le suivant :

```python
from django.contrib import admin
from app.models import Choice, Poll

class ChoiceInline(admin.TabularInline):
    """Choice objects can be edited inline in the Poll editor."""
    model = Choice
    extra = 3

class PollAdmin(admin.ModelAdmin):
    """Definition of the Poll editor."""
    fieldsets = [
        (None, {'fields': ['text']}),
        ('Date information', {'fields': ['pub_date']}),
    ]
    inlines = [ChoiceInline]
    list_display = ('text', 'pub_date')
    list_filter = ['pub_date']
    search_fields = ['text']
    date_hierarchy = 'pub_date'

admin.site.register(Poll, PollAdmin)
```

Comme vous pouvez le voir, la classe `PollAdmin` est dérivée de `django.contrib.admin.ModelAdmin` et personnalise un certain nombre de ses champs à l’aide de noms tirés du modèle `Poll`, qu’elle gère. Ces champs sont décrits sur des [options ModelAdmin](https://docs.djangoproject.com/en/2.0/ref/contrib/admin/#modeladmin-options) dans la documentation Django.

L’appel à `admin.site.register` connecte alors cette classe au modèle (`Poll`) et l’inclut dans l’interface d’administration. Le résultat global est indiqué ci-dessous :

![Affichage complet de l’administration de l’application du Projet web Django de sondage](media/django/step06-polls-administrative-interface.png)

## <a name="next-steps"></a>Étapes suivantes :

> [!Note]
> Si vous validez votre solution Visual Studio lors du contrôle de code source pendant ce tutoriel, c’est le bon moment pour effectuer une autre validation. Votre solution doit correspondre au code source du tutoriel sur GitHub : [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django).

Vous avez maintenant parcouru l’intégralité des modèles du « projet Django web vide », du « projet Django web » et du « projet Django web de sondage » dans Visual Studio. Vous avez appris tous les principes fondamentaux de Django, tels que l’utilisation des affichages et des modèles et vous avez exploré le routage, l’authentification et l’utilisation des modèles de base de données. Vous devez maintenant être en mesure de créer vous-même une application web avec les affichages et les modèles dont vous avez besoin.

L’exécution d’une application web sur votre ordinateur de développement n’est qu’une étape de la mise de l’application à la disposition de vos clients. Les étapes suivantes peuvent inclure les tâches suivantes :

- Déployer l’application web sur un serveur de production, tels qu’Azure App Service. Voir [Publier sur Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md).

- Personnaliser la page d’erreur 404 en créant un modèle nommé *templates/404.html*. Lorsqu’il est disponible, Django utilise ce modèle au lieu de son message d’erreur par défaut. Pour plus d’informations, consultez [Affichage des erreurs](https://docs.djangoproject.com/en/2.0/ref/views/#error-views) dans la documentation Django.

- Écrire des tests unitaires dans *tests.py* ; les modèles de projet Visual Studio fournissent des points de départ, et vous trouverez plus d’informations sous [Écrire votre première application Django, partie 5 – tests](https://docs.djangoproject.com/en/2.0/intro/tutorial05/) et sous [Tests dans Django](https://docs.djangoproject.com/en/2.0/topics/testing/) dans la documentation Django.

- Transformer l’application de SQLite en magasin de données au niveau de la production comme PostgreSQL, MySQL et SQL Server (qui peuvent tous être hébergés sur Azure). Comme décrit dans [Quand utiliser SQLite](https://www.sqlite.org/whentouse.html) (sqlite.org), SQLite fonctionne bien sur les sites au trafic faible à moyen, avec moins de 100 000 accès par jour, mais n’est pas recommandé pour les volumes plus élevés. Il est également limité à un seul ordinateur et ne peut par conséquent pas être utilisé dans un scénario multiserveur tel que l’équilibrage de charge et la géoréplication. Pour plus d’informations sur la prise en charge de Django pour d’autres bases de données, consultez [Configuration de la base de données](https://docs.djangoproject.com/en/2.0/intro/tutorial02/#database-setup). Vous pouvez également utiliser le [kit de développement logiciel (SDK) Azure pour Python](/azure/python/) pour travailler avec les services de stockage Azure, comme les tables et les objets blob.

- Configurez un pipeline d’intégration continue ou de déploiement continu sur un service comme Azure DevOps. En plus de l’utilisation du contrôle de code source (via Azure Repos, GitHub ou ailleurs), vous pouvez configurer un projet Azure DevOps pour exécuter automatiquement vos tests unitaires, dans le cadre des prérequis à la mise en production. Vous pouvez également configurer le pipeline pour effectuer le déploiement sur un serveur de préproduction pour des tests supplémentaires, avant le déploiement en production. Par ailleurs, Azure DevOps s’intègre aux solutions de supervision comme App Insights, et termine le cycle avec des outils de planification agile. Pour plus d’informations, consultez [Créer un pipeline CI/CD pour Python avec le projet Azure DevOps](/azure/devops-project/azure-devops-project-python?view=vsts), ainsi que la [documentation générale sur Azure DevOps ](/azure/devops/?view=vsts).
