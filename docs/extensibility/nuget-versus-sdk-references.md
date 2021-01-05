---
title: Ajout de références avec NuGet ou un kit SDK d’extension
description: Découvrez les différences entre le Packaging logiciel en tant que package NuGet ou un kit de développement logiciel (SDK) lorsqu’il est référencé dans un projet Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 08/02/2019
ms.topic: conceptual
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 50197eeda1828156113fbbfa507447484618861a
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863778"
---
# <a name="nuget-versus-sdk-as-a-project-reference"></a>NuGet et kit de développement logiciel (SDK) comme référence de projet

Cet article est conçu pour aider les développeurs à choisir s’il faut empaqueter leurs logiciels sous la forme d’un package NuGet ou en tant que Kit de développement logiciel (SDK). Plus précisément, il décrit les différences entre les deux lorsqu’ils sont référencés dans un projet Visual Studio.

- [NuGet](/nuget) est un système de gestion de package open source qui simplifie le processus d’intégration de bibliothèques dans un projet. Pour .NET (y compris .NET Core), NuGet est le mécanisme pris en charge par Microsoft pour le partage de code. NuGet définit la manière dont les packages pour .NET sont créés, hébergés et consommés, et fournit les outils pour chacun de ces rôles. Dans Visual Studio, vous ajoutez des packages NuGet à un projet à l’aide de l’interface utilisateur du [Gestionnaire de package](/nuget/consume-packages/install-use-packages-visual-studio) .

- Un [Kit de développement logiciel (SDK)](../extensibility/creating-a-software-development-kit.md) est une collection de fichiers que Visual Studio traite comme un élément de référence unique. La boîte de dialogue Gestionnaire de références de Visual Studio répertorie tous les kits de développement logiciel (SDK) pertinents pour le projet actif lorsque vous choisissez **Ajouter une référence**. Lorsque vous ajoutez un kit de développement logiciel (SDK) à un projet, vous pouvez accéder à tout le contenu du kit de développement logiciel (SDK) via IntelliSense, la fenêtre boîte à outils, les concepteurs, l’Explorateur d’objets, MSBuild, le déploiement, le débogage et l’empaquetage.

## <a name="which-mechanism-should-i-use"></a>Quel mécanisme dois-je utiliser ?

Le tableau suivant vous permet de comparer les fonctionnalités de référencement d’un SDK avec celles de NuGet.

