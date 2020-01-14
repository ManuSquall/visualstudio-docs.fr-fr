---
title: Ajout de références avec NuGet ou un kit SDK d’extension | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.toolsoptionspages.nuget_package_manager.general
- vs.toolsoptionspages.nuget_package_manager.package_sources
ms.assetid: 2175581e-83cb-444c-bb52-cc1fca8ea196
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 95927385ce3218d73ba6b94819429163178bb65b
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75917345"
---
# <a name="adding-references-using-nuget-versus-an-extension-sdk"></a>Ajout de références avec NuGet ou un kit SDK d’extension
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans les projets Visual Studio, vous pouvez fournir un package pour la consommation avec l’extension NuGet pour Visual Studio ou avec un kit SDK. En décrivant les ressemblances et les différences entre les deux mécanismes, cette rubrique peut vous aider à choisir la plus adaptée à votre tâche.

- NuGet est un système de gestion de packages open source qui simplifie le processus d’intégration de bibliothèques dans une solution de projet. Pour plus d’informations, consultez une [présentation de NuGet](/nuget/what-is-nuget).

- Un kit SDK est une collection de fichiers que Visual Studio traite comme un seul élément de référence. Quand vous affichez la boîte de dialogue **Gestionnaire de références**, vous voyez la liste de tous les kits SDK pertinents pour le projet ouvert. Quand vous ajoutez un kit SDK à un projet, vous pouvez accéder à tout son contenu dans IntelliSense, la **Boîte à outils**, les concepteurs, l’**Explorateur d’objets**, MSBuild, le déploiement, le débogage et l’empaquetage. Pour plus d’informations sur les kits SDK, consultez [Création d’un Kit de développement logiciel](../extensibility/creating-a-software-development-kit.md).

## <a name="which-mechanism-should-i-use"></a>Quel mécanisme dois-je utiliser ?
 Le tableau suivant vous permet de comparer les fonctionnalités de référencement d’un SDK avec celles de NuGet.

