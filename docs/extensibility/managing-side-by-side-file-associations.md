---
title: Gestion des associations de fichiers côte à côte | Microsoft Docs
description: Si votre VSPackage fournit des associations de fichiers, décidez comment gérer les installations côte à côte dans lesquelles une version particulière de Visual Studio ouvre un fichier.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- verbs, setting default
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 157e8b4b4d7a00845fb76e0105414879cb1f472d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924859"
---
# <a name="manage-side-by-side-file-associations"></a>Gérer les associations de fichiers côte à côte

Si votre VSPackage fournit des associations de fichiers, vous devez décider comment gérer les installations côte à côte dans lesquelles une version particulière de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] doit être appelée pour ouvrir un fichier. Les formats de fichier incompatibles composent le problème.

Les utilisateurs s’attendent à ce qu’une nouvelle version d’un produit soit compatible avec les versions antérieures, afin que les fichiers existants puissent être chargés dans une nouvelle version sans perdre de données. Dans l’idéal, votre VSPackage peut charger et enregistrer les formats de fichiers des versions antérieures. Si ce n’est pas le cas, vous devez proposer de mettre à niveau le format de fichier vers la nouvelle version de votre VSPackage. L’inconvénient de cette approche est que le fichier mis à niveau ne peut pas être ouvert dans la version antérieure.

Pour éviter ce problème, vous pouvez modifier les extensions lorsque le format de fichier devient incompatible. Par exemple, la version 1 de votre VSPackage peut utiliser l’extension, *. mypkg10*, et la version 2 peut utiliser l’extension, *. mypkg20*. Cette différence identifie le VSPackage qui ouvre un fichier particulier. Si vous ajoutez de nouveaux VSPackages à la liste des programmes associés à une ancienne extension, les utilisateurs peuvent cliquer avec le bouton droit sur le fichier et choisir de l’ouvrir dans un VSPackage plus récent. À ce stade, votre VSPackage peut proposer de mettre à niveau le fichier vers le nouveau format ou d’ouvrir le fichier et de maintenir la compatibilité avec les versions antérieures du VSPackage.

> [!NOTE]
> Vous pouvez combiner ces approches. Par exemple, vous pouvez offrir une compatibilité descendante en chargeant un fichier plus ancien et offrir une mise à niveau du format de fichier lorsque l’utilisateur l’enregistre.

## <a name="face-the-problem"></a>Rencontrez le problème

Si vous souhaitez que plusieurs VSPackages côte à côte utilisent la même extension, vous devez choisir la version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] qui est associée à l’extension. Voici deux alternatives :

- Ouvrez le fichier dans la dernière version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] installée sur l’ordinateur de l’utilisateur.

   Dans cette approche, votre programme d’installation est responsable de la détermination de la version la plus récente de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et de l’inclusion dans l’entrée de Registre écrite pour l’Association de fichiers. Dans un package Windows Installer, vous pouvez inclure des actions personnalisées pour définir une propriété qui indique la dernière version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

  > [!NOTE]
  > Dans ce contexte, « latest » signifie « la dernière version prise en charge ». Ces entrées de programme d’installation ne détectent pas automatiquement une version ultérieure de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Les entrées dans [détecter la configuration système requise](../extensibility/internals/detecting-system-requirements.md) et dans les [commandes qui doivent être exécutées après l’installation](../extensibility/internals/commands-that-must-be-run-after-installation.md) sont similaires à celles présentées ici et sont requises pour prendre en charge des versions supplémentaires de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

   Les lignes suivantes de la table CustomAction définissent la propriété DEVENV_EXE_LATEST comme étant une propriété définie par les tables AppSearch et RegLocator présentées dans les [commandes qui doivent être exécutées après l’installation](../extensibility/internals/commands-that-must-be-run-after-installation.md). Les lignes de la table InstallExecuteSequence planifient les actions personnalisées tôt dans la séquence d’exécution. Les valeurs de la colonne condition rendent la logique de travail :

  - Visual Studio .NET 2002 est la version la plus récente s’il s’agit de la seule version actuelle.

  - Visual Studio .NET 2003 est la version la plus récente uniquement si elle est présente et n' [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] est pas présente.

  - [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] est la dernière version s’il s’agit de la seule version actuelle.

    Le résultat net est que DEVENV_EXE_LATEST contient le chemin d’accès de la dernière version de devenv.exe.

  **Lignes de table CustomAction qui déterminent la dernière version de Visual Studio**

  |Action|Type|Source|Cible|
  |------------|----------|------------|------------|
  |CA_SetDevenvLatest_2002|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2002]|
  |CA_SetDevenvLatest_2003|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2003]|
  |CA_SetDevenvLatest_2005|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2005]|

  **Lignes de la table InstallExecuteSequence qui déterminent la dernière version de Visual Studio**

  |Action|Condition|Séquence|
  |------------|---------------|--------------|
  |CA_SetDevenvLatest_2002|DEVENV_EXE_2002 ET NON (DEVENV_EXE_2003 OU DEVENV_EXE_2005)|410|
  |CA_SetDevenvLatest_2003|DEVENV_EXE_2003 ET NON DEVENV_EXE_2005|420|
  |CA_SetDevenvLatest_2005|DEVENV_EXE_2005|430|

   Vous pouvez utiliser la propriété DEVENV_EXE_LATEST dans la table de Registre du package Windows Installer pour écrire la valeur par défaut de HKEY_CLASSES_ROOT la clé **ShellOpenCommand *ProgID*** , [DEVENV_EXE_LATEST] "%1"

