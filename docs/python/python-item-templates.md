---
title: Modèles d’éléments pour les projets Python
description: Une liste de référence des modèles d’éléments pour les projets Python qui sont disponibles via la fonction Ajouter > Nouvel élément de boîte de dialogue dans Visual Studio.
ms.date: 12/06/2018
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 528606356c2d976de71ab2c0317a1a0236d2e63f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85533391"
---
# <a name="python-item-templates"></a>Modèles d’éléments Python

Les modèles d’élément sont disponibles dans les projets python **Project**par le biais de la  >  commande de menu**Ajouter un nouvel élément** du projet ou de la commande **Ajouter**  >  **un nouvel élément** du menu contextuel dans **Explorateur de solutions**.

![Boîte de dialogue Ajouter un nouvel élément](media/project-item-templates.png)

Avec le nom que vous fournissez pour l’élément, un modèle crée généralement un ou plusieurs fichiers et dossiers dans le dossier actuellement sélectionné dans le projet (un clic droit sur un dossier pour afficher le menu contextuel entraîne la sélection automatique de ce dossier). Un élément ajouté est inclus dans le projet Visual Studio, et l’élément s’affiche dans **l’Explorateur de solutions**.

Le tableau suivant décrit brièvement l’effet de chaque modèle d’élément dans un projet de Python :

| Modèle | Ce que crée le modèle |
| --- | --- |
| **Fichier Python vide** | Un fichier vide avec l’extension *.py*. |
| **Classe Python** | Un fichier *.py* contenant une seule définition de classe Python vide. |
| **Package Python** | Dossier qui contient un fichier * \_ \_ init \_ \_ . py* . |
| **Test unitaire Python** | Un fichier *.py* avec un test unitaire unique basé sur le framework `unittest`, ainsi qu’un appel à `unittest.main()` pour exécuter les tests dans le fichier. |
| **Page HTML** | Un fichier *.html* avec une structure de page simple composée d’un élément `<head>` et d’un élément `<body>`. |
| **JavaScript** | Un fichier *.js* vide. |
| **Feuille de style** | Un fichier *.css* contenant un style vide pour `body`. |
| **Fichier texte** | Un fichier *.txt* vide. |
| **Application Django 1.9**<br/>**Application Django 1.4** | Un dossier portant le nom de l’application, qui contient les principaux fichiers d’une application Django, comme indiqué dans [Découvrir Django dans Visual Studio, étape 2-2](learn-django-in-visual-studio-step-02-create-an-app.md#step-2-1-create-an-app-with-a-default-structure) pour Django 1.9. Pour Django 1.4, le dossier *migrations*, le fichier *admin.py* et le fichier *apps.py* ne sont pas inclus. |
| **Fenêtre IronPython WPF** | Une fenêtre WPF composée de deux fichiers côte à côte : un fichier *.xaml* qui définit `<Window>` avec un élément `<Grid>` vide, et un fichier *.py* associé qui charge le fichier XAML à l’aide de la bibliothèque `wpf`. Généralement utilisé dans un projet créé avec un des modèles de projet IronPython. Consultez [Gérer les projets Python - Modèles de projet](managing-python-projects-in-visual-studio.md#project-templates). |
| **Fichiers de prise en charge des rôles Web** | Un dossier *bin* à la racine du projet (quel que soit le dossier sélectionné dans le projet). Le dossier contient un script de déploiement par défaut et un fichier *web.config* pour les rôles web Azure Cloud Services. Le modèle comprend également un fichier *readme.html* qui explique tous les détails. |
| **Fichiers de prise en charge des rôles de travail** | Un dossier *bin* à la racine du projet (quel que soit le dossier sélectionné dans le projet). Le dossier contient un script de déploiement et de lancement par défaut, ainsi qu’un fichier *web.config*, pour les rôles de travail Azure Cloud Services. Le modèle comprend également un fichier *readme.html* qui explique tous les détails. |
| **Fichier web.config Azure (FastCGI)** | Un fichier *web.config* qui contient des entrées pour les applications utilisant un objet [WSGI](https://wsgi.readthedocs.io/en/latest/) afin de prendre en charge les connexions entrantes. Ce fichier est généralement déployé à la racine d’un serveur web sous IIS. Pour plus d’informations, voir [Configurer une application pour IIS](configure-web-apps-for-iis-windows.md). |
| **Fichier web.config Azure (HttpPlatformHandler)** | Un fichier *web.config* qui contient des entrées pour les applications qui sont à l’écoute des connexions entrantes sur un socket. Ce fichier est généralement déployé à la racine d’un serveur web exécutant IIS, tel qu’Azure App Service. Pour plus d’informations, voir [Configurer une application pour IIS](configure-web-apps-for-iis-windows.md). |
| **Fichier web.config des fichiers statiques Azure** | Un fichier *web.config* généralement ajouté à un dossier *static* (ou à tout autre dossier contenant des éléments statiques) pour désactiver la prise en charge de ce dossier par Python. Ce fichier de configuration fonctionne conjointement avec l’un des fichiers de configuration FastCGI ou HttpPlatformHandler ci-dessus. Pour plus d’informations, voir [Configurer une application pour IIS](configure-web-apps-for-iis-windows.md). |
| **Fichier web.config de débogage à distance Azure** | Déconseillé (auparavant utilisé pour le débogage à distance sur Azure App Service pour Windows, qui n’est plus pris en charge). |

## <a name="see-also"></a>Voir aussi

- [Gérer les projets Python – Modèles de projet](managing-python-projects-in-visual-studio.md#project-templates)
- [Modèles de projet web Python](python-web-application-project-templates.md)
- [Publier sur Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