|Fonctionnalité|Prise en charge par le SDK|Notes concernant le SDK|Prise en charge par NuGet|Notes concernant NuGet|
|-------------|-----------------|---------------|-------------------|-----------------|
|Le mécanisme référence une entité, et ensuite tous les fichiers et les fonctionnalités sont disponibles.|0|Vous ajoutez un kit SDK à l’aide de la boîte de dialogue **Gestionnaire de références** et tous les fichiers et les fonctionnalités sont disponibles pendant le flux de travail de développement.|0||
|MSBuild consomme automatiquement les assemblys et les fichiers de métadonnées Windows (.winmd).|0|Les références dans le kit SDK sont automatiquement passées au compilateur.|0||
|MSBuild consomme automatiquement les fichiers .h ou .lib.|0|Le fichier *Nom_SDK*.props indique à Visual Studio comment configurer le répertoire Visual C++, et ainsi de suite, pour la consommation automatique du fichier .h ou .lib.|N||
|MSBuild consomme automatiquement les fichiers .js ou .css.|0|Dans l’**Explorateur de solutions**, vous pouvez développer le nœud de référence du kit SDK JavaScript pour afficher des fichiers .js ou .css spécifiques, puis générer des balises `<source include/>` en faisant glisser ces fichiers vers leurs fichiers sources. Le kit SDK prend en charge F5 et l’installation automatique des packages.|0||
|MSBuild ajoute automatiquement le contrôle à la **Boîte à outils**.|0|La **Boîte à outils** peut consommer des kits SDK et afficher des contrôles dans les onglets que vous spécifiez.|N||
|Le mécanisme prend en charge le programme d’installation de Visual Studio pour les extensions (VSIX).|0|VSIX a un manifeste et une logique spéciaux pour créer des packages du SDK.|0|L’extension VSIX peut être incorporée dans un autre programme d’installation.|
|L’**Explorateur d’objets** énumère les références.|0|L’**Explorateur d’objets** obtient automatiquement la liste des références dans les kits SDK et les énumère.|N||
|Les fichiers et les liens sont automatiquement ajoutés à la boîte de dialogue **Gestionnaire de références** (les liens d’aide et autres sont remplis automatiquement).|0|La boîte de dialogue **Gestionnaire de références** énumère automatiquement les kits SDK, ainsi que les liens d’aide et la liste des dépendances aux kits SDK.|N|NuGet fournit sa propre boîte de dialogue **Gérer les packages NuGet**.|
|Le mécanisme prend en charge plusieurs architectures.|0|Les kits SDK peuvent fournir plusieurs configurations. MSBuild consomme les fichiers appropriés pour chaque configuration de projet.|N||
|Le mécanisme prend en charge plusieurs configurations.|0|Les kits SDK peuvent fournir plusieurs configurations. En fonction de l’architecture du projet, MSBuild consomme les fichiers appropriés pour chaque architecture de projet.|N||
|Le mécanisme peut spécifier de « ne pas copier ».|0|Selon que les fichiers sont déposés dans le dossier \redist ou \designtime, vous pouvez contrôler les fichiers à copier dans le package de l’application consommatrice.|N|Vous déclarez les fichiers à copier dans le manifeste du package.|
|Le contenu apparaît dans les fichiers localisés.|0|Les documents XML localisés dans les kits SDK sont automatiquement ajoutés, pour une meilleure expérience de conception.|N||
|MSBuild prend en charge la consommation simultanée de plusieurs versions d’un kit SDK.|0|Le kit SDK prend en charge la consommation simultanée de plusieurs versions.|N|Cela ne constitue pas une référence. Vous ne pouvez pas avoir plusieurs versions de fichiers NuGet dans votre projet en même temps.|
|Le mécanisme prend en charge la spécification de frameworks cibles, de versions de Visual Studio et de types de projets applicables.|0|La boîte de dialogue **Gestionnaire de références** et la **Boîte à outils** affichent uniquement les kits SDK qui s’appliquent à un projet. Ainsi, il est plus facile aux utilisateurs de choisir ceux qui leur conviennent.|O (en partie)|Pivot est le framework cible. Il n’existe aucun filtrage sur l’interface utilisateur. Au moment de l’installation, une erreur peut être retournée.|
|Le mécanisme prend en charge la spécification d’informations d’inscription pour les WinMD natifs.|0|Vous pouvez spécifier la corrélation entre le fichier .winmd et le fichier .dll dans SDKManifest.xml.|N||
|Le mécanisme prend en charge la spécification de dépendances envers d’autres kits SDK.|0|Le kit SDK notifie simplement l’utilisateur. Celui-ci doit toujours les installer et les référencer manuellement.|0|NuGet les extrait automatiquement ; l’utilisateur n’est pas averti.|
|Le mécanisme s’intègre à des concepts [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)] tels que le manifeste d’application et l’ID de framework.|0|Le kit SDK doit passer les concepts propres au [!INCLUDE[win8_appstore_short](../includes/win8-appstore-short-md.md)] pour que l’empaquetage et F5 fonctionnent correctement avec les kits SDK qui sont disponibles dans le [!INCLUDE[win8_appstore_short](../includes/win8-appstore-short-md.md)].|N||
|Le mécanisme s’intègre au pipeline de débogage d’application pour les applications [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)].|0|Le kit SDK doit passer les concepts propres au [!INCLUDE[win8_appstore_short](../includes/win8-appstore-short-md.md)] pour que l’empaquetage et F5 fonctionnent correctement avec les kits SDK disponibles dans le [!INCLUDE[win8_appstore_short](../includes/win8-appstore-short-md.md)].|0|Le contenu NuGet devient partie intégrante du projet. Aucune attention particulière n’est nécessaire pour F5.|
|Le mécanisme s’intègre aux manifestes d’application.|0|Le kit SDK doit passer les concepts propres au [!INCLUDE[win8_appstore_short](../includes/win8-appstore-short-md.md)] pour que l’empaquetage et F5 fonctionnent correctement avec les kits SDK disponibles dans le [!INCLUDE[win8_appstore_short](../includes/win8-appstore-short-md.md)].|0|Le contenu NuGet devient partie intégrante du projet. Aucune attention particulière n’est nécessaire pour F5.|
|Le mécanisme déploie les fichiers autres que les fichiers de référence (par exemple, il déploie le framework de test sur lequel exécuter des tests d’applications [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]).|0|Si vous déposez les fichiers dans le dossier \redist, ceux-ci sont automatiquement déployés.|0||
|Le mécanisme ajoute automatiquement les kits SDK de plateforme dans l’IDE Visual Studio.|0|Si vous déposez le kit SDK [!INCLUDE[win8](../includes/win8-md.md)] ou le kit SDK Windows Phone dans un emplacement spécifique avec une disposition spécifique, celui-ci est automatiquement intégré à toutes les fonctionnalités de Visual Studio.|N||
|Le mécanisme prend en charge un ordinateur de développeur propre. (Autrement dit, aucune installation n’est nécessaire, et la récupération simple à partir du contrôle de code source fonctionnera.)|N|Étant donné que vous référencez un kit SDK, vous devez l’archiver séparément de votre solution. Vous pouvez archiver le kit SDK à partir des deux emplacements par défaut hors du Registre à partir desquels MSBuild itère les kits SDK (pour plus d’informations, consultez [Création d’un kit de développement logiciel](../extensibility/creating-a-software-development-kit.md)). Autre solution : si un emplacement personnalisé se compose de kits SDK, vous pouvez spécifier le code suivant dans le fichier projet :<br /><br /> `<PropertyGroup>    <SDKReferenceDirectoryRoot>C:\MySDKs</SDKReferenceDirectoryRoot>   </PropertyGroup>`<br /><br /> Ensuite, archivez les kits SDK à cet emplacement.|0|Vous pouvez extraire la solution, et Visual Studio reconnaît immédiatement les fichiers et agit en conséquence.|
|Vous pouvez rejoindre une grande communauté d’auteurs de packages.|N/A|La communauté est nouvelle.|0||
|Vous pouvez rejoindre une grande communauté de consommateurs de packages.|N/A|La communauté est nouvelle.|0||
|Vous pouvez rejoindre un écosystème de partenaires (galeries personnalisées, dépôts, etc.).|N/A|Parmi les dépôts disponibles, citons la Galerie Visual Studio, le Centre de téléchargement Microsoft et [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)].|0||
|Le mécanisme s’intègre aux serveurs de build d’intégration continue pour la création et la consommation de packages.|0|Le kit SDK doit passer l’emplacement archivé (propriété SDKReferenceDirectoryRoot) sur la ligne de commande à MSBuild.|0||
|Le mécanisme prend en charge les versions de package stables et préliminaires.|0|Le kit SDK prend en charge l’ajout de références à plusieurs versions.|0||
|Le mécanisme prend en charge la mise à jour automatique des packages installés.|0|S’il est fourni comme VSIX ou dans le cadre des mises à jour automatiques de Visual Studio, le kit SDK fournit des notifications automatiques.|0||
|Le mécanisme contient un fichier .exe autonome pour créer et consommer des packages.|0|Le kit SDK contient MSBuild.exe.|0||
|Les packages peuvent être archivés dans la gestion de version.|0|Vous ne pouvez rien archiver en dehors du nœud Documents, ce qui signifie que les kits SDK d’extension ne peuvent pas être archivés. La taille du kit SDK d’extension peut être élevée.|0||
|Vous pouvez utiliser une interface PowerShell pour créer et consommer des packages.|O (consommation), N (création)|Aucun outil de création de SDK. La consommation exécute MSBuild sur la ligne de commande.|0||
|Vous pouvez utiliser un package de symbole pour la prise en charge du débogage.|0|Si vous déposez des fichiers .pdb dans le kit SDK, ceux-ci sont récupérés automatiquement.|0||
|Le mécanisme prend en charge les mises à jour automatiques du gestionnaire de packages.|N/A|Le kit SDK est révisé avec MSBuild.|0||
|Le mécanisme prend en charge un format léger de manifeste.|0|SDKManifest.xml prend en charge de nombreux attributs, mais seule une petite partie est généralement nécessaire.|0||
|Le mécanisme est disponible pour toutes les éditions de Visual Studio.|0|Le kit SDK prend en charge toutes les éditions de Visual Studio, de Visual Studio Express jusqu’à [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)].|0|NuGet prend en charge toutes les éditions de Visual Studio, de Visual Studio Express jusqu’à [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)].|
|Le mécanisme est disponible pour tous les types de projets.|N|Le kit SDK prend en charge les applications du [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] à partir de [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|N|Vous pouvez consulter une liste de projets autorisés.|

## <a name="see-also"></a>Voir aussi
 [Gestion des références dans un projet](../ide/managing-references-in-a-project.md)
