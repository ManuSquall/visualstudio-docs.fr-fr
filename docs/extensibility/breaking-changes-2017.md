---
title: Breaking Changes in Visual Studio 2017 extensibility
titleSuffix: ''
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b3a04c925ef897171de51c73c90973a12c3b17d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739973"
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Changements dans l’extéabilité Visual Studio 2017

Visual Studio 2017 offre une [expérience d’installation Visual Studio plus rapide et plus légère](https://devblogs.microsoft.com/visualstudio/faster-leaner-visual-studio-installer) qui réduit l’impact de Visual Studio sur les systèmes utilisateurs tout en donnant aux utilisateurs un plus grand choix sur les charges de travail et les fonctionnalités qui sont installées. Pour soutenir ces améliorations, nous avons apporté des changements au modèle d’extéabilité, y compris quelques changements de rupture. Cet article décrit les détails techniques de ces changements et ce qui peut être fait pour y remédier.

> [!NOTE]
> Certaines informations sont des détails de mise en œuvre ponctuelles et peuvent être modifiées plus tard.

## <a name="changes-affecting-vsix-format-and-installation"></a>Changements affectant le format et l’installation VSIX

Visual Studio 2017 a introduit le format VSIX v3 (version 3) pour soutenir l’expérience d’installation légère.

Les modifications apportées au format VSIX comprennent :

* Déclaration des conditions préalables à l’installation. Pour tenir la promesse d’un studio visuel léger et à installation rapide, l’installateur offre maintenant plus d’options de configuration aux utilisateurs. Par conséquent, pour s’assurer que les caractéristiques et les composants requis par une extension sont installés, les extensions doivent déclarer leurs dépendances.

  * L’installateur Visual Studio 2017 propose automatiquement d’acquérir et d’installer les composants nécessaires pour l’utilisateur dans le cadre de l’installation de votre extension.
  * Les utilisateurs sont également avertis lorsqu’ils tentent d’installer une extension qui n’a pas été construite en utilisant le nouveau format VSIX v3, même s’ils ont été marqués dans leur manifeste comme la version de ciblage 15.0.

* Capacités améliorées pour le format VSIX. Pour livrer sur une [installation à faible impact](https://devblogs.microsoft.com/visualstudio/anatomy-of-a-low-impact-visual-studio-install) de Visual Studio qui prend également en charge les installations côte à côte, nous n’économisons plus la plupart des données de configuration au registre du système et avons déplacé les assemblages spécifiques Visual Studio hors de la GAC. Nous avons également augmenté les capacités du format VSIX et du moteur d’installation VSIX, vous permettant de l’utiliser plutôt qu’un MSI ou EXE pour installer vos extensions pour certains types d’installation.

Les nouvelles capacités comprennent :

* Inscription dans l’instance Visual Studio spécifiée.
* Installation à l’extérieur du [dossier d’extensions](set-install-root.md).
* Détection de l’architecture du processeur.
* Dépendance à l’égard des paquets linguistiques séparés.
* Installation avec [support NGEN](ngen-support.md).

## <a name="build-an-extension-for-visual-studio-2017"></a>Construire une extension pour Visual Studio 2017

L’outillage design pour la rédaction du nouveau format manifeste VSIX v3 est disponible dans Visual Studio 2017. Voir le document d’accompagnement [Comment : Migrer les projets d’extensibility à Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) pour plus de détails sur l’utilisation des outils de concepteur ou la mise à jour manuelle du projet et manifestez pour développer des extensions VSIX v3.

## <a name="change-visual-studio-user-data-path"></a>Changement : Chemin de données utilisateur Visual Studio

Auparavant, une seule installation de chaque version majeure de Visual Studio pouvait exister sur chaque machine. Pour prendre en charge les installations côte à côte de Visual Studio 2017, plusieurs parcours de données utilisateur pour Visual Studio peuvent exister sur la machine de l’utilisateur.

Le code fonctionnant à l’intérieur du processus Visual Studio doit être mis à jour pour utiliser le Visual Studio Settings Manager. Code fonctionnant en dehors du processus Visual Studio peut trouver le chemin utilisateur d’une installation spécifique Visual Studio [en suivant les conseils ici](locating-visual-studio.md).

## <a name="change-global-assembly-cache-gac"></a>Changement : Global Assembly Cache (GAC)

La plupart des assemblages de base Visual Studio ne sont plus installés dans le GAC. Les modifications suivantes ont été apportées afin que le code en cours d’exécution dans le processus Visual Studio puisse toujours trouver les assemblages requis au moment de l’exécution.

> [!NOTE]
> [INSTALLDIR] ci-dessous se réfère à l’installation root directory de Visual Studio. *VSIXInstaller.exe* va automatiquement remplir cela, mais pour écrire du code de déploiement personnalisé, s’il vous plaît lire [la localisation Visual Studio](locating-visual-studio.md).

* Assemblées qui n’ont été installées que dans le GAC :

  Ces assemblages sont maintenant installés sous <em>[INSTALLDIR]\*-Common7-IDE , '[INSTALLDIR]'Common7'IDE’PublicAssemblies</em> ou *[INSTALLDIR] 'Common7'IDE’PrivateAssemblies*. Ces dossiers font partie des voies de sondage du processus Visual Studio.

* Assemblées qui ont été installées dans un chemin non-sondage et dans le GAC:

  * La copie du GAC a été retirée de la configuration.
  * Un fichier *.pkgdef* a été ajouté pour spécifier une entrée de base de code pour l’assemblage.

    Par exemple :

    ```
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```

    Au moment de l’exécution, le sous-système Visual Studio pkgdef fusionne ces entrées dans le fichier de configuration de temps d’exécution du processus Visual Studio (sous *[VSAPPDATA]-devenv.exe.config*) en tant qu’éléments. [`<codeBase>`](/dotnet/framework/configure-apps/file-schema/runtime/codebase-element) C’est la façon recommandée de laisser le processus Visual Studio trouver votre assemblage, car il évite la recherche à travers les chemins de sondage.

### <a name="reacting-to-this-breaking-change"></a>Réagir à ce changement radical

* Si votre extension s’exécute dans le processus Visual Studio :

  * Votre code sera en mesure de trouver des assemblages de base Visual Studio.
  * Envisagez d’utiliser un fichier *.pkgdef* pour spécifier un chemin vers vos assemblages si nécessaire.

* Si votre extension est en cours d’exécution en dehors du processus Visual Studio :

  Envisagez de rechercher des assemblages de base visual studio dans le cadre <em>de [INSTALLDIR] -Common7-IDE\*, '[INSTALLDIR] 'Common7'IDE’PublicAssemblies</em> ou *[INSTALLDIR]-Common7'IDE’PrivateAssemblies* utilisant des fichiers de configuration ou un résolveur d’assemblage.

## <a name="change-reduce-registry-impact"></a>Changement : Réduire l’impact du registre

### <a name="global-com-registration"></a>Enregistrement GLOBAL COM

* Auparavant, Visual Studio installait de nombreuses clés de registre dans les ruches HKEY_CLASSES_ROOT et HKEY_LOCAL_MACHINE pour soutenir l’enregistrement natif de COM. Pour éliminer cet impact, Visual Studio utilise maintenant [l’activation sans inscription pour les composants COM](https://msdn.microsoft.com/library/ms973913.aspx).
* En conséquence, la plupart des fichiers TLB / OLB / DLL sous %ProgramFiles (x86)% -Common Files-Microsoft Shared-MSEnv ne sont plus installés par défaut par Visual Studio. Ces fichiers sont maintenant installés dans le cadre de [INSTALLDIR] avec des manifestes COM sans inscription correspondant utilisés par le processus d’hôte Visual Studio.
* Par conséquent, le code externe qui s’appuie sur l’enregistrement GLOBAL de COM pour les interfaces Visual Studio COM ne trouvera plus ces enregistrements. Le code fonctionnant à l’intérieur du processus Visual Studio ne verra pas de différence.

### <a name="visual-studio-registry"></a>Registre visual des studios

* Auparavant, Visual Studio installait de nombreuses clés de registre dans les **ruches HKEY_LOCAL_MACHINE** et **HKEY_CURRENT_USER du** système sous une clé spécifique à Visual Studio :

  * **HKLM-Software-Microsoft-VisualStudio\{Version :** Clés de registre créées par des installateurs MSI et des extensions par machine.
  * **HKCU-Software-Microsoft-VisualStudio\{Version :** Clés de registre créées par Visual Studio pour stocker des paramètres spécifiques à l’utilisateur.
  * **HKCU-Software-Microsoft-VisualStudio\{Version-_Config**: Une copie de la clé Visual Studio HKLM ci-dessus, ainsi que les touches de registre fusionnées à partir de fichiers *.pkgdef* par extensions.

* Pour réduire l’impact sur le registre, Visual Studio utilise maintenant la fonction [RegLoadAppKey](/windows/desktop/api/winreg/nf-winreg-regloadappkeya) pour stocker les clés de registre dans un fichier binaire privé dans le cadre *de [VSAPPDATA]-privateregistry.bin*. Il ne reste qu’un très petit nombre de clés spécifiques à Visual Studio dans le registre du système.
* Le code existant fonctionnant à l’intérieur du processus Visual Studio n’est pas affecté. Visual Studio redirigera toutes les opérations d’enregistrement sous la clé spécifique du studio visuel HKCU au registre privé. La lecture et l’écriture à d’autres emplacements d’enregistrement continueront d’utiliser le registre du système.
* Le code externe devra charger et lire à partir de ce fichier pour les entrées de registre Visual Studio.

### <a name="react-to-this-breaking-change"></a>Réagissez à ce changement de rupture

* Le code externe doit également être converti pour utiliser l’activation sans inscription pour les composants COM.
* Composants externes peuvent trouver l’emplacement Visual Studio [en suivant les conseils ici](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup).
* Nous recommandons que les composants externes utilisent le [gestionnaire des paramètres externes](/dotnet/api/microsoft.visualstudio.settings.externalsettingsmanager) au lieu de lire/écrire directement sur les clés du registre Visual Studio.
* Vérifiez si les composants que votre extension utilise peuvent avoir mis en œuvre une autre technique d’enregistrement. Par exemple, les extensions de débbugger peuvent être en mesure de profiter de la nouvelle [msvsmon JSON-fichier COM enregistrement](migrate-debugger-COM-registration.md).
