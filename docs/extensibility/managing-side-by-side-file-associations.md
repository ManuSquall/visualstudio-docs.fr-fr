---
title: Gestion des associations de fichiers côte à côte (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- verbs, setting default
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c284fe7ef4c2d07051a8524860583cb634e13bf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702761"
---
# <a name="manage-side-by-side-file-associations"></a>Gérer les associations de fichiers côte à côte

Si votre VSPackage fournit des associations de fichiers, vous devez décider comment [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gérer les installations côte à côte dans lesquelles une version particulière doit être invoquée pour ouvrir un fichier. Les formats de fichiers incompatibles aggravent le problème.

Les utilisateurs s’attendent à ce qu’une nouvelle version d’un produit soit compatible avec les versions antérieures, de sorte que les fichiers existants peuvent être chargés dans une nouvelle version sans perdre de données. Idéalement, votre VSPackage peut à la fois charger et enregistrer les formats de fichiers des versions antérieures. Si ce n’est pas vrai, vous devriez offrir de mettre à niveau le format de fichier à la nouvelle version de votre VSPackage. L’inconvénient de cette approche est que le fichier mis à niveau ne peut pas être ouvert dans la version antérieure.

Pour éviter ce problème, vous pouvez modifier les extensions lorsque les formats de fichiers deviennent incompatibles. Par exemple, la version 1 de votre VSPackage pourrait utiliser l’extension, *.mypkg10*, et la version 2 pourrait utiliser l’extension, *.mypkg20*. Cette différence identifie le VSPackage qui ouvre un fichier particulier. Si vous ajoutez de nouveaux VSPackages à la liste des programmes qui sont associés à une ancienne extension, les utilisateurs peuvent cliquer directement sur le fichier et choisir de l’ouvrir dans un VSPackage plus récent. À ce stade, votre VSPackage peut vous proposer de mettre à niveau le fichier vers le nouveau format ou d’ouvrir le fichier et de maintenir la compatibilité avec les versions antérieures du VSPackage.

> [!NOTE]
> Vous pouvez combiner ces approches. Par exemple, vous pouvez offrir une compatibilité rétrograde en chargeant un fichier plus ancien et proposer de mettre à niveau le format de fichier lorsque l’utilisateur l’enregistre.

## <a name="face-the-problem"></a>Faire face au problème

Si vous souhaitez que plusieurs VSPackages côte à côte utilisent la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] même extension, vous devez choisir la version de cette version associée à l’extension. Voici deux alternatives :

- Ouvrez le fichier dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] la dernière version de l’installation sur l’ordinateur d’un utilisateur.

   Dans cette approche, votre installateur est [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] responsable de déterminer la dernière version de et d’inclure celle dans l’entrée du registre écrite pour l’association de fichiers. Dans un package d’installateur Windows, vous pouvez inclure des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]actions personnalisées pour définir une propriété qui indique la dernière version de .

  > [!NOTE]
  > Dans ce contexte, "dernier" signifie "dernière version prise en charge". Ces entrées d’installateur ne [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]détecteront pas automatiquement une version ultérieure de . Les inscriptions dans [Les exigences du système de détection](../extensibility/internals/detecting-system-requirements.md) et dans les commandes qui doivent être [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [exécutées après l’installation](../extensibility/internals/commands-that-must-be-run-after-installation.md) sont similaires à celles présentées ici et sont nécessaires pour prendre en charge des versions supplémentaires de .

   Les rangées suivantes dans la table CustomAction définir la propriété DEVENV_EXE_LATEST d’être une propriété définie par les tables AppSearch et RegLocator discutés dans [les commandements qui doivent être exécutés après l’installation](../extensibility/internals/commands-that-must-be-run-after-installation.md). Les lignes dans le tableau InstallExecuteSequence planifient les actions personnalisées au début de la séquence d’exécution. Les valeurs de la colonne Condition font fonctionner la logique :

  - Visual Studio .NET 2002 est la dernière version si elle est la seule version actuelle.

  - Visual Studio .NET 2003 est la dernière [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] version seulement si elle est présente et n’est pas présente.

  - [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]est la dernière version si c’est la seule version actuelle.

    Le résultat net est que DEVENV_EXE_LATEST contient le chemin de la dernière version de devenv.exe.

  **Lignes de table CustomAction qui déterminent la dernière version de Visual Studio**

  |Action|Type|Source|Cible|
  |------------|----------|------------|------------|
  |CA_SetDevenvLatest_2002|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2002]|
  |CA_SetDevenvLatest_2003|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2003]|
  |CA_SetDevenvLatest_2005|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2005]|

  **InstallezExecuteSequence lignes de table qui déterminent la dernière version de Visual Studio**

  |Action|Condition|Séquence|
  |------------|---------------|--------------|
  |CA_SetDevenvLatest_2002|DEVENV_EXE_2002 ET NON (DEVENV_EXE_2003 OU DEVENV_EXE_2005)|410|
  |CA_SetDevenvLatest_2003|DEVENV_EXE_2003 ET NON DEVENV_EXE_2005|420|
  |CA_SetDevenvLatest_2005|DEVENV_EXE_2005|430|

   Vous pouvez utiliser la propriété DEVENV_EXE_LATEST dans le tableau d’enregistrement du paquet d’installateur Windows pour écrire la valeur par défaut de la clé **ProgId ShellOpenCommand HKEY_CLASSES_ROOT*ProgId,*** [DEVENV_EXE_LATEST] « %1 »

