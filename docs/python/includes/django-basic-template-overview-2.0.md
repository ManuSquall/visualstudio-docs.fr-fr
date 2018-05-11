---
ms.topic: include
ms.openlocfilehash: b629de8144e08c7c0019a0a116f84e5877c3a477
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2018
---
### <a name="create-a-project-using-django-20"></a>Créer un projet à l’aide de Django 2.0

Actuellement, le modèle de projet de Web vide Django utilise la version la plus récente de Django 1.x. Le moyen le plus rapide d’utiliser Django 2.x consiste à importer des fichiers Django 2.x dans un projet Django 1.x. Grâce à ce processus, vous allez profiter d’autres détails gérés par le modèle de projet Visual Studio.

1. Créez un projet Django 1.x à l’aide du modèle « Projet web Django vide », comme décrit dans la section précédente. Toutefois, à l’invite « Ce projet requiert des dépendances externes », sélectionnez **I will install them myself**. Cette option vous évitera d’installer des dépendances qui seront désinstallées ultérieurement.

1. Ouvrez une invite de commande et accédez au dossier temporaire.

1. Exécutez `pip install django` pour installer le dernier package Django dans votre environnement Python global.

1. Exécutez `django-admin startproject <project_name>` en remplaçant `<project_name>` par le nom de projet utilisé à l’étape 1, par exemple « HelloDjango ». La commande `startproject` crée un fichier `manage.py` avec un dossier correspondant `<project_name>` qui contient les fichiers `__init.py__`, `settings.py`, `urls.py` et `wsgi.py`.

1. Dans Visual Studio, remplacez les fichiers Django 1.x dans le projet par les fichiers Django 2.x comme suit :

  a. Dans l’**Explorateur de solutions**, supprimez `manage.py` et le dossier d’application Django.
  b. Cliquez avec le bouton droit de la souris sur le projet, sélectionnez la commande **Ajouter > Élément existant...** , accédez à, puis sélectionnez le fichier `manage.py` créé à l’étape 4, puis sélectionnez **OK**. Visual Studio copie ensuite ce fichier dans le projet.
  c. Cliquez à nouveau avec le bouton droit de la souris sur le projet, sélectionnez la commande **Ajouter > Dossier existant...** , accédez à, puis sélectionnez le dossier d’application créé à l’étape 4, puis sélectionnez **OK**. Visual Studio copie ensuite ce dossier entier et ses quatre fichiers dans le projet.
  d. Cliquez avec le bouton droit sur `manage.py` et sélectionnez **Définir comme fichier de démarrage**.

  > [!Important]
  > Le nom de l’application indiqué dans le projet Visual Studio doit correspondre au `<project_name>` utilisé avec l’utilitaire `django-admin`, car l’utilitaire utilise ce nom comme un espace de noms dans les fichiers de code Python.

1. Ouvrez `requirements.txt`, modifiez son contenu dans `django >=2.0, <3` et enregistrez le fichier.

1. Dans **Explorateur de solutions**, cliquez avec le bouton de droite sur le nœud **Environnements Python** et sélectionnez **Ajouter un environnement virtuel...**. Acceptez les valeurs par défaut dans la boîte de dialogue qui s’affiche et sélectionnez **Créer**. Accepter les invites de privilèges d’administrateur.