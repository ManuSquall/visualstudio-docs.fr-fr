---
title: Problèmes connus liés aux conteneurs
description: Découvrez les problèmes connus susceptibles de se produire lorsque vous installez Visual Studio Build Tools dans un conteneur Windows.
ms.date: 02/18/2020
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: 140083f1-05bc-4014-949e-fb5802397c7a
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: a56d820805fa97f3672480c063ebfcc0fdc96fb6
ms.sourcegitcommit: 0499d813d5c24052c970ca15373d556a69507250
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2021
ms.locfileid: "113046090"
---
# <a name="known-issues-for-containers"></a>Problèmes connus liés aux conteneurs

Quelques problèmes nous ont été signalés concernant l’installation de Visual Studio dans un conteneur Docker.

## <a name="windows-container"></a>Conteneur Windows

Les problèmes connus suivants se produisent quand vous installez Visual Studio Build Tools dans un conteneur Windows.

::: moniker range="vs-2017"

* Vous ne pouvez pas installer Visual Studio dans un conteneur basé sur l’image mcr.microsoft.com/windows/servercore :10.0.14393.1593. Les images marquées avec des versions de Windows antérieures ou ultérieures à la version 10.0.14393 doivent normalement fonctionner.

* Vous ne pouvez pas installer le SDK Windows 10.0.14393 ou version ultérieure. Certains packages ne peuvent pas être installés, si bien que les charges de travail qui en dépendent ne peuvent pas fonctionner.

::: moniker-end

* Passez `-m 2GB` (ou plus) au moment de la génération de l’image. L’installation de certaines charges de travail nécessite plus de mémoire que la valeur par défaut (1 Go).
* Configurez Docker pour utiliser des disques ayant une capacité supérieure à la valeur par défaut (20 Go).
* Passez `--norestart` sur la ligne de commande. Au moment de la rédaction de cet article, le redémarrage d’un conteneur Windows au sein même de celui-ci retourne `ERROR_TOO_MANY_OPEN_FILES` à l’hôte.
* Si vous basez votre image directement sur mcr.microsoft.com/windows/servercore, le .NET Framework peut ne pas s’installer correctement et aucune erreur d’installation n’est indiquée. Le code managé risque de ne pas s’exécuter une fois l’installation terminée. Basez plutôt votre image sur [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) ou une version ultérieure. Par exemple, vous pouvez voir une erreur lors de la génération avec MSBuild qui est similaire à ceci :

  > C:\BuildTools\MSBuild\15.0\bin\Roslyn\Microsoft.CSharp.Core.targets(84,5) : erreur MSB6003: Impossible d’exécuter la tâche exécutable spécifiée "csc.exe". Impossible de charger le fichier ou l’assembly 'System.IO.FileSystem, Version=4.0.1.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a', ou l’une de ses dépendances. Le système ne peut pas trouver le fichier spécifié.

::: moniker range="vs-2017"

* Vous ne pouvez pas installer Visual Studio 2017 version 15.8 ou antérieure (n’importe quel produit) sur mcr.microsoft.com/windows/servercore:1809 ou ultérieur. Consultez la rubrique https://aka.ms/setup/containers/servercore1809 (éventuellement en anglais) pour plus d'informations.

::: moniker-end

## <a name="build-tools-container"></a>Conteneur Build Tools

Les problèmes connus suivants peuvent se produire lorsque vous utilisez un conteneur Build Tools. Pour voir si des problèmes ont été résolus ou s’il existe d’autres problèmes connus, consultez la [communauté des développeurs](https://aka.ms/feedback/suggest?space=8).

* L’utilisation d’IntelliTrace au sein d’un conteneur peut ne pas fonctionner dans [certains scénarios](https://github.com/Microsoft/vstest/issues/940).
* Dans les versions antérieures de Docker pour Windows, la taille des images du conteneur par défaut est de seulement 20 Go et n’ajuste pas Build Tools. Suivez [instructions pour modifier la taille des images](/virtualization/windowscontainers/manage-containers/container-storage#storage-limits) à 127 Go ou plus.
Pour confirmer un problème d’espace disque, consultez les fichiers journaux pour plus d’informations. Votre `vslogs\dd_setup_<timestamp>_errors.log` fichier inclut les éléments suivants si l’espace disque est insuffisant : 
```
Pre-check verification: Visual Studio needs at least 91.99 GB of disk space. Try to free up space on C:\ or change your target drive.
Pre-check verification failed with error(s) :  SizePreCheckEvaluator.
```
[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Installer Build Tools dans un conteneur](build-tools-container.md)
* [Exemple avancé pour les conteneurs](advanced-build-tools-container.md)
* [ID de composant et de charge de travail de Visual Studio Build Tools](workload-component-id-vs-build-tools.md)
