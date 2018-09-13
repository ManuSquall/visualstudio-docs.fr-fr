---
title: Modèles d’éléments pour les projets Python
description: Une liste de référence des modèles d’éléments pour les projets Python qui sont disponibles via la fonction Ajouter > Nouvel élément de boîte de dialogue dans Visual Studio.
ms.date: 09/04/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 8319c99e5de12ce1c09a2c20fc5cf1b132f34092
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43776033"
---
# <a name="python-item-templates"></a>Modèles d’éléments Python

Les modèles d’élément sont disponibles dans les projets Python via la commande de menu **Projet** > **Ajouter un nouvel élément**, ou via la commande **Ajouter** > **Nouvel élément** dans le menu contextuel de **l’Explorateur de solutions**.

![Boîte de dialogue Ajouter un nouvel élément](media/project-item-templates.png)

Avec le nom que vous fournissez pour l’élément, un modèle crée généralement un ou plusieurs fichiers et dossiers dans le dossier actuellement sélectionné dans le projet (un clic droit sur un dossier pour afficher le menu contextuel entraîne la sélection automatique de ce dossier). Un élément ajouté est inclus dans le projet Visual Studio, et l’élément s’affiche dans **l’Explorateur de solutions**.

Le tableau suivant décrit brièvement l’effet de chaque modèle d’élément dans un projet de Python :

| Modèle | Ce que crée le modèle |
| --- | --- |
| **Fichier Python vide** | Un fichier vide avec l’extension *.py*. |
| **Classe Python** | Un fichier *.py* contenant une seule définition de classe Python vide. |
| **Package Python** | Un dossier contenant un fichier *\_\_init\_\_.py*. |
| **Test unitaire Python** | Un fichier *.py* avec un test unitaire unique basé sur le framework `unittest`, ainsi qu’un appel à `unittest.main()` pour exécuter les tests dans le fichier. |
| **Page HTML** | Un fichier *.html* avec une structure de page simple composée d’un élément `<head>` et d’un élément `<body>`. |
| **JavaScript** | Un fichier *.js* vide. |
| **Feuille de style** | Un fichier *.css* contenant un style vide pour `body`. |
| **Fichier texte** | Un fichier *.txt* vide. |
| **Application Django 1.9**<br/>**Application Django 1.4** | Un dossier portant le nom de l’application, qui contient les principaux fichiers d’une application Django, comme indiqué dans [Découvrir Django dans Visual Studio, étape 2-2](learn-django-in-visual-studio-step-02-create-an-app.md#step-2-1-create-an-app-with-a-default-structure) pour Django 1.9. Pour Django 1.4, le dossier *migrations*, le fichier *admin.py* et le fichier *apps.py* ne sont pas inclus. |
| **Fenêtre IronPython WPF** | Une fenêtre WPF composée de deux fichiers côte à côte : un fichier *.xaml* qui définit `<Window>` avec un élément `<Grid>` vide, et un fichier *.py* associé qui charge le fichier XAML à l’aide de la bibliothèque `wpf`. Généralement utilisé dans un projet créé avec un des modèles de projet IronPython. Consultez [Gérer les projets Python - Modèles de projet](managing-python-projects-in-visual-studio.md#project-templates). |
| **Fichiers de prise en charge des rôles web** | Un dossier *bin* à la racine du projet (quel que soit le dossier sélectionné dans le projet). Le dossier contient un script de déploiement par défaut et un fichier *web.config* pour les rôles web Azure Cloud Services. Le modèle comprend également un fichier *readme.html* qui explique tous les détails. |
| **Fichiers de prise en charge des rôles de travail** | Un dossier *bin* à la racine du projet (quel que soit le dossier sélectionné dans le projet). Le dossier contient un script de déploiement et de lancement par défaut, ainsi qu’un fichier *web.config*, pour les rôles de travail Azure Cloud Services. Le modèle comprend également un fichier *readme.html* qui explique tous les détails. |
| **Fichier web.config Azure (FastCGI)** | Un fichier *web.config* qui contient des entrées pour les applications utilisant un objet [WSGI](https://wsgi.readthedocs.io/en/latest/) afin de prendre en charge les connexions entrantes. Ce fichier est généralement déployé à la racine d’un serveur web exécutant IIS, tel qu’Azure App Service. Pour plus d’informations, consultez [Publier sur Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md). |
| **Fichier web.config Azure (HttpPlatformHandler)** | Un fichier *web.config* qui contient des entrées pour les applications qui sont à l’écoute des connexions entrantes sur un socket. Ce fichier est généralement déployé à la racine d’un serveur web exécutant IIS, tel qu’Azure App Service. Pour plus d’informations, consultez [Publier sur Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md). |
| **Fichier web.config des fichiers statiques Azure** | Un fichier *web.config* généralement ajouté à un dossier *static* (ou à tout autre dossier contenant des éléments statiques) pour désactiver la prise en charge de ce dossier par Python. Ce fichier de configuration fonctionne conjointement avec l’un des fichiers de configuration FastCGI ou HttpPlatformHandler ci-dessus. Pour plus d’informations, consultez [Publier sur Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md). |
| **Fichier web.config de débogage à distance Azure** | Un fichier *web.config.debug* qui active le débogage à distance sur WebSockets, ainsi que *Microsoft.PythonTools.WebRole.dll* et un dossier *ptvsd* qui contient les modules à déployer sur le serveur pour activer le débogage à distance. En règle générale, vous créez cet élément au même emplacement que votre fichier *web.config*. Pour plus d’informations, consultez [Déboguer à distance du code Python sur Azure](debugging-remote-python-code-on-azure.md). Lisez également la remarque ci-dessous. |

> [!Note]
> Si vous ajoutez le modèle de débogage *web.config* à un projet et si vous prévoyez d’utiliser le débogage à distance Python, vous devez publier le site en configuration **Debug**. Ce paramètre est distinct de la configuration de la solution active et a toujours la valeur par défaut **Release**. Pour le changer, ouvrez l’onglet **Paramètres** et utilisez la zone de liste modifiable **Configuration** dans l’Assistant **Publication**. (Consultez la [documentation Azure](https://azure.microsoft.com/develop/python/) pour plus d’informations sur la création et le déploiement vers des applications Web Azure.)
>
> ![Modification de la configuration de publication](media/template-web-publish-config.png)

## <a name="see-also"></a>Voir aussi

- [Gérer les projets Python - Modèles de projet](managing-python-projects-in-visual-studio.md#project-templates)
- [Modèles de projet web Python](python-web-application-project-templates.md)
- [Publier sur Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