- Exécutez un programme de lancement partagé qui peut faire le meilleur choix parmi les versions de VSPackage disponibles.

   Les développeurs de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] choisissent cette approche pour gérer les exigences complexes des différents formats des solutions et des projets qui résultent de nombreuses versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Dans cette approche, vous inscrivez un programme de lancement en tant que gestionnaire d’extensions. Le lanceur examine le fichier et décide quelle version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et votre VSPackage peuvent gérer ce fichier particulier. Par exemple, si un utilisateur ouvre un fichier qui a été enregistré pour la dernière fois par une version particulière de votre VSPackage, le lanceur peut démarrer ce VSPackage dans la version correspondante de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . En outre, un utilisateur peut configurer le lanceur pour toujours démarrer la dernière version. Un lanceur peut également inviter un utilisateur à mettre à niveau le format du fichier. Si le format du fichier contient un numéro de version, le lanceur peut informer un utilisateur si le format de fichier provient d’une version ultérieure à l’un ou plusieurs des VSPackages installés.

   Le lanceur doit se trouver dans un composant Windows Installer partagé avec toutes les versions de votre VSPackage. Ce processus permet de s’assurer que la version la plus récente est toujours installée et n’est pas supprimée tant que toutes les versions de votre VSPackage n’ont pas été désinstallées. Ainsi, les associations de fichiers et autres entrées de Registre du composant lanceur sont conservées même si une version du VSPackage est désinstallée.

## <a name="uninstall-and-file-associations"></a>Désinstallation et associations de fichiers

La désinstallation d’un VSPackage qui écrit des entrées de Registre pour les associations de fichiers supprime les associations de fichiers. Par conséquent, l’extension n’a pas de programmes associés. Windows Installer ne récupère pas les entrées de Registre qui ont été ajoutées lors de l’installation du VSPackage. Voici quelques méthodes pour corriger les associations de fichiers d’un utilisateur :

- Utilisez un composant lanceur partagé comme décrit précédemment.

- Demandez à l’utilisateur d’exécuter une réparation de la version du VSPackage dont l’utilisateur souhaite posséder l’Association de fichiers.

- Fournissez un programme exécutable distinct qui réécrit les entrées de Registre appropriées.

- Fournissez une page d’options de configuration ou une boîte de dialogue qui permet aux utilisateurs de choisir des associations de fichiers et de récupérer des associations perdues. Demandez aux utilisateurs de l’exécuter après la désinstallation.

## <a name="see-also"></a>Voir aussi

- [Inscrire des extensions de nom de fichier pour les déploiements côte à côte](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Verbes Register pour les extensions de nom de fichier](../extensibility/registering-verbs-for-file-name-extensions.md)
