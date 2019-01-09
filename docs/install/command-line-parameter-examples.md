---
title: Exemples de paramètres de ligne de commande pour l’installation
description: Personnalisez ces exemples pour créer votre propre installation en ligne de commande de Visual Studio.
ms.date: 11/14/2018
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6584d1b1864712a1c97b8d2405e7b366c5dd69d6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53989985"
---
# <a name="command-line-parameter-examples-for-visual-studio-2017-installation"></a>Exemples de paramètres de ligne de commande pour l’installation de Visual Studio 2017

Voici plusieurs exemples montrant comment [utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md). Vous pouvez les personnaliser en fonction de vos besoins.

Dans chaque exemple, `vs_enterprise.exe`, `vs_professional.exe` et `vs_community.exe` représentent l’édition respective du programme d’amorçage de Visual Studio, qui est le petit fichier (environ 1 Mo) qui lance le processus de téléchargement. Si vous utilisez une autre édition, remplacez le nom du programme d’amorçage comme il convient.

> [!NOTE]
> Toutes les commandes nécessitent une élévation administrative. Une invite du Contrôle de compte d’utilisateur s’affiche si le processus n’est pas démarré à partir d’une invite avec élévation de privilèges.
>
> [!NOTE]
>  Vous pouvez utiliser le caractère `^` à la fin d’une ligne de commande pour concaténer plusieurs lignes en une seule commande. Vous pouvez aussi simplement regrouper ces lignes sur une seule ligne. Dans PowerShell, le caractère équivalent est l’accent grave (`` ` ``).

## <a name="using---installpath"></a>Utilisation de --installPath

* Installez une instance minimale de Visual Studio, sans invites interactives, mais avec la progression affichée :

  ```cmd
  vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
  ```

* Mettez à jour une instance Visual Studio en utilisant la ligne de commande, sans invites interactives, mais avec la progression affichée :

  ```cmd
  vs_enterprise.exe --update --quiet --wait
  vs_enterprise.exe update --wait --passive --norestart --installPath "C:\installPathVS"
  ```

  > [!NOTE]
  > Les deux commandes sont requises. La première commande met à jour le programme d’installation de Visual Studio. La seconde commande met à jour l’instance de Visual Studio. Pour éviter l’affichage d’une boîte de dialogue Contrôle de compte d’utilisateur, exécutez l’invite de commande en tant qu’administrateur.

* Installez une instance de bureau de Visual Studio en mode silencieux, avec le module linguistique français, avec un retour uniquement une fois le produit installé.

  ```cmd
  vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --includeRecommended --quiet --wait
  ```

  > [!NOTE]
  > Le paramètre `--wait` est conçu pour être utilisé dans un fichier de commandes. Dans un fichier de commandes, l’exécution de la commande suivante s’interrompt jusqu’à ce que l’installation soit terminée. La variable d’environnement `%ERRORLEVEL%` contient la valeur de retour de la commande, comme indiqué dans la page [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

## <a name="using---layout"></a>Utilisation de --layout

* Téléchargez l’éditeur de base de Visual Studio (configuration minimale de Visual Studio). Incluez uniquement le module linguistique anglais :

  ```cmd
  vs_community.exe --layout C:\VS2017
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor
  ```

* Téléchargez le bureau .NET et les charges de travail web .NET avec tous les composants recommandés et l’extension GitHub. Incluez uniquement le module linguistique anglais :

  ```cmd
  vs_community.exe --layout C:\VS2017 ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Component.GitHub.VisualStudio ^
   --includeRecommended
  ```

## <a name="using---includerecommended"></a>Utilisation de --includeRecommended

* Démarrez une installation interactive de l’ensemble des charges de travail et composants disponibles dans Visual Studio 2017 Enterprise Edition :

  ```cmd
  vs_enterprise.exe --all --includeRecommended --includeOptional
  ```

* Installez une deuxième instance nommée de Visual Studio 2017 Professional sur un ordinateur sur lequel Visual Studio 2017 Community Edition est déjà installé, avec prise en charge du développement Node.js :

  ```cmd
  vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --includeRecommended --nickname VSforNode
  ```

## <a name="using---remove"></a>Utilisation de --remove

* Supprimez le composant Outils de profilage de l’instance de Visual Studio installée par défaut :

  ```cmd
  vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

## <a name="using---path"></a>Utilisation de --path

Ces paramètres de ligne de commande sont **nouveaux dans 15.7**. Pour plus d’informations à leur sujet, consultez la page [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

* Utilisation des chemins install, cache et shared :

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache" --path shared="C:\VS\shared"`

* Utilisation des chemins install et cache uniquement :

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache"`

* Utilisation des chemins install et shared uniquement :

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path shared="C:\VS\shared"`

* Utilisation du chemin install uniquement :

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS"`

## <a name="using-export"></a>Utilisation d’export

Cette commande de ligne de commande est **nouvelle dans la version 15.9**. Pour plus d’informations à son sujet, consultez la page [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

* Utilisation d’export pour enregistrer la sélection à partir d’une installation :

```cmd
"C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --installPath "C:\VS" --config "C:\.vsconfig"
```

* Utilisation d’export pour enregistrer une sélection personnalisée à partir de zéro :

```cmd
"C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --config "C:\.vsconfig"
```

## <a name="using---config"></a>Utilisation de --config

Ce paramètre de ligne de commande est **nouveau dans la version 15.9**. Pour plus d’informations à son sujet, consultez la page [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

* Utilisation de --config pour installer les composants et charges de travail à partir d’un fichier de configuration d’installation enregistré :

```cmd
vs_enterprise.exe --config "C:\.vsconfig" --installPath "C:\VS"
```

* Utilisation de --config pour ajouter des composants et charges de travail à une installation existante :

```cmd
vs_enterprise.exe modify --installPath "C:\VS" --config "C:\.vsconfig"
```


[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Créer une installation hors connexion de Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
