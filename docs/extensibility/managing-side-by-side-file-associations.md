---
title: La gestion des Associations de fichiers de côte à côte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- verbs, setting default
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f6cd0ac349d332f7e07d4f0ce6e5567cb5deb63c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62907251"
---
# <a name="manage-side-by-side-file-associations"></a>Gérer les associations de fichiers de côte à côte

Si votre VSPackage fournit des associations de fichiers, vous devez décider comment gérer les installations côte à côte dans lequel une version particulière de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] doit être appelé pour ouvrir un fichier. Formats de fichier incompatibles composée le problème.

Les utilisateurs attendent une nouvelle version d’un produit pour être compatible avec les versions antérieures, afin que les fichiers existants peuvent être chargées dans une nouvelle version sans perte de données. Dans l’idéal, votre VSPackage peut charger et enregistrer les formats de fichier des versions antérieures. Si tel n’est pas vrai, vous pouvez proposer mettre à niveau le format de fichier vers la nouvelle version de votre VSPackage. L’inconvénient de cette approche est que le fichier mis à niveau ne peut pas être ouvert dans une version antérieure.

Pour éviter ce problème, vous pouvez modifier des extensions lorsque les formats de fichier sont incompatibles. Par exemple, la version 1 de votre VSPackage peut utiliser l’extension, *.mypkg10*et la version 2 peut utiliser l’extension, *.mypkg20*. Cette différence identifie le VSPackage qui ouvre un fichier particulier. Si vous ajoutez des VSPackages plus récente à la liste des programmes qui sont associés à une ancienne extension, les utilisateurs peuvent cliquez sur le fichier et ouvrez-la dans un VSPackage plus récente. À ce stade, votre VSPackage peut offrir à mettre à niveau le fichier vers le nouveau format ou ouvrez le fichier et maintenir la compatibilité avec les versions antérieures du VSPackage.

> [!NOTE]
> Vous pouvez combiner ces approches. Par exemple, vous pouvez offrir une compatibilité descendante en chargeant un fichier plus ancien et offre mettre à niveau le format de fichier lorsque l’utilisateur enregistre.

## <a name="face-the-problem"></a>Confronté au problème

Si vous souhaitez que plusieurs VSPackages côte à côte pour utiliser la même extension, vous devez choisir la version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] qui est associé à l’extension. Voici deux alternatives :

- Ouvrez le fichier dans la dernière version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] installé sur l’ordinateur d’un utilisateur.

   Dans cette approche, votre programme d’installation est chargé de déterminer la dernière version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et y compris celui de l’entrée de Registre écrite pour l’association de fichiers. Dans un package de programme d’installation de Windows, vous pouvez inclure des actions personnalisées pour définir une propriété qui indique la dernière version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

  > [!NOTE]
  > Dans ce contexte, « dernier » signifie « version la plus récente. » Ces entrées du programme d’installation ne détecte pas automatiquement une version ultérieure de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Entrées dans [requise de détection](../extensibility/internals/detecting-system-requirements.md) et dans [commandes que doit être exécuté après l’Installation](../extensibility/internals/commands-that-must-be-run-after-installation.md) sont similaires à ceux présentés ici et sont requises pour prendre en charge des versions supplémentaires de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

   Les lignes suivantes dans la table CustomAction définir la propriété DEVENV_EXE_LATEST soit une propriété définie par le AppSearch et RegLocator tables présentées dans [commandes qui doivent être exécutées après l’installation](../extensibility/internals/commands-that-must-be-run-after-installation.md). Lignes de la table InstallExecuteSequence planifier les actions personnalisées au début de la séquence d’exécution. Valeurs de la marque de colonne Condition la logique de travail :

  - Visual Studio .NET 2002 est la dernière version, s’il s’agit de la version actuelle uniquement.

  - Visual Studio .NET 2003 est la dernière version uniquement s’il est présent et [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] n’est pas présent.

  - [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] est la dernière version, s’il s’agit de la version actuelle uniquement.

    Le résultat net est que DEVENV_EXE_LATEST contient le chemin d’accès de la dernière version de devenv.exe.

  **Lignes de la table CustomAction qui déterminent la dernière version de Visual Studio**

  |Action|Type|Source|une cible|
  |------------|----------|------------|------------|
  |CA_SetDevenvLatest_2002|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2002]|
  |CA_SetDevenvLatest_2003|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2003]|
  |CA_SetDevenvLatest_2005|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2005]|

  **Lignes de la table InstallExecuteSequence qui déterminent la dernière version de Visual Studio**

  |Action|Condition|Séquence|
  |------------|---------------|--------------|
  |CA_SetDevenvLatest_2002|DEVENV_EXE_2002 ET NON (DEVENV_EXE_2003 OU DEVENV_EXE_2005)|410|
  |CA_SetDevenvLatest_2003|DEVENV_EXE_2003 ET PAS DEVENV_EXE_2005|420|
  |CA_SetDevenvLatest_2005|DEVENV_EXE_2005|430|

   Vous pouvez utiliser la propriété DEVENV_EXE_LATEST dans la table de Registre du package Windows Installer pour écrire la **HKEY_CLASSES_ROOT*ProgId*ShellOpenCommand** valeur par défaut de la clé [DEVENV_EXE_LATEST] « %1 »

