---
title: "Modèle de projet web Django pour Python dans Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 7/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c479be58-13eb-4d77-9a27-c97ddc290963
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: 242203505dc80c9cdfe6041fbf97308a16ccd2c8
ms.contentlocale: fr-fr
ms.lasthandoff: 07/18/2017

---

# <a name="django-web-project-template"></a>Modèle de projet Web Django

[Django](https://www.djangoproject.com/) est un framework Python général conçu pour un développement web rapide, sécurisé et scalable. La prise en charge de Python dans Visual Studio fournit un modèle de projet permettant de configurer la structure d’une application web Django. Pour utiliser ce modèle dans Visual Studio, sélectionnez **Fichier > Nouveau > Projet**, recherchez « Django », puis sélectionnez le modèle « Django Web Project » (Projet web Django). Le projet résultant inclut du code réutilisable, ainsi qu’une base de données SQLite par défaut. Le modèle « Blank Django Web Project » (Projet Web Django vide) est similaire, mais n’inclut pas la base de données.

Visual Studio offre une fonctionnalité IntelliSense complète pour les projets Django :

- Variables de contexte transmises dans le modèle :

    ![IntelliSense pour les variables de contexte](media/template-django-intellisense.png)

- Balisage et filtrage pour les éléments intégrés et définis par l’utilisateur :

    ![IntelliSense pour les balises et les filtres](media/template-django-intellisense-filter.png)

- Coloration syntaxique pour les éléments CSS et JavaScript incorporés :

    ![IntelliSense pour CSS](media/template-django-intellisense-css.png)

    ![IntelliSense JavaScript](media/template-django-intellisense-js.png)


Visual Studio offre également une [prise en charge complète du débogage](debugging.md) pour les projets Django : 

![Points d’arrêt](media/template-django-debugging.png)

Il est courant pour les projets Django d’être gérés via leur fichier `manage.py`, qui est une hypothèse suivie par Visual Studio. Si vous n’utilisez plus ce fichier comme point d’entrée, vous arrêtez essentiellement le fichier projet. Dans ce cas, vous devez [recréer le projet à partir de fichiers existants](python-projects.md#creating-a-project-from-existing-files) sans le marquer comme projet Django.


## <a name="django-management-console"></a>Console de gestion Django

La console de gestion Django est accessible par le biais de plusieurs commandes du menu **Projet** ou par un clic droit sur le projet dans l’Explorateur de solutions.

- **Ouvrir l’interpréteur de commandes Django**  : ouvre un interpréteur de commandes dans le contexte de l’application qui vous permet de manipuler vos modèles.

    ![Console](media/template-django-console-shell.png)

- **Django Sync DB (Base de données de synchronisation Django)** : exécute `manage.py syncdb` dans une fenêtre interactive :

    ![Console](media/template-django-console-sync-db.png)

- **Collect Static (Collecter les fichiers statiques)** : exécute `manage.py collectstatic --noinput` pour copier tous les fichiers statiques dans le chemin d’accès spécifié par `STATIC_ROOT` dans votre fichier `settings.py`. Notez que lors de la [publication sur Microsoft Azure](template-web.md#publishing-to-azure-app-service), les fichiers statiques sont automatiquement collectés dans le cadre de l’opération de publication.

    ![Console](media/template-django-console-collect-static.png)

- **Valider** : exécute `manage.py validate`, qui signale toutes les erreurs de validation dans les modèles installés spécifiés par `INSTALLED_APPS` dans votre fichier `settings.py` :

    ![Console](media/template-django-console-validate.png)
