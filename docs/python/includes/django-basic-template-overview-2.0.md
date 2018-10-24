---
ms.topic: include
ms.openlocfilehash: 9e882ddd8bafe500713a71624ce9a51278939958
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950937"
---
### <a name="create-a-project-using-django-20"></a>Créer un projet à l’aide de Django 2.0

Actuellement, le **modèle de projet web Django vide** utilise la version la plus récente de Django 1.x. Le moyen le plus rapide d’utiliser Django 2.x consiste à importer des fichiers Django 2.x dans un projet Django 1.x. Grâce à ce processus, vous allez profiter d’autres détails gérés par le modèle de projet Visual Studio.

1. Créez un projet Django 1.x à l’aide du modèle **Projet web Django vide**, comme décrit dans la section précédente. Toutefois, à l’invite **Ce projet requiert des dépendances externes**, sélectionnez **Je vais les installer moi-même**. Cette option vous évitera d’installer des dépendances qui seront désinstallées ultérieurement.

2. Ouvrez une invite de commande et accédez au dossier temporaire.

3. Exécutez `pip install django` pour installer le dernier package Django dans votre environnement Python global.

4. Exécutez `django-admin startproject <project_name>` en remplaçant `<project_name>` par le nom de projet utilisé à l’étape 1, par exemple « HelloDjango ». La commande `startproject` crée un fichier *manage.py* avec un dossier correspondant `<project_name>`, qui contient les fichiers *\_\_init\_\_.py*, *settings.py*, *urls.py* et *wsgi.py*.

5. Dans Visual Studio, remplacez les fichiers Django 1.x dans le projet par les fichiers Django 2.x comme suit :

   1. Dans **l’Explorateur de solutions**, supprimez **manage.py** et le dossier d’application Django.
   2. Cliquez avec le bouton droit sur le projet, sélectionnez la commande **Ajouter** > **Élément existant**, accédez au fichier **manage.py** créé à l’étape 4, sélectionnez-le, puis sélectionnez **OK**. Visual Studio copie ensuite ce fichier dans le projet.
   3. Cliquez à nouveau avec le bouton droit sur le projet, sélectionnez la commande **Ajouter** > **Dossier existant**, accédez au dossier d’application créé à l’étape 4, sélectionnez-le, puis sélectionnez **OK**. Visual Studio copie ensuite ce dossier entier et ses quatre fichiers dans le projet.
   4. Cliquez avec le bouton droit sur **manage.py** et sélectionnez **Définir comme fichier de démarrage**.

      > [!Important]
      > Le nom de l’application indiqué dans le projet Visual Studio doit correspondre au `<project_name>` utilisé avec l’utilitaire `django-admin`, car l’utilitaire utilise ce nom comme un espace de noms dans les fichiers de code Python.

6. Ouvrez *requirements.txt*, changez son contenu en `django >=2.0, <3` et enregistrez le fichier.

7. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Environnements Python** et sélectionnez **Ajouter un environnement virtuel**. Acceptez les valeurs par défaut dans la boîte de dialogue qui s’affiche et sélectionnez **Créer**. Accepter les invites de privilèges d’administrateur.