- Exécuter un programme de lanceur partagées qui peut rendre le meilleur choix à partir de versions VSPackage disponibles.

   Les développeurs de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] choisi cette approche pour gérer les exigences complexes des plusieurs formats de solutions et projets qui résultent de nombreuses versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Dans cette approche, vous inscrivez un programme de lancement en tant que le Gestionnaire d’extensions. Le Lanceur examine le fichier et détermine la version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et votre VSPackage peut gérer ce fichier particulier. Par exemple, si un utilisateur ouvre un fichier qui a été enregistré dans une version particulière de votre VSPackage, le lanceur peut démarrer ce VSPackage dans la version correspondante des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. En outre, un utilisateur peut configurer le Lanceur pour toujours démarrer la version la plus récente. Un lanceur peut également inviter un utilisateur à mettre à niveau le format du fichier. Si le format du fichier inclut un numéro de version, le Lanceur d’informer un utilisateur si le format de fichier provient d’une version ultérieure à une ou plusieurs du VSPackage installés.

   Le service de lancement doit être dans un composant de programme d’installation de Windows qui est partagé avec toutes les versions de votre VSPackage. Ce processus permet de s’assurer que la version la plus récente est toujours installée et qu’il n’est pas supprimée tant que toutes les versions de votre VSPackage sont désinstallées. De cette façon, les associations de fichiers et d’autres entrées de Registre du composant Lanceur sont conservées même si une version du VSPackage est désinstallée.

## <a name="uninstall-and-file-associations"></a>Désinstaller et les associations de fichiers

Désinstallation d’un VSPackage qui écrit des entrées de Registre pour les associations de fichiers supprime les associations de fichiers. Par conséquent, l’extension ne possède aucun programmes associés. Programme d’installation de Windows ne pas « recover » les entrées de Registre qui ont été ajoutées lors de l’installation de VSPackage. Voici quelques méthodes permettant de corriger les associations de fichiers d’un utilisateur :

- Utiliser un composant Lanceur partagé comme décrit précédemment.

- Demandez à l’utilisateur d’exécuter une réparation de la version du VSPackage que l’utilisateur veut être propriétaire de l’association de fichiers.

- Fournir un programme exécutable qui réécrit les entrées de Registre appropriées.

- Fournir une configuration options page ou boîte de dialogue qui permet aux utilisateurs de choisir les associations de fichiers et de récupérer des associations perdues. Demandez aux utilisateurs de s’exécuter après la désinstallation.

## <a name="see-also"></a>Voir aussi

- [Inscrire des extensions de nom de fichier pour les déploiements côte à côte](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Inscrire des verbes pour les extensions de nom de fichier](../extensibility/registering-verbs-for-file-name-extensions.md)