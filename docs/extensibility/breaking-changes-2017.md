---
title: Modifications avec rupture dans Visual Studio 2017 extensibilité
titleSuffix: ''
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: e7363a0779721e4fb36106d6ee77324c341517ba
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62926833"
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Nouveautés d’extensibilité de Visual Studio 2017

Visual Studio 2017 fournit un [expérience d’installation de Visual Studio plus rapide et léger](https://devblogs.microsoft.com/visualstudio/faster-leaner-visual-studio-installer) afin de réduire l’impact de Visual Studio sur les systèmes de l’utilisateur tout en donnant aux utilisateurs un plus grand choix sur les charges de travail et les fonctionnalités qui sont installé. Pour prendre en charge ces améliorations, nous avons apporté des modifications au modèle d’extensibilité, y compris des modifications avec rupture. Cet article décrit les détails techniques de ces modifications et ce qui peut être fait pour les résoudre.

> [!NOTE]
> Certaines informations constituent les détails d’implémentation de point-à-temps et peuvent être modifiées ultérieurement.

## <a name="changes-affecting-vsix-format-and-installation"></a>Modifications affectant l’installation et du format VSIX

Visual Studio 2017 introduit la v3 VSIX format (version 3) pour prendre en charge de l’expérience d’installation allégé.

Modifications du format VSIX sont les suivantes :

* Déclaration des conditions préalables d’installation. Pour remettre la promesse d’un léger et rapide-installation de Visual Studio, le programme d’installation propose désormais des options de configuration supplémentaires aux utilisateurs. Par conséquent, pour vous assurer que les fonctionnalités et les composants requis par une extension sont installés, les extensions doivent déclarent leurs dépendances.

  * Le programme d’installation de Visual Studio 2017 offre automatiquement acquérir et installer les composants nécessaires pour l’utilisateur dans le cadre de l’installation de votre extension.
  * Également, les utilisateurs sont avertis lorsque vous tentez d’installer une extension qui n’a pas créée à l’aide du nouveau format VSIX v3, même s’ils ont été marqués dans leur manifeste en ciblant la version 15.0.

* Capacités améliorées pour le format VSIX. Pour répondre à une [installation low-impact](https://devblogs.microsoft.com/visualstudio/anatomy-of-a-low-impact-visual-studio-install) de Visual Studio qui prend également en charge les installations côte à côte, nous n’en avez plus enregistrer la plupart des données de configuration dans le Registre système et ont été déplacés hors du GAC, les assemblys spécifique de Visual Studio. Nous avons également augmenté les fonctionnalités du format VSIX et moteur d’installation VSIX, ce qui vous permet d’utiliser plutôt que des EXE ou un MSI pour installer vos extensions pour certains types d’installation.

Les nouvelles fonctionnalités sont les suivantes :

* Inscription dans l’instance spécifiée de Visual Studio.
* Installation en dehors de la [dossier extensions](set-install-root.md).
* Détection de l’architecture processeur.
* Dépendance sur le langage séparées par des modules linguistiques.
* Installation avec [prise en charge NGEN](ngen-support.md).

## <a name="build-an-extension-for-visual-studio-2017"></a>Générer une extension pour Visual Studio 2017

Concepteur d’outils pour la création du nouveau format de manifeste VSIX v3 est disponible dans Visual Studio 2017. Consultez le document [Comment : Migrer des projets d’extensibilité vers Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) pour plus d’informations sur l’utilisation des outils concepteurs ou effectuer des mises à jour manuelles au projet et le manifeste pour développer des extensions VSIX v3.

## <a name="change-visual-studio-user-data-path"></a>Modification : Chemin des données utilisateur Visual Studio

Auparavant, une seule installation de chaque version majeure de Visual Studio peut exister sur chaque ordinateur. Pour prendre en charge les installations côte à côte de Visual Studio 2017, plusieurs chemins de données utilisateur pour Visual Studio peuvent exister sur l’ordinateur de l’utilisateur.

Code qui s’exécute au sein du processus de Visual Studio doit être mis à jour pour utiliser le Gestionnaire de paramètres Visual Studio. Code qui s’exécute en dehors du processus Visual Studio peut trouver le chemin d’accès de l’utilisateur d’une installation de Visual Studio spécifique [en suivant les conseils donnés ici](locating-visual-studio.md).

## <a name="change-global-assembly-cache-gac"></a>Modification : Global Assembly Cache (GAC)

La plupart des assemblys principaux de Visual Studio ne sont plus installés dans le GAC. Les modifications suivantes ont été apportées afin que code s’exécutant dans le processus de Visual Studio peut toujours trouver les assemblys requis lors de l’exécution.

> [!NOTE]
> [INSTALLDIR] ci-dessous fait référence au répertoire racine d’installation de Visual Studio. *VSIXInstaller.exe* sera remplir automatiquement, mais pour écrire le code de déploiement personnalisé, veuillez lire [recherche de Visual Studio](locating-visual-studio.md).

* Assemblys qui ont été installés uniquement dans le GAC :

   Ces assemblys sont maintenant installés sous <em>[INSTALLDIR] \Common7\IDE\*, * [INSTALLDIR] \Common7\IDE\PublicAssemblies</em> ou *[INSTALLDIR] \Common7\IDE\PrivateAssemblies*. Ces dossiers font partie de chemins de détection du processus Visual Studio.

* Assemblys qui ont été installés dans un chemin d’accès non détection et dans le GAC :

   * La copie dans le GAC a peut-être été retirée le programme d’installation.
   * Un *.pkgdef* fichier a été ajouté pour spécifier une entrée de base de code pour l’assembly.

      Exemple :

      ```xml
      [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
      "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
      "publicKeyToken"="Public Key Token"
      "culture"="neutral"
      "version"=15.0.0.0
      ```

      Lors de l’exécution, le sous-système de pkgdef Visual Studio fusionne ces entrées dans le fichier de configuration du runtime du processus Visual Studio (sous *[VSAPPDATA]\devenv.exe.config*) en tant que [ `<codeBase>` ](/dotnet/framework/configure-apps/file-schema/runtime/codebase-element) éléments. Il s’agit de la méthode recommandée pour vous permettre du processus de Visual Studio de trouver votre assembly, car elle évite d’effectuer une recherche dans les chemins d’accès de détection.

### <a name="reacting-to-this-breaking-change"></a>Réagir à cette modification avec rupture

* Si votre extension s’exécute au sein du processus de Visual Studio :

   * Votre code sera en mesure de trouver les assemblys principaux de Visual Studio.
   * Envisagez d’utiliser un *.pkgdef* fichier pour spécifier un chemin d’accès à vos assemblys, si nécessaire.

* Si votre extension s’exécute en dehors du processus de Visual Studio :

   Prendre en compte la recherche d’assemblys principaux de Visual Studio sous <em>[INSTALLDIR] \Common7\IDE\*, * [INSTALLDIR] \Common7\IDE\PublicAssemblies</em> ou *[INSTALLDIR] \Common7\IDE\PrivateAssemblies*à l’aide du résolveur de fichier ou l’assembly de configuration.

## <a name="change-reduce-registry-impact"></a>Modification : Réduire l’impact sur le Registre

### <a name="global-com-registration"></a>Inscription de COM globale

* Auparavant, Visual Studio installé de clés de Registre dans les ruches HKEY_CLASSES_ROOT et HKEY_LOCAL_MACHINE pour prendre en charge d’inscription COM native. Pour éviter cet impact, Visual Studio utilise désormais [l’Activation sans inscription pour les composants COM](https://msdn.microsoft.com/library/ms973913.aspx).
* Par conséquent, la plupart des TLB / OLB / fichiers DLL sous % ProgramFiles (x86) %\Common Files\Microsoft Shared\MSEnv ne sont plus installés par défaut par Visual Studio. Ces fichiers sont maintenant installés sous [INSTALLDIR] avec des manifestes Registration-Free COM correspondants utilisés par le processus hôte de Visual Studio.
* Par conséquent, le code externe qui s’appuie sur l’inscription de COM globale pour les interfaces COM Visual Studio sera ne trouve plus ces inscriptions. Code qui s’exécute à l’intérieur du processus Visual Studio ne verrez pas de différence.

### <a name="visual-studio-registry"></a>Registre de Visual Studio

* Auparavant, Visual Studio installé de clés de Registre dans le système **HKEY_LOCAL_MACHINE** et **HKEY_CURRENT_USER** ruches sous une clé spécifique de Visual Studio :

  * **HKLM\Software\Microsoft\VisualStudio\{Version}**: Clés de Registre créées par les programmes d’installation MSI et des extensions par ordinateur.
  * **HKCU\Software\Microsoft\VisualStudio\{Version}**: Clés de Registre créées par Visual Studio pour stocker des paramètres propres à l’utilisateur.
  * **HKCU\Software\Microsoft\VisualStudio\{Version}_Config**: Une copie de la clé de Visual Studio HKLM ci-dessus, ainsi que les clés de Registre fusionné à partir de *.pkgdef* fichiers par les extensions.

* Pour réduire l’impact sur le Registre, Visual Studio utilise désormais le [RegLoadAppKey](/windows/desktop/api/winreg/nf-winreg-regloadappkeya) (fonction) pour stocker les clés de Registre dans un fichier binaire privé sous *[VSAPPDATA]\privateregistry.bin*. Uniquement un très petit nombre de clés de Visual Studio spécifiques reste dans le Registre système.
* Code existant en cours d’exécution au sein du processus de Visual Studio n’est pas affecté. Visual Studio redirige toutes les opérations de Registre sous la clé HKCU Visual Studio-spécifique au Registre privé. Lire et écrire à d’autres emplacements de Registre continue à utiliser le Registre système.
* Code externe doit charger et lire à partir de ce fichier pour les entrées de Registre de Visual Studio.

### <a name="react-to-this-breaking-change"></a>Réagir à cette modification avec rupture

* Code externe doit être converti pour utiliser l’activation sans inscription pour les composants COM et.
* Composants externes pour trouver l’emplacement de Visual Studio [en suivant les conseils donnés ici](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup).
* Nous recommandons d’utilisent des composants externes les [Gestionnaire de paramètres externe](/dotnet/api/microsoft.visualstudio.settings.externalsettingsmanager) au lieu de lecture/écriture directement aux clés de Registre de Visual Studio.
* Vérifiez si les composants à l’aide de votre extension a peut-être implémenté une autre technique pour l’inscription. Par exemple, les extensions de débogueur peuvent être en mesure de tirer parti de la nouvelle [msvsmon enregistrement JSON-fichier COM](migrate-debugger-COM-registration.md).