| Fonctionnalité | Prise en charge par le SDK | Notes concernant le SDK | Prise en charge par NuGet | Notes concernant NuGet |
| - | - | - |---------------| - |
| Le mécanisme référence une entité, et ensuite tous les fichiers et les fonctionnalités sont disponibles. | Y | Vous ajoutez un kit SDK à l’aide de la boîte de dialogue **Gestionnaire de références** et tous les fichiers et les fonctionnalités sont disponibles pendant le flux de travail de développement. | Y | |
| MSBuild consomme automatiquement les assemblys et les fichiers de métadonnées Windows (*. winmd*). | Y | Les références dans le kit SDK sont automatiquement passées au compilateur. | Y | |
| MSBuild consomme automatiquement les fichiers .h ou .lib. | Y | Le fichier *SDKName. props* indique à Visual Studio comment configurer le répertoire Visual C++, etc., pour la consommation automatique du fichier. *h* ou *. lib* . | N | |
| MSBuild consomme automatiquement les fichiers  *. js* ou *. CSS* . | Y | Dans **Explorateur de solutions**, vous pouvez développer le nœud de référence du kit de développement logiciel (SDK) JavaScript pour afficher des fichiers. *js* ou *. CSS* individuels, puis générer des `<source include/>` balises en faisant glisser ces fichiers vers leurs fichiers sources. Le kit SDK prend en charge F5 et l’installation automatique des packages. | Y | |
| MSBuild ajoute automatiquement le contrôle à la **Boîte à outils**. | Y | La **Boîte à outils** peut consommer des kits SDK et afficher des contrôles dans les onglets que vous spécifiez. | N | |
| Le mécanisme prend en charge le programme d’installation de Visual Studio pour les extensions (VSIX). | Y | VSIX a un manifeste et une logique spéciaux pour créer des packages du SDK. | Y | L’extension VSIX peut être incorporée dans un autre programme d’installation. |
| L’**Explorateur d’objets** énumère les références. | Y | L’**Explorateur d’objets** obtient automatiquement la liste des références dans les kits SDK et les énumère. | N | |
| Les fichiers et les liens sont automatiquement ajoutés à la boîte de dialogue **Gestionnaire de références** (les liens d’aide et autres sont remplis automatiquement). | Y | La boîte de dialogue **Gestionnaire de références** énumère automatiquement les kits SDK, ainsi que les liens d’aide et la liste des dépendances aux kits SDK. | N | NuGet fournit sa propre boîte de dialogue **Gérer les packages NuGet**. |
| Le mécanisme prend en charge plusieurs architectures. | Y | Les kits SDK peuvent fournir plusieurs configurations. MSBuild consomme les fichiers appropriés pour chaque configuration de projet. | N | |
| Le mécanisme prend en charge plusieurs configurations. | Y | Les kits SDK peuvent fournir plusieurs configurations. En fonction de l’architecture du projet, MSBuild consomme les fichiers appropriés pour chaque architecture de projet. | N | |
| Le mécanisme peut spécifier de « ne pas copier ». | Y | Selon que les fichiers sont déposés dans le dossier *\Redist* ou *\designtime* , vous pouvez contrôler les fichiers à copier dans le package de l’application consommatrice. | N | Vous déclarez les fichiers à copier dans le manifeste du package. |
| Le contenu apparaît dans les fichiers localisés. | Y | Les documents XML localisés dans les kits SDK sont automatiquement ajoutés, pour une meilleure expérience de conception. | N | |
| MSBuild prend en charge la consommation simultanée de plusieurs versions d’un kit SDK. | Y | Le kit SDK prend en charge la consommation simultanée de plusieurs versions. | N | Cela ne constitue pas une référence. Vous ne pouvez pas avoir plusieurs versions de fichiers NuGet dans votre projet en même temps. |
| Le mécanisme prend en charge la spécification de frameworks cibles, de versions de Visual Studio et de types de projets applicables. | Y | La boîte de dialogue **Gestionnaire de références** et la **Boîte à outils** affichent uniquement les kits SDK qui s’appliquent à un projet. Ainsi, il est plus facile aux utilisateurs de choisir ceux qui leur conviennent. | O (en partie) | Pivot est le framework cible. Il n’existe aucun filtrage sur l’interface utilisateur. Au moment de l’installation, une erreur peut être retournée. |
| Le mécanisme prend en charge la spécification d’informations d’inscription pour les WinMD natifs. | Y | Vous pouvez spécifier la corrélation entre le fichier. winmd et le fichier. dll dans *SDKManifest.xml*. | N | |
| Le mécanisme prend en charge la spécification de dépendances envers d’autres kits SDK. | Y | Le kit SDK notifie simplement l’utilisateur. Celui-ci doit toujours les installer et les référencer manuellement. | Y | NuGet les extrait automatiquement ; l’utilisateur n’est pas averti. |
| Le mécanisme s’intègre à des concepts [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] tels que le manifeste d’application et l’ID de framework. | Y | Le kit SDK doit passer les concepts propres au [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] pour que l’empaquetage et F5 fonctionnent correctement avec les kits SDK qui sont disponibles dans le [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]. | N | |
| Le mécanisme s’intègre au pipeline de débogage d’application pour les applications [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]. | Y | Le kit SDK doit passer les concepts propres au [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] pour que l’empaquetage et F5 fonctionnent correctement avec les kits SDK disponibles dans le [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]. | Y | Le contenu NuGet devient partie intégrante du projet. Aucune attention particulière n’est nécessaire pour F5. |
| Le mécanisme s’intègre aux manifestes d’application. | Y | Le kit SDK doit passer les concepts propres au [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] pour que l’empaquetage et F5 fonctionnent correctement avec les kits SDK disponibles dans le [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]. | Y | Le contenu NuGet devient partie intégrante du projet. Aucune attention particulière n’est nécessaire pour F5. |
| Le mécanisme déploie les fichiers autres que les fichiers de référence (par exemple, il déploie le framework de test sur lequel exécuter des tests d’applications [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]). | Y | Si vous déposez les fichiers dans le dossier *\Redist* , les fichiers sont automatiquement déployés. | Y | |
| Le mécanisme ajoute automatiquement les kits SDK de plateforme dans l’IDE Visual Studio. | Y | Si vous déposez le kit SDK [!INCLUDE[win8](../debugger/includes/win8_md.md)] ou le kit SDK Windows Phone dans un emplacement spécifique avec une disposition spécifique, celui-ci est automatiquement intégré à toutes les fonctionnalités de Visual Studio. | N | |
| Le mécanisme prend en charge un ordinateur de développeur propre. (Autrement dit, aucune installation n’est nécessaire, et la récupération simple à partir du contrôle de code source fonctionnera.) | N | Étant donné que vous référencez un kit SDK, vous devez l’archiver séparément de votre solution. Vous pouvez archiver le kit SDK à partir des deux emplacements par défaut hors du Registre à partir desquels MSBuild itère les kits SDK (pour plus d’informations, consultez [Création d’un kit de développement logiciel](../extensibility/creating-a-software-development-kit.md)). Autre solution : si un emplacement personnalisé se compose de kits SDK, vous pouvez spécifier le code suivant dans le fichier projet :<br /><br />`<PropertyGroup>`<br />&nbsp;&nbsp;`<SDKReferenceDirectoryRoot>`<br />&nbsp;&nbsp;`C:\MySDKs`<br />&nbsp;&nbsp;`</SDKReferenceDirectoryRoot>`<br />`</PropertyGroup>`<br /><br /> Ensuite, archivez les kits SDK à cet emplacement. | Y | Vous pouvez extraire la solution, et Visual Studio reconnaît immédiatement les fichiers et agit en conséquence. |
| Vous pouvez rejoindre une grande communauté d’auteurs de packages. | N/A | La communauté est nouvelle. | Y | |
| Vous pouvez rejoindre une grande communauté de consommateurs de packages. | N/A | La communauté est nouvelle. | Y | |
| Vous pouvez rejoindre un écosystème de partenaires (galeries personnalisées, dépôts, etc.). | N/A | Parmi les dépôts disponibles, citons la Place de marché Visual Studio, le Centre de téléchargement Microsoft et [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]. | Y | |
| Le mécanisme s’intègre aux serveurs de build d’intégration continue pour la création et la consommation de packages. | Y | Le kit SDK doit passer l’emplacement archivé (propriété SDKReferenceDirectoryRoot) sur la ligne de commande à MSBuild. | Y | |
| Le mécanisme prend en charge les versions de package stables et préliminaires. | Y | Le kit SDK prend en charge l’ajout de références à plusieurs versions. | Y | |
| Le mécanisme prend en charge la mise à jour automatique des packages installés. | Y | S’il est fourni comme VSIX ou dans le cadre des mises à jour automatiques de Visual Studio, le kit SDK fournit des notifications automatiques. | Y | |
| Le mécanisme contient un fichier *. exe* autonome pour la création et la consommation de packages. | Y | Le kit de développement logiciel (SDK) contient *MSBuild.exe*. | Y | |
| Les packages peuvent être archivés dans la gestion de version. | Y | Vous ne pouvez rien archiver en dehors du nœud Documents, ce qui signifie que les kits SDK d’extension ne peuvent pas être archivés. Le kit SDK d’extension peut être volumineux. | Y | |
| Vous pouvez utiliser une interface PowerShell pour créer et consommer des packages. | O (consommation), N (création) | Aucun outil de création de SDK. La consommation exécute MSBuild sur la ligne de commande. | Y | |
| Vous pouvez utiliser un package de symbole pour la prise en charge du débogage. | Y | Si vous supprimez des fichiers *. pdb* dans le kit de développement logiciel (SDK), les fichiers sont récupérés automatiquement. | Y | |
| Le mécanisme prend en charge les mises à jour automatiques du gestionnaire de packages. | N/A | Le kit SDK est révisé avec MSBuild. | Y | |
| Le mécanisme prend en charge un format léger de manifeste. | Y | *SDKManifest.xml* prend en charge de nombreux attributs, mais un petit sous-ensemble est généralement nécessaire. | Y | |
| Le mécanisme est disponible pour toutes les éditions de Visual Studio. | Y | Le Kit de développement logiciel (SDK) prend en charge toutes les éditions Visual Studio. | Y | NuGet prend en charge toutes les éditions Visual Studio. |

## <a name="see-also"></a>Voir aussi

- [Gérer les références dans un projet](../ide/managing-references-in-a-project.md)
- [Gérer des références dans un projet (Visual Studio pour Mac)](/visualstudio/mac/managing-references-in-a-project)
