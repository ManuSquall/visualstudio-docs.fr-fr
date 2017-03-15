---
title: "Créer une installation hors connexion de Visual Studio 2017 RC | Microsoft Docs"
description: "Découvrez comment créer une installation hors connexion de Visual Studio."
ms.custom: 
ms.date: 02/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- ISO [Visual Studio]
ms.assetid: 7bd7e724-7bfd-43f1-9935-981919be5a00
author: TerryGLee
ms.author: tglee
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
translationtype: Human Translation
ms.sourcegitcommit: d4d1bd45ce697017480b3f63d0c7feb5ab20d2d6
ms.openlocfilehash: 33e765d205aa7ad8a3d8c5b871863ab659092a77
ms.lasthandoff: 02/22/2017

---
# <a name="create-an-offline-installation-of-visual-studio-2017-rc"></a>Créer une installation hors connexion de Visual Studio 2017 RC

## <a name="create-a-layout"></a>Créer une disposition
Si vous voulez installer [Visual Studio 2017 RC](https://www.visualstudio.com/vs/visual-studio-2017-rc/) sur un autre ordinateur qui n’a pas accès à Internet, vous pouvez le faire en créant d’abord une disposition d’installation hors connexion qui contient tous les fichiers Visual Studio et les composants dont vous avez besoin.

Vous pouvez ensuite installer Visual Studio sur l’ordinateur cible à l’aide de la disposition d’installation hors connexion que vous avez créée.     

> [!WARNING]
> Actuellement, le kit SDK Android ne prend pas en charge les installations hors connexion. Si vous installez des éléments de l’installation du kit SDK Android sur un ordinateur qui n’est pas connecté à internet, l’installation peut échouer. Pour plus d’informations, accédez à la section [Résoudre les problèmes d’une installation hors connexion](#tshootofflineinstall) dans cette rubrique.


#### <a name="to-create-an-offline-installation-layout-of-visual-studio"></a>Pour créer une disposition d’installation hors connexion de Visual Studio
1. Téléchargez le fichier exécutable d’installation de Visual Studio sur un lecteur de votre ordinateur local.
  Par exemple, [téléchargez le fichier vs_enterprise.exe](https://www.visualstudio.com/vs/visual-studio-2017-rc/).
2. Exécutez `vs_enterprise.exe` avec les arguments suivants (commutateurs) à partir d’une invite de commandes :

   a. Ajoutez `--layout <path>`, où `<path>` est l’emplacement où télécharger la disposition. Notez que les chemins relatifs (par exemple, `..\vs2017`) ne sont pas pris en charge actuellement. Par défaut, toutes les langues sont téléchargées. (Voir l’exemple A.)

   b. Limitez le téléchargement à un sous-ensemble de langues disponibles en fournissant l’argument `--lang <language>`, où `<language>` désigne un ou plusieurs paramètres régionaux de langue.  (Voir les exemples B et C.)

   c. Limitez le téléchargement à un sous-ensemble de composants et de charges de travail en fournissant l’argument `--add <package ID>`. De cette façon, vous ne téléchargez que les charges de travail et les composants (et leurs dépendances) que vous spécifiez. (Voir les exemples D et E.)

   Pour obtenir la liste complète des ID de charge de travail et de composant triés par produit Visual Studio, consultez notre page [ID de composant et de charge de travail Visual Studio 2017](https://aka.ms/vs2017componentids).

### <a name="examples"></a>Exemples
**Exemple A** : Télécharger tous composants et les charges de travail dans toutes les langues
  > ```vs_enterprise.exe --layout C:\vs2017```

**Exemple B** : Télécharger tous composants et les charges de travail dans une langue  
  > ```vs_enterprise.exe --layout C:\vs2017 --lang en-US```

**Exemple C** : Télécharger tous composants et les charges de travail dans plusieurs langues
  > ```vs_enterprise.exe --layout C:\vs2017 --lang en-US de-DE ja-JP```

**Exemple D** : Télécharger une charge de travail dans toutes les langues
  > ```vs_enterprise.exe --layout C:\vs2017 --add Microsoft.VisualStudio.Workload.Azure ```

**Exemple E** : Télécharger deux charges de travail et un composant facultatif dans trois langues
  > ```vs_enterprise.exe --layout C:\vs2017 --add Microsoft.VisualStudio.Workload.Azure Microsoft.VisualStudio.Workload.ManagedDesktop Component.GitHub.VisualStudio --lang en-US de-DE ja-JP ```

  > [!WARNING]
  > Le paramètre --layout échoue si le nom du fichier .exe d’installation comprend des chiffres. Pour contourner ce problème, vous devez supprimer les chiffres du nom du fichier, par exemple, renommez *vs_community__198521760.1486960229.exe* en ***vs_community.exe***.

### <a name="language-locales"></a>Paramètres régionaux de langue

| Paramètres régionaux de langue | Langage |
| -----   | ----- |
| cs-CZ    | Tchèque |
| de-DE    | Allemand |
| fr-FR    | Anglais |
| es-ES    | Espagnol |
| fr-FR    | Français |
| it-IT    | Italien |
| ja-JP    | Japonais |
| ko-KR    | Coréen |
| pl-PL    | Polonais |
| pt-BR    | Portugais - Brésil |
| ru-RU    | Russe |
| tr-TR    | Turc |
| zh-CN    | Chinois (simplifié) |
| zh-TW    | Chinois (traditionnel) |


## <a name="install-from-a-layout"></a>Installation à partir d’une disposition
#### <a name="to-install-visual-studio-from-an-offline-installation-layout"></a>Pour installer Visual Studio à partir d’une disposition d’installation hors connexion
1. Sur l’ordinateur cible, accédez au dossier **Certificats**, qui se trouve dans le dossier Disposition.
2. Cliquez avec le bouton droit sur chaque certificat du dossier **Certificats** et installez-les.

  (Si vous êtes invité à entrer un mot de passe après avoir installé un certificat, cliquez sur **Continuer**.)  
3. Exécutez `vs_enterprise.exe` à partir du dossier **Disposition**.

Remarque : Si vous effectuez l’installation à partir d’une disposition partielle et que vous sélectionnez des charges de travail, des composants ou des langues qui ne sont pas disponibles dans la disposition, le programme d’installation tente de les télécharger.  Si vous n’avez pas accès à Internet, ces éléments ne sont pas installés.

> [!CAUTION]
> La disposition d’installation hors connexion crée actuellement des fichiers avec des autorisations limitées (ACL) qui empêchent l’accès à tous les utilisateurs.  Vérifiez que vous ajustez les autorisations (ACL) pour accorder un accès en lecture aux autres utilisateurs *avant* de partager l’installation hors connexion.

## <a name="update-an-installation-layout"></a>Mettre à jour une disposition d’installation
Quand des mises à jour sont disponibles pour Visual Studio 2017 RC, vous pouvez réexécuter la commande `--layout`, en pointant vers le même dossier de disposition, pour vérifier que le dossier contient les composants les plus récents. Seuls les composants qui ont été mis à jour depuis la dernière exécution de `--layout` sont téléchargés.

## <a id="tshootofflineinstall"> </a>Résoudre les problèmes d’une disposition d’installation
Quand vous effectuez une installation hors connexion à partir de votre cache d’installation hors connexion, des messages d’avertissement peuvent s’afficher pour vous indiquer l’impossibilité d’installer certains composants et packages. Le tableau suivant présente les solutions possibles à ces scénarios.

| Composant ou package | Solution |
| -------------------- | -------- |
|Programme d’installation du SDK Android (Niveau API)| Vous devez avoir une connexion Internet pour installer les packages du SDK Android (niveau API). Si vous êtes sur un réseau limité, vous devez autoriser l’accès aux URL suivantes quand vous installez Visual Studio : <br><br> - http://dl.google.com:443 <br>- http://dl-ssl.google.com:443 <br>  - https://dl-ssl.google.com/android/repository/*<br><br>Pour plus d’informations sur la résolution des éventuels problèmes avec les paramètres de proxy, consultez le billet de blog [Visual Studio install failures (Android SDK Setup) behind a proxy](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/) (Échec de l’installation de Visual Studio (Programme d’installation du SDK Android) derrière un proxy).  |  

 > [!IMPORTANT]
 > Alors que Visual Studio 2017 RC est généralement pris en charge pour une utilisation dans un environnement de production, les charges de travail et les composants qui sont marqués « Préversion » dans l’interface utilisateur de l’installation ne le sont pas.

 ## <a name="see-also"></a>Voir aussi
 * [Installer Visual Studio](install-visual-studio.md)
 * [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
 * [Signaler un problème avec Visual Studio](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

