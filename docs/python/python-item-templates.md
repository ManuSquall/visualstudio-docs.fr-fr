---
title: Modèles d’éléments pour les projets Python
description: Une liste de référence des modèles d’éléments pour les projets Python qui sont disponibles via la fonction Ajouter > Nouvel élément de boîte de dialogue dans Visual Studio.
ms.date: 04/25/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 9811905e842eeb62399ef3b88558ee0286b05c84
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2018
---
# <a name="python-item-templates"></a>Modèles d’éléments Python

Les modèles d’élément sont disponibles dans les projets Python via la commande de menu **Projet** > **Ajouter un nouvel élément**, ou via la commande **Ajouter** > **Nouvel élément** dans le menu contextuel de **l’Explorateur de solutions**.

![Boîte de dialogue Ajouter un nouvel élément](media/project-item-templates.png)

Avec le nom que vous fournissez pour l’élément, un modèle crée généralement un ou plusieurs fichiers et dossiers dans le dossier actuellement sélectionné dans le projet (un clic droit sur un dossier pour afficher le menu contextuel entraîne la sélection automatique de ce dossier). Un élément ajouté est inclus dans le projet Visual Studio, et l’élément s’affiche dans **l’Explorateur de solutions**.

Le tableau suivant décrit brièvement l’effet de chaque modèle d’élément dans un projet de Python :

| Modèle | Ce que crée le modèle |
| --- | --- |
| Fichier Python vide | Un fichier vide avec l’extension `.py`. |
| Classe Python | Un fichier `.py` contenant une seule définition de classe Python vide. |
| Package Python | Un dossier qui contient un fichier `__init.py__`. |
| Test unitaire Python | Un fichier `.py` avec un test unitaire unique basé sur l’infrastructure `unittest` ainsi qu’un appel à `unittest.main()` pour exécuter les tests dans le fichier. |
| Page HTML | Un fichier `.html` avec une structure de page simple composé d’un élément `<head>` et d’un élément `<body>`. |
| JavaScript | Un fichier `.js` vide. |
| Feuille de style | Un fichier `.css` contenant un style vide pour `body` |
| Fichier texte | Un fichier `.txt` vide. |
| Application Django 1.9<br/>Application Django 1.4 | Un dossier portant le nom de l’application, qui contient les principaux fichiers de pour une application Django comme expliqué dans [Découvrir Django dans Visual Studio, étape 2-2](learn-django-in-visual-studio-step-02-create-an-app.md#step-2-1-create-an-app-with-a-default-structure) pour Django 1.9. Pour Django 1.4, le dossier `migrations`, le fichier `admin.py` et le fichier `apps.py` ne sont pas inclus. |
| Fenêtre IronPython WPF | Une fenêtre WPF constitué de deux fichiers côte à côte : un fichier `.xaml` qui définit une `<Window>` avec un élément `<Grid>` vide, et un fichier `.py` associé qui charge le fichier XAML à l’aide de la bibliothèque `wpf`. Généralement utilisé dans un projet créé avec un des modèles de projet IronPython. Consultez [projets Python de gestion – modèles de projet](managing-python-projects-in-visual-studio.md#project-templates). |
| Fichiers de prise en charge des rôles Web | Un dossier `bin` dans la racine du projet (quel que soit le dossier sélectionné dans le projet). Le dossier contient un script de déploiement par défaut et un fichier `web.config` pour les rôles web du service cloud Azure. Le modèle inclut également un fichier `readme.html` qui explique les détails. |
| Fichiers de prise en charge des rôles de travail | Un dossier `bin` dans la racine du projet (quel que soit le dossier sélectionné dans le projet). Le dossier contient un script de déploiement par défaut et un script de lancement, ainsi qu’un fichier `web.config` pour les rôle de travail du service cloud Azure. Le modèle inclut également un fichier `readme.html` qui explique les détails. |
| Fichier web.config Azure (FastCGI) | Un fichier `web.config` qui contient des entrées pour les applications utilisant un objet [WSGI](https://wsgi.readthedocs.io/en/latest/) objet pour gérer les connexions entrantes. Ce fichier est généralement déployé à la racine d’un serveur web exécutant IIS, tel qu’Azure App Service. Pour plus d'informations, consultez [Publication sur Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md). |
| Fichier web.config Azure (HttpPlatformHandler) | Un fichier `web.config` qui contient des entrées pour les applications sur un socket d’écoute pour les connexions entrantes. Ce fichier est généralement déployé à la racine d’un serveur web exécutant IIS, tel qu’Azure App Service. Pour plus d'informations, consultez [Publication sur Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md). |
| Fichier web.config des fichiers statiques Azure | Un fichier `web.config` généralement ajouté à un dossier `static` (ou à un autre dossier contenant des éléments statiques) pour désactiver la gestion de ce dossier par Python. Ce fichier de configuration fonctionne conjointement avec l’un des fichiers de configuration FastCGI ou HttpPlatformHandler ci-dessus. Pour plus d'informations, consultez [Publication sur Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md). |
| Fichier web.config de débogage à distance Azure | Un fichier `web.config.debug` qui active le débogage à distance sur WebSockets, parallèlement à `Microsoft.PythonTools.WebRole.dll` et à un `ptvsd` dossier qui contient les modules à déployer sur le serveur pour activer le débogage distant. En règle générale, vous créez cet élément au même emplacement que votre fichier `web.config`. Pour plus d’'informations, consultez [Débogage à distance de code Python sur Azure](debugging-remote-python-code-on-azure.md). Lisez également la remarque ci-dessous. |

> [!Note]
> Si vous ajoutez le modèle de débogage `web.config` à un projet et que vous prévoyez d’utiliser le débogage à distance Python, vous devez publier le site dans la configuration « Debogage ». Ce paramètre est distinct de la configuration de la solution active actuelle et est toujours défini par défaut sur la valeur « Release ». Pour le modifier, ouvrez l’onglet **Paramètres** et utilisez la liste modifiable **Configuration** dans l’Assistant de publication. (Consultez la [documentation Azure](https://azure.microsoft.com/develop/python/) pour plus d’informations sur la création et le déploiement vers des applications Web Azure.)
>
> ![Modification de la configuration de publication](media/template-web-publish-config.png)

## <a name="see-also"></a>Voir aussi

- [Gestion de projets Python (modèles de projets)](managing-python-projects-in-visual-studio.md#project-templates)
- [Modèles de projet web Python](python-web-application-project-templates.md)
- [Publication sur Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)