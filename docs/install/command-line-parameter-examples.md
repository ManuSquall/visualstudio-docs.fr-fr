---
title: "Exemples de paramètres de ligne de commande pour l’installation de Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 05/06/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
author: timsneath
ms.author: tims
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 0f07824b29e7851e353d472838a897853e227d6c
ms.contentlocale: fr-fr
ms.lasthandoff: 05/09/2017

---
# <a name="command-line-parameter-examples-for-visual-studio-2017-installation"></a>Exemples de paramètres de ligne de commande pour l’installation de Visual Studio 2017
Voici plusieurs exemples montrant comment [utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md). Vous pouvez les personnaliser en fonction de vos besoins.

Dans chaque exemple, `vs_enterprise.exe`, `vs_professional.exe` et `vs_community.exe` représentent l’édition respective du programme d’amorçage de Visual Studio, qui est le petit fichier (environ 1 Mo) qui lance le processus de téléchargement. Si vous utilisez une autre édition, remplacez le nom du programme d’amorçage comme il convient.

> [!NOTE]
> Toutes les commandes nécessitent une élévation administrative. Une invite du Contrôle de compte d’utilisateur s’affiche si le processus n’est pas démarré à partir d’une invite avec élévation de privilèges.

> [!NOTE]
>  Vous pouvez utiliser le caractère `^` à la fin d’une ligne de commande pour concaténer plusieurs lignes en une seule commande. Vous pouvez aussi simplement regrouper ces lignes sur une seule ligne. Dans PowerShell, le caractère équivalent est l’accent grave (`` ` ``). 

* Installez une instance minimale de Visual Studio, sans invites interactives, mais avec la progression affichée :
```
vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
```

* Installez une instance de bureau de Visual Studio en mode silencieux, avec le module linguistique français, avec un retour uniquement une fois le produit installé.
```
vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --includeRecommended --quiet --wait
```

> [!NOTE]
>  Le paramètre `--wait` est conçu pour être utilisé dans un fichier de commandes. Dans un fichier de commandes, l’exécution de la commande suivante s’interrompt jusqu’à ce que l’installation soit terminée. La variable d’environnement `%ERRORLEVEL%` contient la valeur de retour de la commande, comme indiqué dans la page [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

* Téléchargez l’éditeur de base de Visual Studio (configuration minimale de Visual Studio). Incluez uniquement le module linguistique anglais :

```cmd
vs_community.exe --layout C:\VS2017
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor
```

* Téléchargez le bureau .NET et les charges de travail web .NET avec tous les composants recommandés et l’extension GitHub. Incluez uniquement le module linguistique anglais :
```
vs_community.exe --layout C:\VS2017 ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Component.GitHub.VisualStudio ^
   --includeRecommended
```

* Démarrez une installation interactive de l’ensemble des charges de travail et composants disponibles dans Visual Studio 2017 Enterprise Edition :
```
vs_enterprise.exe --all --includeRecommended --includeOptional
```

* Installez une deuxième instance nommée de Visual Studio 2017 Professional sur un ordinateur sur lequel Visual Studio 2017 Community Edition est déjà installé, avec prise en charge du développement Node.js :
```
vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --includeRecommended --nickname VSforNode
```

* Supprimez le composant Outils de profilage de l’instance de Visual Studio installée par défaut :
```
vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
```

## <a name="see-also"></a>Voir aussi

 * [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
 * [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
 * [Créer une installation hors connexion de Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)