- Exécutez un programme de lanceur partagé qui peut faire le meilleur choix à partir des versions VSPackage disponibles.

   Les développeurs [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] de cette approche ont choisi de répondre aux exigences complexes des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]multiples formats de solutions et de projets qui résultent de nombreuses versions de . Dans cette approche, vous enregistrez un programme de lanceur en tant que gestionnaire d’extension. Le lanceur examine le fichier et [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] décide quelle version et votre VSPackage peuvent gérer ce fichier particulier. Par exemple, si un utilisateur ouvre un fichier qui a été enregistré pour la dernière fois par une [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]version particulière de votre VSPackage, le lanceur peut démarrer ce VSPackage dans la version correspondante de . En outre, un utilisateur peut configurer le lanceur pour toujours démarrer la dernière version. Un lanceur pourrait également inciter un utilisateur à mettre à niveau le format du fichier. Si le format du fichier inclut un numéro de version, le lanceur peut informer un utilisateur si le format du fichier provient d’une version postérieure à une ou plusieurs des VSPackages installés.

   Le lanceur doit être dans un composant d’installateur Windows qui est partagé avec toutes les versions de votre VSPackage. Ce processus permet de s’assurer que la dernière version est toujours installée et n’est pas supprimée jusqu’à ce que toutes les versions de votre VSPackage ne soient pas bloquées. De cette façon, les associations de fichiers et autres entrées de registre du composant lanceur sont conservés même si une version du VSPackage n’est pas bloquée.

## <a name="uninstall-and-file-associations"></a>Désinstaller et classer les associations

Le désinstallation d’un VSPackage qui écrit des inscriptions de registre pour les associations de fichiers supprime les associations de fichiers. Par conséquent, la prolongation n’a pas de programmes associés. Windows Install ne "récupère" pas les entrées de registre qui ont été ajoutées lors de l’installation du VSPackage. Voici quelques façons de corriger les associations de fichiers d’un utilisateur :

- Utilisez un composant de lanceur partagé tel qu’il a été décrit précédemment.

- Demandez à l’utilisateur d’exécuter une réparation de la version de la VSPackage que l’utilisateur veut posséder l’association de fichiers.

- Fournir un programme exécutable distinct qui réécrit les inscriptions appropriées au registre.

- Fournir une page d’options de configuration ou une boîte de dialogue qui permet aux utilisateurs de choisir des associations de fichiers et de récupérer les associations perdues. Demandez aux utilisateurs de l’exécuter après la non-réinstallation.

## <a name="see-also"></a>Voir aussi

- [Enregistrer les extensions de noms de fichiers pour les déploiements côte à côte](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Enregistrer les verbes pour les extensions de nom de fichier](../extensibility/registering-verbs-for-file-name-extensions.md)
