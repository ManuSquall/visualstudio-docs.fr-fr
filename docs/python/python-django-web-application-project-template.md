---
title: Modèle de projet web Django pour Python
description: Visual Studio fournit un modèle complet pour la création rapide d’applications web Django avec Python.
ms.date: 11/12/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 0193256edb4a55285e8017a56fe7249ef5d60362
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912398"
---
# <a name="django-web-project-template"></a>Modèle de projet web Django

[Django](https://www.djangoproject.com/) est une infrastructure Python de haut niveau conçue pour assurer un développement Web rapide, sécurisé et évolutif. La prise en charge de Python dans Visual Studio fournit plusieurs modèles de projet permettant de configurer la structure d’une application web Django. Pour utiliser un modèle dans Visual Studio, sélectionnez **fichier**  >  **nouveau**  >  **projet**, recherchez « Django », sélectionnez dans le **projet Web Django vide**, **projet Web Django**, puis interrogez les modèles de **projet Web Django** . Consultez le [tutoriel d’apprentissage de Django](learn-django-in-visual-studio-step-01-project-and-solution.md) qui propose une procédure pas à pas pour tous les modèles.

Visual Studio offre une fonctionnalité IntelliSense complète pour les projets Django :

- Variables de contexte transmises dans le modèle :

    ![IntelliSense pour les variables de contexte](media/template-django-intellisense.png)

- Balisage et filtrage pour les éléments intégrés et définis par l’utilisateur :

    ![IntelliSense pour les balises et les filtres](media/template-django-intellisense-filter.png)

- Coloration syntaxique pour les éléments CSS et JavaScript incorporés :

    ![IntelliSense pour CSS](media/template-django-intellisense-css.png)

    ![IntelliSense JavaScript](media/template-django-intellisense-js.png)

Visual Studio offre également une [prise en charge complète du débogage](debugging-python-in-visual-studio.md) pour les projets Django :

![Points d’arrêt](media/template-django-debugging.png)

Il est courant pour les projets Django d’être gérés via leur fichier *manage.py*, qui est une hypothèse suivie par Visual Studio. Si vous n’utilisez plus ce fichier comme point d’entrée, vous arrêtez essentiellement le fichier projet. Dans ce cas, vous devez [recréer le projet à partir de fichiers existants](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) sans le marquer comme projet Django.

## <a name="django-management-console"></a>Console de gestion Django

Vous pouvez accéder à la console de gestion Django à l’aide de différentes commandes du menu **projet** ou en cliquant avec le bouton droit sur le projet dans **Explorateur de solutions**.

- **Open Django Shell**: ouvre un shell dans le contexte de votre application, qui vous permet de manipuler vos modèles :

    ![Résultats de la commande Ouvrir l’interpréteur de commandes Django](media/template-django-console-shell.png)

- **Django Sync DB**: s’exécute `manage.py syncdb` dans une fenêtre **interactive** :

    ![Résultats de la commande Base de données de synchronisation Django](media/template-django-console-sync-db.png)

- **Collect Static (Collecter les fichiers statiques)** : exécute `manage.py collectstatic --noinput` pour copier tous les fichiers statiques dans le chemin d’accès spécifié par `STATIC_ROOT` dans votre fichier *settings.py*.

    ![Résultat de la commande Collecter les fichiers statiques](media/template-django-console-collect-static.png)

- **Valider** : exécute `manage.py validate`, qui signale toutes les erreurs de validation dans les modèles installés spécifiés par `INSTALLED_APPS` dans votre fichier *settings.py* :

    ![Résultat de la commande Valider](media/template-django-console-validate.png)

## <a name="see-also"></a>Voir aussi

- [Tutoriel d’apprentissage de Django](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [Publier sur Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
