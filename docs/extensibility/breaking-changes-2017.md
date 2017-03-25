---
title: "Modifications avec rupture dans Visual Studio 2017 extensibilité | Documents Microsoft"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
caps.latest.revision: 1
author: gregvanl
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 2e6e4b3d9d1528d57fe181b3765e1ce3624bebad
ms.lasthandoff: 03/07/2017

---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Modifications apportées à l’extensibilité de Visual Studio 2017

Avec Visual Studio 2017, nous offrons une [une expérience d’installation Visual Studio plus rapide, légère](https://blogs.msdn.microsoft.com/visualstudio/2016/04/01/faster-leaner-visual-studio-installer) afin de réduire l’impact de Visual Studio sur les systèmes de l’utilisateur, tout en donnant aux utilisateurs un choix supérieur sur les charges de travail et les fonctionnalités qui sont installées. Pour prendre en charge ces améliorations, nous avez apporté des modifications au modèle d’extensibilité et apportées des modifications avec rupture à l’extensibilité de Visual Studio. Ce document décrit les détails techniques de ces modifications, et ce qui peut être fait pour les résoudre. Veuillez noter que certaines informations sont de détails d’implémentation de point-à-temps et peuvent être modifiées ultérieurement.

## <a name="changes-affecting-vsix-format-and-installation"></a>Modifications qui affectent le Format VSIX et Installation

Nous avons créé le VSIX v3 format (version 3) pour prendre en charge l’expérience d’installation de légers.

Modifications du format VSIX sont les suivantes :

* Déclaration des conditions préalables d’installation. Pour la distribution sur la promesse d’un léger et rapide à l’installation de Visual Studio, le programme d’installation propose maintenant plusieurs options de configuration pour les utilisateurs. Par conséquent, pour vous assurer que les fonctionnalités et les composants requis par une extension sont installés, les extensions devez déclarer leurs dépendances.
  * Le programme d’installation de Visual Studio 2017 propose automatiquement acquérir et installer les composants nécessaires pour l’utilisateur dans le cadre de l’installation de votre extension.
  * Les utilisateurs sont avertis également lorsque vous tentez d’installer une extension qui n’a pas créée le nouveau format VSIX v3, même s’ils ont été marqués dans leur manifeste en ciblant la version 15.0.
* Capacités améliorées pour le format VSIX. Fournir un [faible impact installation](https://blogs.msdn.microsoft.com/visualstudio/2016/04/25/anatomy-of-a-low-impact-visual-studio-install) de Visual Studio qui prend également en charge l’installation côte à côte, nous ne peut plus enregistrer les données de configuration dans le Registre système et ont été déplacés hors du GAC, les assemblys spécifiques à Visual Studio. Nous avons également augmenté les fonctionnalités du format VSIX et moteur d’installation VSIX, ce qui vous permet d’utiliser plutôt que des EXE ou un MSI pour installer vos extensions pour certains types d’installation.

  Les nouvelles fonctionnalités sont les suivantes :

  * Inscription dans l’instance spécifiée de Visual Studio.
  * Installation en dehors de la [dossier extensions](set-install-root.md).
  * Détection de l’architecture processeur.
  * Vis-à-vis des modules linguistiques séparées par langue.
  * Installation avec [prise en charge NGEN](ngen-support.md).

## <a name="building-an-extension-for-visual-studio-2017"></a>Création d’une extension pour Visual Studio 2017

Concepteur d’outils pour la création de nouveau le format de manifeste VSIX v3 est désormais disponible dans Visual Studio 2017. Consultez le document [Comment : migrer les projets d’extensibilité pour Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) pour plus d’informations à l’aide des outils du concepteur ou de mise à jour manuelle du projet et le manifeste pour développer les extensions VSIX v3.

## <a name="change-visual-studio-user-data-path"></a>Modification : Chemin d’accès des données utilisateur Visual Studio

Auparavant, une seule installation de chaque version majeure de Visual Studio peut exister sur chaque ordinateur. Pour prendre en charge les installations côte à côte de Visual Studio 2017, plusieurs chemins de données utilisateur pour Visual Studio peuvent exister sur l’ordinateur de l’utilisateur.

Code qui s’exécute dans le processus Visual Studio doit-elle être mis à jour pour utiliser le Gestionnaire de paramètres Visual Studio. Code qui s’exécute en dehors du processus Visual Studio peut trouver le chemin d’accès de l’utilisateur d’une installation de Visual Studio spécifique [en suivant les instructions ici](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup).

## <a name="change-global-assembly-cache-gac"></a>Modification : Global Assembly Cache (GAC)

La plupart des assemblys principaux de Visual Studio ne sont plus installés dans le GAC. Les modifications suivantes ont été apportées afin que le code exécuté dans le processus de Visual Studio trouve toujours les assemblys requis lors de l’exécution.

* Assemblys qui ont été installés uniquement dans le GAC :
  * Ces assemblys sont désormais installées sous %VsFolder%\Common7\IDE\, %VsFolder%\Common7\IDE\PublicAssemblies ou % VsFolder%\Common7\IDE\PrivateAssemblies. Ces dossiers font partie des chemins de détection du processus Visual Studio.
* Assemblys qui ont été installés dans un chemin d’accès non détection et dans le GAC :
  * Le programme d’installation a été supprimée la copie dans le GAC.
  * Un fichier .pkgdef a été ajouté pour spécifier une entrée de base de code pour l’assembly.

    Exemple :
    
    ```xml
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```
    Lors de l’exécution, le sous-système de pkgdef Visual Studio fusionne ces entrées dans le fichier de configuration d’exécution du processus Visual Studio (sous % VsAppDataFolder%\devenv.exe.config) en tant que [ `<codeBase>` ](https://msdn.microsoft.com/en-us/library/efs781xb(v=vs.110).aspx) éléments. Il est recommandé de laisser le processus de Visual Studio de trouver votre assembly, car elle évite d’effectuer une recherche dans la détection des chemins d’accès.

### <a name="reacting-to-this-breaking-change"></a>Réagir à cette modification avec rupture

* Si votre extension s’exécute dans le processus de Visual Studio :
  * Votre code sera en mesure de trouver les assemblys principaux de Visual Studio.
  * Envisagez d’utiliser un fichier .pkgdef pour spécifier un chemin d’accès à vos assemblys, si nécessaire.
* Si votre extension s’exécute en dehors du processus Visual Studio :
  * Envisagez la recherche d’assemblys principaux de Visual Studio sous %VsFolder%\Common7\IDE\, %VsFolder%\Common7\IDE\PublicAssemblies ou %VsFolder%\Common7\IDE\PrivateAssemblies à l’aide du résolveur d’assembly ou de fichier de configuration.

## <a name="change-reduce-registry-impact"></a>Modification : Réduire l’impact sur le Registre

### <a name="global-com-registration"></a>Inscription COM globale

* Auparavant, Visual Studio installé plusieurs clés de Registre dans les ruches HKEY_CLASSES_ROOT et HKEY_LOCAL_MACHINE pour prendre en charge l’inscription COM native. Pour éviter cet impact, Visual Studio utilise désormais [l’Activation sans inscription pour les composants COM](https://msdn.microsoft.com/en-us/library/ms973913.aspx).
* Par conséquent, la plupart des TLB / OLB / fichiers DLL sous % ProgramFiles% (x86) %\Common Files\Microsoft Shared\MSEnv ne sont plus installés par défaut par Visual Studio. Ces fichiers sont désormais installées sous % VsFolder % avec des manifestes de COM sans inscription correspondantes utilisées par le processus hôte de Visual Studio.
* Par conséquent, le code externe qui s’appuie sur l’inscription COM globale pour les interfaces COM Visual Studio sera ne trouve plus ces enregistrements. Code qui s’exécute dans le processus de Visual Studio ne voient pas de différence.

### <a name="visual-studio-registry"></a>Registre de Studio Visual

* Auparavant, Visual Studio installé plusieurs clés de Registre dans les ruches HKEY_LOCAL_MACHINE et HKEY_CURRENT_USER du système sous une clé spécifique de Visual Studio :
  * HKLM\Software\Microsoft\VisualStudio\\**Version**: les clés de Registre créées par des programmes d’installation MSI et extensions de machine.
  * HKCU\Software\Microsoft\VisualStudio\\**Version**: les clés de Registre créés par Visual Studio pour stocker des paramètres spécifiques à l’utilisateur.
  * HKCU\Software\Microsoft\VisualStudio\\**Version**_Config : une copie de la clé de Visual Studio HKLM ci-dessus, ainsi que les clés de Registre fusionnées à partir de fichiers de .pkgdef par les extensions.
* Pour réduire l’impact sur le Registre, Visual Studio utilise désormais le [RegLoadAppKey](https://msdn.microsoft.com/en-us/library/windows/desktop/ms724886(v=vs.85).aspx) (fonction) pour stocker les clés de Registre dans un fichier binaire privé sous % VsAppDataFolder%\privateregistry.bin. Seulement un très petit nombre de clés spécifiques Visual Studio reste dans le Registre système.
* Code existant en cours d’exécution dans le processus de Visual Studio n’est pas affecté. Visual Studio redirige toutes les opérations de Registre sous la clé HKCU Visual Studio spécifiques dans le Registre privé. Lire et écrire à d’autres emplacements de Registre continuera d’utiliser le Registre système.
* Code externe doit charger et lire à partir de ce fichier pour les entrées de Registre Visual Studio.

### <a name="reacting-to-this-breaking-change"></a>Réagir à cette modification avec rupture

* Le code externe doit être converti pour utiliser l’activation sans inscription pour les composants COM et.
* Composants externes pour trouver l’emplacement de Visual Studio [en suivant les instructions ici](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup).
* Nous recommandons d’utilisent des composants externes les [externe Settings Manager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.settings.externalsettingsmanager.aspx) au lieu de lire/écrire directement dans les clés de Registre Visual Studio.
* Vérifiez si les composants à l’aide de votre extension a peut-être implémenté une autre technique pour l’inscription. Par exemple, les extensions de débogueur peuvent être en mesure de tirer parti de la nouvelle [msvsmon d’enregistrement de fichier JSON COM](migrate-debugger-COM-registration.md).

## <a name="change-lightweight-solution-load"></a>Modification : Charge de Solution légère

Charger Solution légère (LSL) réduit le temps de charge Solution en chargeant pas entièrement projets jusqu'à ce que l’utilisateur commence à fonctionner avec eux. Cela peut avoir un impact extensions qui supposent qu'un projet est complètement chargé. Consultez la page [Lightweight Solution charge](lightweight-solution-load-extension-impact.md) pour savoir si votre extension peuvent être réduites et obtenez des conseils sur la mise à jour de votre extension.

