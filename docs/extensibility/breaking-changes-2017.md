---
title: Dernières modifications dans l’extensibilité de Visual Studio 2017
description: Découvrez les détails techniques des modifications avec rupture apportées au modèle d’extensibilité dans Visual Studio 2017 et ce que vous pouvez faire pour les résoudre.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c07d48eb63c727701c3b6fcde9d405f9c96abec1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068191"
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Modifications de l’extensibilité de Visual Studio 2017

Visual Studio 2017 offre une [expérience d’installation Visual Studio plus rapide et plus légère](https://devblogs.microsoft.com/visualstudio/faster-leaner-visual-studio-installer) qui réduit l’impact de Visual Studio sur les systèmes des utilisateurs tout en offrant aux utilisateurs un meilleur choix sur les charges de travail et les fonctionnalités qui sont installées. Pour prendre en charge ces améliorations, nous avons apporté des modifications au modèle d’extensibilité, y compris des modifications avec rupture. Cet article décrit les détails techniques de ces modifications et ce qui peut être fait pour les résoudre.

> [!NOTE]
> Certaines informations sont des détails d’implémentation à un point dans le temps et peuvent être modifiées ultérieurement.

## <a name="changes-affecting-vsix-format-and-installation"></a>Modifications affectant le format et l’installation VSIX

Visual Studio 2017 a introduit le format VSIX v3 (version 3) pour prendre en charge l’expérience d’installation légère.

Les modifications apportées au format VSIX sont les suivantes :

* Déclaration des conditions préalables à l’installation. Pour répondre à la promesse d’une installation légère et rapide de Visual Studio, le programme d’installation offre désormais davantage d’options de configuration aux utilisateurs. Par conséquent, pour vous assurer que les fonctionnalités et composants requis par une extension sont installés, les extensions doivent déclarer leurs dépendances.

  * Le programme d’installation de Visual Studio 2017 propose automatiquement l’acquisition et l’installation des composants nécessaires pour l’utilisateur dans le cadre de l’installation de votre extension.
  * Les utilisateurs sont également avertis quand vous tentez d’installer une extension qui n’a pas été créée à l’aide du nouveau format VSIX v3, même si elles ont été marquées dans leur manifeste comme ciblant la version 15,0.

* Fonctionnalités améliorées pour le format VSIX. Pour effectuer une installation de Visual Studio à [faible impact](https://devblogs.microsoft.com/visualstudio/anatomy-of-a-low-impact-visual-studio-install) qui prend également en charge les installations côte à côte, nous n’enregistrons plus la plupart des données de configuration dans le registre système et avons déplacé des assemblys spécifiques à Visual Studio hors du GAC. Nous avons également augmenté les fonctionnalités du format VSIX et du moteur d’installation VSIX, ce qui vous permet de l’utiliser plutôt qu’un fichier MSI ou EXE pour installer vos extensions pour certains types d’installation.

Les nouvelles fonctionnalités sont les suivantes :

* Inscription dans l’instance de Visual Studio spécifiée.
* Installation en dehors du [dossier Extensions](set-install-root.md).
* Détection de l’architecture du processeur.
* Dépendance vis-à-vis des modules linguistiques séparés par une langue.
* Installation avec [prise en charge de NGen](ngen-support.md).

## <a name="build-an-extension-for-visual-studio-2017"></a>Créer une extension pour Visual Studio 2017

Les outils de conception pour la création du nouveau format de manifeste VSIX v3 sont disponibles dans Visual Studio 2017. Pour plus d’informations sur l’utilisation des outils du concepteur ou sur la réalisation de mises à jour manuelles du projet et du manifeste pour développer des extensions VSIX v3, consultez le document d’accompagnement [Comment : migrer des projets d’extensibilité vers Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) .

## <a name="change-visual-studio-user-data-path"></a>Modifier : chemin d’accès aux données utilisateur Visual Studio

Auparavant, une seule installation de chaque version majeure de Visual Studio pouvait exister sur chaque ordinateur. Pour prendre en charge les installations côte à côte de Visual Studio 2017, plusieurs chemins d’accès aux données utilisateur pour Visual Studio peuvent exister sur l’ordinateur de l’utilisateur.

Le code s’exécutant dans le processus Visual Studio doit être mis à jour pour utiliser le gestionnaire de paramètres de Visual Studio. Le code qui s’exécute en dehors du processus Visual Studio peut trouver le chemin d’accès de l’utilisateur d’une installation spécifique de Visual Studio [en suivant les instructions fournies ici](locating-visual-studio.md).

## <a name="change-global-assembly-cache-gac"></a>Modification : global assembly cache (GAC)

La plupart des assemblys principaux de Visual Studio ne sont plus installés dans le GAC. Les modifications suivantes ont été apportées afin que le code s’exécutant dans le processus Visual Studio puisse toujours trouver les assemblys requis au moment de l’exécution.

> [!NOTE]
> [INSTALLDIR] ci-dessous fait référence au répertoire racine d’installation de Visual Studio. *VSIXInstaller.exe* remplit automatiquement cette valeur, mais pour écrire du code de déploiement personnalisé, consultez la [recherche de Visual Studio](locating-visual-studio.md).

* Assemblys qui étaient uniquement installés dans le GAC :

  Ces assemblys sont maintenant installés sous <em>[INSTALLDIR] \Common7\IDE \* , * [INSTALLDIR] \Common7\IDE\PublicAssemblies</em> ou *[INSTALLDIR] \Common7\IDE\PrivateAssemblies*. Ces dossiers font partie des chemins d’accès de détection du processus Visual Studio.

* Assemblys qui ont été installés dans un chemin d’accès de non-détection et dans le GAC :

  * La copie dans le GAC a été supprimée du programme d’installation.
  * Un fichier *. pkgdef* a été ajouté pour spécifier une entrée de base de code pour l’assembly.

    Par exemple :

    ```
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```

    Au moment de l’exécution, le sous-système pkgdef de Visual Studio fusionne ces entrées dans le fichier de configuration du runtime du processus Visual Studio (sous *[VSAPPDATA] \devenv.exe.config*) en tant qu' [`<codeBase>`](/dotnet/framework/configure-apps/file-schema/runtime/codebase-element) éléments. Il s’agit de la méthode recommandée pour permettre au processus Visual Studio de trouver votre assembly, car il évite d’effectuer des recherches dans les chemins d’accès de détection.

### <a name="reacting-to-this-breaking-change"></a>Réaction à cette modification avec rupture

* Si votre extension s’exécute dans le processus Visual Studio :

  * Votre code sera en mesure de trouver les assemblys principaux de Visual Studio.
  * Envisagez d’utiliser un fichier *. pkgdef* pour spécifier un chemin d’accès à vos assemblys, si nécessaire.

* Si votre extension s’exécute en dehors du processus Visual Studio :

  Examinez les assemblys principaux de Visual Studio sous <em>[INSTALLDIR] \Common7\IDE \* , * [INSTALLDIR] \Common7\IDE\PublicAssemblies</em> ou *[INSTALLDIR] \Common7\IDE\PrivateAssemblies* à l’aide d’un fichier de configuration ou d’un programme de résolution d’assembly.

## <a name="change-reduce-registry-impact"></a>Modification : réduire l’impact sur le registre

### <a name="global-com-registration"></a>Inscription COM globale

* Précédemment, Visual Studio a installé de nombreuses clés de Registre dans le HKEY_CLASSES_ROOT et HKEY_LOCAL_MACHINE Hive pour prendre en charge l’inscription COM native. Pour éliminer cet impact, Visual Studio utilise désormais l' [activation sans inscription pour les composants com](/previous-versions/dotnet/articles/ms973913(v=msdn.10)).
* En conséquence, la plupart des fichiers TLB/OLB/DLL sous% ProgramFiles (x86)% \ Common Files\Microsoft Shared\MSEnv ne sont plus installés par défaut par Visual Studio. Ces fichiers sont maintenant installés sous [INSTALLDIR] avec les manifestes COM Registration-Free correspondants utilisés par le processus hôte Visual Studio.
* Par conséquent, le code externe qui s’appuie sur l’inscription COM globale pour les interfaces COM de Visual Studio ne trouvera plus ces inscriptions. Le code qui s’exécute dans le processus Visual Studio ne voit pas de différence.

### <a name="visual-studio-registry"></a>Registre Visual Studio

* Précédemment, Visual Studio a installé de nombreuses clés de Registre dans le **HKEY_LOCAL_MACHINE** du système et **HKEY_CURRENT_USER** ruches sous une clé spécifique à Visual Studio :

  * **HKLM\Software\Microsoft\VisualStudio \{ Version}**: clés de Registre créées par les programmes d’installation MSI et les extensions par ordinateur.
  * **HKCU\Software\Microsoft\VisualStudio \{ Version}**: clés de Registre créées par Visual Studio pour stocker des paramètres spécifiques à l’utilisateur.
  * **HKCU\Software\Microsoft\VisualStudio \{ Version} _Config**: une copie de la clé HKLM de Visual Studio ci-dessus, ainsi que les clés de Registre fusionnées à partir des fichiers *. pkgdef* par extensions.

* Pour réduire l’impact sur le registre, Visual Studio utilise désormais la fonction [RegLoadAppKey](/windows/desktop/api/winreg/nf-winreg-regloadappkeya) pour stocker les clés de Registre dans un fichier binaire privé sous *[VSAPPDATA] \privateregistry.bin*. Seul un très petit nombre de clés spécifiques à Visual Studio restent dans le registre système.
* Le code existant s’exécutant dans le processus Visual Studio n’est pas affecté. Visual Studio redirige toutes les opérations du Registre sous la clé spécifique de Visual Studio HKCU vers le registre privé. La lecture et l’écriture dans d’autres emplacements du Registre continuent à utiliser le registre système.
* Le code externe devra charger et lire à partir de ce fichier pour les entrées de Registre Visual Studio.

### <a name="react-to-this-breaking-change"></a>Réagir à cette modification avec rupture

* Le code externe doit être converti pour utiliser Registration-Free l’activation des composants COM.
* Les composants externes peuvent trouver l’emplacement de Visual Studio [en suivant les instructions fournies ici](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup).
* Nous recommandons que les composants externes utilisent le [Gestionnaire de paramètres externes](/dotnet/api/microsoft.visualstudio.settings.externalsettingsmanager) au lieu de lire/écrire directement dans les clés de Registre Visual Studio.
* Vérifiez si les composants que votre extension utilise peuvent avoir implémenté une autre technique d’inscription. Par exemple, les extensions de débogueur peuvent être en mesure de tirer parti de la nouvelle [inscription com msvsmon du fichier JSON](migrate-debugger-COM-registration.md).