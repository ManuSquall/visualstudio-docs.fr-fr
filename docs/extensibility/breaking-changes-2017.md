---
title: Modifications avec rupture dans Visual Studio 2017 extensibilité | Documents Microsoft
ms.custom: ''
ms.date: 11/09/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bff9c97b052f359f3d03e12093b1cdae86d5dfbd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107174"
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Modifications apportées à l’extensibilité de Visual Studio 2017

Avec Visual Studio 2017, nous offrons une [plus rapide, légère expérience d’installation de Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2016/04/01/faster-leaner-visual-studio-installer) afin de réduire l’impact de Visual Studio sur les systèmes de l’utilisateur, tout en donnant aux utilisateurs plus grand choix sur les fonctionnalités et les charges de travail qui sont installés. Pour prendre en charge ces améliorations, nous avez apporté des modifications au modèle d’extensibilité et qui ont effectué des modifications avec rupture à l’extensibilité de Visual Studio. Ce document décrit les détails techniques de ces modifications, et ce qui peut être fait pour les résoudre. Notez que certaines informations sont détails de l’implémentation d’un point-à-temps et peuvent être modifiées ultérieurement.

## <a name="changes-affecting-vsix-format-and-installation"></a>Modifications qui affectent l’Installation et le Format VSIX

Nous avons créé la v3 VSIX format (version 3) pour prendre en charge l’expérience d’installation de légers.

Modifications du format VSIX sont les suivantes :

* Déclaration de la configuration requise. Pour fournir la promesse de léger et rapide à l’installation de Visual Studio, le programme d’installation propose désormais davantage d’options de configuration pour les utilisateurs. Par conséquent, pour vous assurer que les fonctionnalités et les composants requis par une extension sont installés, les extensions devez déclarer leurs dépendances.
  * Le programme d’installation de Visual Studio 2017 propose automatiquement acquérir et installer les composants nécessaires pour l’utilisateur en tant que partie de l’installation de votre extension.
  * Les utilisateurs sont avertis également lorsque vous tentez d’installer une extension qui n’a pas créée en utilisant le nouveau format VSIX v3, même si elles ont été marquées dans leur manifeste en ciblant la version 15.0.
