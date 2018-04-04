---
title: Exemples de paramètres de ligne de commande pour l’installation de Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 05/06/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
author: tglee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ddb6afe950c2563f7ded04efbdd2b441a8c72e30
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2018
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

* Mettez à jour une instance Visual Studio en utilisant la ligne de commande, sans invites interactives, mais avec la progression affichée :
```
vs_enterprise.exe --update --quiet --wait
vs_enterprise.exe update --wait --passive --norestart --installPath "C:\installPathVS"
```

> [!NOTE]
> Les deux commandes sont requises. La première commande met à jour le programme d’installation de Visual Studio. La seconde commande met à jour l’instance de Visual Studio. Pour éviter l’affichage d’une boîte de dialogue Contrôle de compte d’utilisateur, exécutez l’invite de commande en tant qu’administrateur.

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

## <a name="get-support"></a>Obtenir de l’aide
Parfois, des problèmes peuvent se produire. Si votre installation de Visual Studio échoue, consultez la page [Résolution des problèmes d’installation et de mise à niveau de Visual Studio 2017](troubleshooting-installation-issues.md). Si aucune étape de résolution des problèmes ne vous aide, vous pouvez nous contacter pour une conversation en direct sur une assistance à l’installation (en anglais uniquement). Pour plus de détails, consultez la [page du support Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Voici d’autres options de support :
* Vous pouvez nous signaler des problèmes au niveau d’un produit via l’outil [Signaler un problème](../ide/how-to-report-a-problem-with-visual-studio-2017.md) qui s’affiche dans le programme d’installation de Visual Studio et dans l’IDE de Visual Studio.
* Vous pouvez nous faire part d’une suggestion de produit via [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Vous pouvez suivre les problèmes au niveau d’un produit sur le site [Visual Studio Developer Community](https://developercommunity.visualstudio.com/) et y poser des questions et obtenir des réponses.
* Vous pouvez également communiquer avec nous et d’autres développeurs Visual Studio en prenant part à notre [conversation Visual Studio dans la communauté Gitter ](https://gitter.im/Microsoft/VisualStudio)  (Cette option nécessite un compte [GitHub](https://github.com/).)

## <a name="see-also"></a>Voir aussi

 * [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
 * [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
 * [Créer une installation hors connexion de Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