* Capacités améliorées pour le format VSIX. Pour respecter une [l’installation low impact](https://blogs.msdn.microsoft.com/visualstudio/2016/04/25/anatomy-of-a-low-impact-visual-studio-install) de Visual Studio qui prend également en charge l’installation côte à côte, nous ne sont plus enregistrer les données de configuration dans le Registre système et avez déplacé des assemblys spécifiques à Visual Studio hors du GAC. Nous avons également augmenté les fonctionnalités du format VSIX et moteur d’installation VSIX, ce qui vous permet d’installer vos extensions pour certains types d’installation plutôt que des EXE ou un fichier MSI.

  Les nouvelles fonctionnalités sont les suivantes :

  * Inscription dans l’instance spécifiée de Visual Studio.
  * Installation en dehors de la [dossier extensions](set-install-root.md).
  * Détection de l’architecture processeur.
  * Dépendance de langage séparées par des modules linguistiques.
  * Installation avec [prise en charge NGEN](ngen-support.md).

## <a name="building-an-extension-for-visual-studio-2017"></a>Génération d’une extension de Visual Studio 2017

Concepteur pour les outils pour la création de nouveau le format de manifeste VSIX v3 est désormais disponible dans Visual Studio 2017. Consultez le document d’accompagnement [Comment : migrer les projets d’extensibilité pour Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) pour plus d’informations sur à l’aide des outils du concepteur ou l’apport de mises à jour manuelles pour le projet et le manifeste pour développer les extensions VSIX v3.

## <a name="change-visual-studio-user-data-path"></a>Modification : Chemin d’accès des données utilisateur Visual Studio

Auparavant, une seule installation de chaque version majeure de Visual Studio peut exister sur chaque ordinateur. Pour prendre en charge les installations côte à côte de Visual Studio 2017, plusieurs chemins de données utilisateur pour Visual Studio peuvent exister sur l’ordinateur de l’utilisateur.

Code qui s’exécute au sein du processus Visual Studio doit être mis à jour pour utiliser le Gestionnaire de paramètres de Visual Studio. Code qui s’exécute en dehors du processus Visual Studio peut trouver le chemin d’accès de l’utilisateur d’une installation de Visual Studio spécifique [en suivant les instructions fournies ici](locating-visual-studio.md).

## <a name="change-global-assembly-cache-gac"></a>Modification : Global Assembly Cache (GAC)

La plupart des assemblys principaux de Visual Studio ne sont plus installés dans le GAC. Les modifications suivantes ont été apportées afin que le code s’exécutant dans le processus de Visual Studio peut toujours trouver les assemblys requis lors de l’exécution.

> [!NOTE]
> [INSTALLDIR] ci-dessous fait référence au répertoire racine d’installation de Visual Studio. VSIXInstaller.exe sera automatiquement le remplir, mais pour écrire du code de déploiement personnalisé, veuillez lire [recherche Visual Studio](locating-visual-studio.md).

* Assemblys qui ont été installés uniquement dans le GAC :
  * Ces assemblys sont maintenant installés sous [INSTALLDIR] \Common7\IDE\, [INSTALLDIR] \Common7\IDE\PublicAssemblies ou [INSTALLDIR] \Common7\IDE\PrivateAssemblies. Ces dossiers font partie des chemins d’accès de détection du processus Visual Studio.
* Assemblys qui ont été installés dans un chemin d’accès non détection et dans le GAC :
  * Le programme d’installation a été supprimée la copie dans le GAC.
  * Un fichier .pkgdef a été ajouté pour spécifier une entrée de base de code pour l’assembly.

    Par exemple :
    
    ```xml
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```
    Lors de l’exécution, le sous-système de pkgdef Visual Studio fusionne ces entrées dans le fichier de configuration d’exécution du processus Visual Studio (sous [VSAPPDATA]\devenv.exe.config) en tant que [ `<codeBase>` ](https://msdn.microsoft.com/en-us/library/efs781xb(v=vs.110).aspx) éléments. Il s’agit de la méthode recommandée pour vous permettre du processus Visual Studio de trouver votre assembly, car elle évite d’effectuer une recherche dans les chemins d’accès de détection.

### <a name="reacting-to-this-breaking-change"></a>Réagir à cette modification avec rupture

* Si votre extension est en cours d’exécution dans le processus de Visual Studio :
  * Votre code sera en mesure de trouver les assemblys principaux de Visual Studio.
  * Envisagez d’utiliser un fichier .pkgdef pour spécifier un chemin d’accès à vos assemblys, si nécessaire.
* Si votre extension est en cours d’exécution en dehors du processus Visual Studio :
  * Envisagez de recherche d’assemblys principaux de Visual Studio sous [INSTALLDIR] \Common7\IDE\, [INSTALLDIR] \Common7\IDE\PublicAssemblies ou \Common7\IDE\PrivateAssemblies [INSTALLDIR] à l’aide du résolveur de fichier ou l’assembly de configuration.

## <a name="change-reduce-registry-impact"></a>Modification : Réduire l’impact sur le Registre

### <a name="global-com-registration"></a>Inscription de COM globale

* Auparavant, Visual Studio installé plusieurs clés de Registre dans les ruches HKEY_CLASSES_ROOT et HKEY_LOCAL_MACHINE pour prendre en charge d’inscription COM native. Pour réduire cet impact, Visual Studio utilise désormais [l’Activation sans inscription pour les composants COM](https://msdn.microsoft.com/en-us/library/ms973913.aspx).
* Par conséquent, la plupart des TLB / OLB / fichiers DLL sous % ProgramFiles% (x86) %\Common Files\Microsoft Shared\MSEnv ne sont plus installés par défaut par Visual Studio. Ces fichiers sont maintenant installés sous [INSTALLDIR] avec des manifestes de COM sans inscription correspondants utilisés par le processus hôte de Visual Studio.
* Par conséquent, le code externe qui s’appuie sur l’inscription de COM globale pour les interfaces COM Visual Studio ne trouvera n’est plus de ces enregistrements. Code qui s’exécute à l’intérieur du processus Visual Studio ne verrez pas de différence.

### <a name="visual-studio-registry"></a>Registre de Studio Visual

* Auparavant, Visual Studio installé plusieurs clés de Registre dans la ruche HKEY_LOCAL_MACHINE et HKEY_CURRENT_USER du système sous une clé spécifique de Visual Studio :
  * HKLM\Software\Microsoft\VisualStudio\\**Version**: les clés de Registre créés par les programmes d’installation MSI et extensions de machine.
  * HKCU\Software\Microsoft\VisualStudio\\**Version**: les clés de Registre créés par Visual Studio pour stocker des paramètres spécifiques à l’utilisateur.
  * HKCU\Software\Microsoft\VisualStudio\\**Version**_Config : une copie de la clé de Visual Studio HKLM ci-dessus, ainsi que les clés de Registre fusionnées à partir de fichiers de .pkgdef par les extensions.
* Pour réduire l’impact sur le Registre, Visual Studio utilise désormais la [RegLoadAppKey](https://msdn.microsoft.com/en-us/library/windows/desktop/ms724886(v=vs.85).aspx) (fonction) pour stocker les clés de Registre dans un fichier binaire privé sous [VSAPPDATA]\privateregistry.bin. Uniquement un très petit nombre de clés spécifiques Visual Studio reste dans le Registre système.
* Code existant qui s’exécute au sein du processus Visual Studio n’est pas affecté. Visual Studio effectue une redirection toutes les opérations de Registre sous la clé HKCU Visual Studio spécifiques dans le Registre privé. Lecture et en écriture à d’autres emplacements de Registre continue à utiliser le Registre système.
* Code externe doit charger et lire à partir de ce fichier pour les entrées de Registre de Visual Studio.

### <a name="reacting-to-this-breaking-change"></a>Réagir à cette modification avec rupture

* Le code externe doit être converti pour utiliser l’activation sans inscription pour les composants COM et.
* Composants externes pour trouver l’emplacement de Visual Studio [en suivant les instructions fournies ici](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup).
* Nous recommandons d’utilisent des composants externes les [Gestionnaire de paramètres externe](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.settings.externalsettingsmanager.aspx) au lieu de lecture/écriture directement aux clés de Registre de Visual Studio.
* Vérifiez si les composants à l’aide de votre extension a peut-être implémenté une autre technique pour l’inscription. Par exemple, les extensions de débogueur peuvent être en mesure de tirer parti de la nouvelle [msvsmon d’enregistrement du fichier JSON COM](migrate-debugger-COM-registration.md).
