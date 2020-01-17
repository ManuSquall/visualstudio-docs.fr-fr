---
title: Utiliser les paramètres de ligne de commande pour installer Visual Studio
titleSuffix: ''
description: Découvrez comment utiliser les paramètres de ligne de commande pour contrôler ou personnaliser votre installation de Visual Studio.
ms.date: 10/22/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 7210a2834dda749cfe1d89b9093cd627b7c0ae1b
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114358"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>Utiliser les paramètres de ligne de commande pour installer Visual Studio

Lorsque vous installez Visual Studio à partir d’une invite de commandes, vous pouvez utiliser divers paramètres de ligne de commande pour contrôler ou personnaliser l’installation. À partir de la ligne de commande, vous pouvez effectuer les actions suivantes :

- Démarrer l’installation avec certaines options présélectionnées.
- Automatiser le processus d’installation.
- Créer un cache (disposition) des fichiers d’installation pour une utilisation ultérieure.

Les options de ligne de commande sont utilisées conjointement avec le programme d’amorçage du programme d’installation, qui est le petit fichier (1 Mo) qui initie le processus de téléchargement. Le programme d’amorçage est le premier exécutable qui est lancé quand vous effectuez un téléchargement à partir du site Visual Studio.

::: moniker range="vs-2017"

Pour obtenir un programme d’amorçage pour Visual Studio 2017, consultez la page de téléchargement des [**versions précédentes de Visual Studio**](https://visualstudio.microsoft.com/vs/older-downloads/) pour plus d’informations sur la façon de procéder.

::: moniker-end

::: moniker range="vs-2019"

Utilisez les liens suivants pour obtenir un lien direct vers le programme d’amorçage de la version la plus récente de l’édition du produit que vous installez :

- [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)
- [Visual Studio 2019 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)
- [Visual Studio 2019 Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)

::: moniker-end


Votre fichier de programme d’amorçage doit correspondre ou être similaire à l’un des noms de fichiers suivants :

* vs_enterprise.exe
* vs_professional.exe
* vs_community.exe

>[!TIP]
>Si vous avez précédemment téléchargé un fichier de programme d’amorçage et que vous souhaitez vérifier sa version, voici comment procéder. Dans Windows, ouvrez l’Explorateur de fichiers, cliquez avec le bouton droit sur le fichier du programme d’amorçage, choisissez **Propriétés**, cliquez sur l’onglet **Détails** , puis affichez le numéro de **version du produit** . Pour faire correspondre ce nombre à une version de Visual Studio, consultez la page [numéros de build et dates de publication de Visual Studio](visual-studio-build-numbers-and-release-dates.md) .

## <a name="command-line-parameters"></a>Paramètres de ligne de commande

 Les paramètres de ligne de commande Visual Studio ne respectent pas la casse.

> Syntaxe : `vs_enterprise.exe [command] <options>...`

Remplacez `vs_enterprise.exe` comme il convient pour l’édition du produit que vous installez. (Vous pouvez également utiliser `vs_installer.exe`.)

>[!TIP]
> Pour obtenir des exemples supplémentaires sur l’utilisation de la ligne de commande afin d’installer Visual Studio, consultez la page [Exemples de paramètres de ligne de commande](command-line-parameter-examples.md).

::: moniker range="vs-2017"

| **Commande** | **Description** |
| ----------------------- | --------------- |
| (vide) | Installe le produit. |
| `modify` | Modifie un produit installé. |
| `update` | Met à jour un produit installé. |
| `repair` | Répare un produit installé. |
| `uninstall` | Désinstalle un produit installé. |
| `export` | **Nouveauté de la version 15,9**: exporte la sélection de l’installation vers un fichier de configuration d’installation. **Remarque**: ne peut être utilisé qu’avec vs_installer. exe. |

::: moniker-end

::: moniker range="vs-2019"

| **Commande** | **Description** |
| ----------------------- | --------------- |
| (vide) | Installe le produit. |
| `modify` | Modifie un produit installé. |
| `update` | Met à jour un produit installé. |
| `repair` | Répare un produit installé. |
| `uninstall` | Désinstalle un produit installé. |
| `export` | Exporte la sélection de l’installation dans un fichier de configuration d’installation. **Remarque**: ne peut être utilisé qu’avec vs_installer. exe. |

::: moniker-end

## <a name="install-options"></a>Options d’installation

::: moniker range="vs-2017"

| **Option d’installation** | **Description** |
| ----------------------- | --------------- |
| `--installPath <dir>` | Répertoire d’installation de l’instance à installer. Pour la commande d’installation, cette option est **facultative** et il s’agit de l’emplacement où l’instance doit être installée. Pour les autres commandes, cette option est **requise** et il s’agit de l’emplacement où l’instance précédente a été installée. |
| `--addProductLang <language-locale>` | **Facultatif** : lors d’une installation ou d’une modification, cette option détermine les modules linguistiques de l’interface utilisateur qui sont installés sur le produit. Elle peut apparaître plusieurs fois sur la ligne de commande pour ajouter plusieurs modules linguistiques. Si elle est absente, l’installation utilise les paramètres régionaux de l’ordinateur. Pour plus d’informations, consultez la section [Liste des paramètres régionaux de langue](#list-of-language-locales) de cette page.|
| `--removeProductLang <language-locale>` | **Facultatif** : lors d’une installation ou d’une modification, cette option détermine les modules linguistiques de l’interface utilisateur qui doivent être supprimés du produit. Elle peut apparaître plusieurs fois sur la ligne de commande pour ajouter plusieurs modules linguistiques. Pour plus d’informations, consultez la section [Liste des paramètres régionaux de langue](#list-of-language-locales) de cette page.|
| `--add <one or more workload or component IDs>` | **Facultatif** : un ou plusieurs ID de charge de travail ou composant à ajouter. Les composants obligatoires de l’artefact sont installés, mais pas les composants recommandés ni facultatifs. Vous pouvez contrôler globalement les autres composants à l’aide des options `--includeRecommended` et/ou `--includeOptional`. Pour inclure plusieurs charges de travail ou composants, répétez la commande `--add` (par exemple, `--add Workload1 --add Workload2`). Pour un contrôle plus précis, vous pouvez ajouter `;includeRecommended` ou `;includeOptional` à l’ID (par exemple, `--add Workload1;includeRecommended` ou `--add Workload2;includeRecommended;includeOptional`). Pour plus d’informations, consultez la page [ID de charge de travail et de composant](workload-and-component-ids.md). Vous pouvez répéter cette option si nécessaire.|
| `--remove <one or more workload or component IDs>` | **Facultatif** : un ou plusieurs ID de charge de travail ou composant à supprimer. Pour plus d’informations, consultez notre page [ID de charge de travail et de composant](workload-and-component-ids.md). Vous pouvez répéter cette option si nécessaire.|
| `--in <path>` | **Facultatif** : URI ou chemin d’un fichier réponse.  |
| `--all` | **Facultatif** : indique s’il faut installer tous les composants et charges de travail d’un produit. |
| `--allWorkloads` | **Facultatif** : installe toutes les charges de travail et tous les composants, mais n’installe pas les composants recommandés ou facultatifs. |
| `--includeRecommended` | **Facultatif** : inclut les composants recommandés pour toutes les charges de travail installées, mais pas les composants facultatifs. Les charges de travail sont spécifiées avec `--allWorkloads` ou `--add`. |
| `--includeOptional` | **Facultatif** : inclut les composants facultatifs pour toutes les charges de travail installées, mais pas les composants recommandés. Les charges de travail sont spécifiées avec `--allWorkloads` ou `--add`.  |
| `--quiet, -q` | **Facultatif**: n’affiche pas d’interface utilisateur lors de l’installation. |
| `--passive, -p` | **Facultatif**: afficher l’interface utilisateur, mais ne pas demander d’interaction avec l’utilisateur. |
| `--norestart` | **Facultatif**: s’il est présent, les commandes avec `--passive` ou `--quiet` ne redémarrent pas automatiquement l’ordinateur (si nécessaire).  Option ignorée si ni `--passive` ni `--quiet` ne sont spécifiés.  |
| `--nickname <name>` | **Facultatif** : définit le surnom à attribuer à un produit installé. Le surnom ne peut pas comporter plus de 10 caractères.  |
| `--productKey` | **Facultatif** : définit la clé de produit à utiliser pour un produit installé. Elle est composée de 25 caractères alphanumériques au format `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` ou `xxxxxxxxxxxxxxxxxxxxxxxxx`. |
| `--help, --?, -h, -?` | Permet d’afficher une version hors connexion de cette page. |
| `--config <path>` | **Facultatif** et **nouveauté de la version 15.9** : pendant une opération d’installation ou de modification, cette option détermine les charges de travail et composants à ajouter en fonction d’un fichier de configuration d’installation déjà enregistré. Cette opération est additive et ne supprime aucune charge de travail ou composant s’ils ne sont pas présents dans le fichier. En outre, les éléments qui ne s’appliquent pas au produit ne sont pas ajoutés. Pendant une opération d’exportation, cette option détermine l’emplacement auquel enregistrer le fichier de configuration d’installation. |

::: moniker-end

::: moniker range="vs-2019"

| **Option d’installation** | **Description** |
| ----------------------- | --------------- |
| `--installPath <dir>` | Répertoire d’installation de l’instance à installer. Pour la commande d’installation, cette option est **facultative** et il s’agit de l’emplacement où l’instance doit être installée. Pour les autres commandes, cette option est **requise** et il s’agit de l’emplacement où l’instance précédente a été installée. |
| `--addProductLang <language-locale>` | **Facultatif** : lors d’une installation ou d’une modification, cette option détermine les modules linguistiques de l’interface utilisateur qui sont installés sur le produit. Elle peut apparaître plusieurs fois sur la ligne de commande pour ajouter plusieurs modules linguistiques. Si elle est absente, l’installation utilise les paramètres régionaux de l’ordinateur. Pour plus d’informations, consultez la section [Liste des paramètres régionaux de langue](#list-of-language-locales) de cette page.|
| `--removeProductLang <language-locale>` | **Facultatif** : lors d’une installation ou d’une modification, cette option détermine les modules linguistiques de l’interface utilisateur qui doivent être supprimés du produit. Elle peut apparaître plusieurs fois sur la ligne de commande pour ajouter plusieurs modules linguistiques. Pour plus d’informations, consultez la section [Liste des paramètres régionaux de langue](#list-of-language-locales) de cette page.|
| `--add <one or more workload or component IDs>` | **Facultatif** : un ou plusieurs ID de charge de travail ou composant à ajouter. Les composants obligatoires de l’artefact sont installés, mais pas les composants recommandés ni facultatifs. Vous pouvez contrôler globalement les autres composants à l’aide des options `--includeRecommended` et/ou `--includeOptional`. Pour inclure plusieurs charges de travail ou composants, répétez la commande `--add` (par exemple, `--add Workload1 --add Workload2`). Pour un contrôle plus précis, vous pouvez ajouter `;includeRecommended` ou `;includeOptional` à l’ID (par exemple, `--add Workload1;includeRecommended` ou `--add Workload2;includeRecommended;includeOptional`). Pour plus d’informations, consultez la page [ID de charge de travail et de composant](workload-and-component-ids.md). Vous pouvez répéter cette option si nécessaire.|
| `--remove <one or more workload or component IDs>` | **Facultatif** : un ou plusieurs ID de charge de travail ou composant à supprimer. Pour plus d’informations, consultez notre page [ID de charge de travail et de composant](workload-and-component-ids.md). Vous pouvez répéter cette option si nécessaire.|
| `--in <path>` | **Facultatif** : URI ou chemin d’un fichier réponse.  |
| `--all` | **Facultatif** : indique s’il faut installer tous les composants et charges de travail d’un produit. |
| `--allWorkloads` | **Facultatif** : installe toutes les charges de travail et tous les composants, mais n’installe pas les composants recommandés ou facultatifs. |
| `--includeRecommended` | **Facultatif** : inclut les composants recommandés pour toutes les charges de travail installées, mais pas les composants facultatifs. Les charges de travail sont spécifiées avec `--allWorkloads` ou `--add`. |
| `--includeOptional` | **Facultatif** : inclut les composants facultatifs pour toutes les charges de travail installées, mais pas les composants recommandés. Les charges de travail sont spécifiées avec `--allWorkloads` ou `--add`.  |
| `--quiet, -q` | **Facultatif**: n’affiche pas d’interface utilisateur lors de l’installation. |
| `--passive, -p` | **Facultatif**: afficher l’interface utilisateur, mais ne pas demander d’interaction avec l’utilisateur. |
| `--norestart` | **Facultatif**: s’il est présent, les commandes avec `--passive` ou `--quiet` ne redémarrent pas automatiquement l’ordinateur (si nécessaire).  Option ignorée si ni `--passive` ni `--quiet` ne sont spécifiés.  |
| `--nickname <name>` | **Facultatif** : définit le surnom à attribuer à un produit installé. Le surnom ne peut pas comporter plus de 10 caractères.  |
| `--productKey` | **Facultatif** : définit la clé de produit à utiliser pour un produit installé. Elle est composée de 25 caractères alphanumériques au format `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` ou `xxxxxxxxxxxxxxxxxxxxxxxxx`. |
| `--help, --?, -h, -?` | Permet d’afficher une version hors connexion de cette page. |
| `--config <path>` | **Facultatif**: lors d’une opération d’installation ou de modification, cela détermine les charges de travail et les composants à ajouter en fonction d’un fichier de configuration d’installation précédemment enregistré. Cette opération est additive et ne supprime aucune charge de travail ou composant s’ils ne sont pas présents dans le fichier. En outre, les éléments qui ne s’appliquent pas au produit ne sont pas ajoutés. Pendant une opération d’exportation, cette option détermine l’emplacement auquel enregistrer le fichier de configuration d’installation. |

::: moniker-end

> [!IMPORTANT]
> Lorsque vous spécifiez plusieurs charges de travail et plusieurs composants, vous devez répéter le commutateur de ligne de commande `--add` ou `--remove` pour chaque élément.

## <a name="layout-options"></a>Options de disposition

::: moniker range="vs-2017"

| **Options de disposition** | **Description** |
| ----------------------- | --------------- |
| `--layout <dir>` | Spécifie un répertoire pour créer un cache d’installation hors connexion. Pour plus d’informations, consultez [Créer une installation réseau de Visual Studio](create-a-network-installation-of-visual-studio.md).|
| `--lang <one or more language-locales>` | **Facultatif** : utilisé avec `--layout` pour préparer un cache d’installation hors connexion avec des packages de ressources correspondant à la langue ou aux langues spécifiées. Pour plus d’informations, consultez la section [Liste des paramètres régionaux de langue](#list-of-language-locales) de cette page.|
| `--add <one or more workload or component IDs>` | **Facultatif** : un ou plusieurs ID de charge de travail ou composant à ajouter. Les composants obligatoires de l’artefact sont installés, mais pas les composants recommandés ni facultatifs. Vous pouvez contrôler globalement les autres composants à l’aide des options `--includeRecommended` et/ou `--includeOptional`. Pour un contrôle plus précis, vous pouvez ajouter `;includeRecommended` ou `;includeOptional` à l’ID (par exemple, `--add Workload1;includeRecommended` ou `--add Workload2;includeOptional`). Pour plus d’informations, consultez la page [ID de charge de travail et de composant](workload-and-component-ids.md). <br/>**Remarque** : Si `--add` est utilisé, seuls les composants et les charges de travail spécifiés ainsi que leurs dépendances sont téléchargés. Si `--add` n’est pas spécifié, tous les composants et charges de travail sont téléchargés vers la disposition.|
| `--includeRecommended` | **Facultatif** : inclut les composants recommandés pour toutes les charges de travail installées, mais pas les composants facultatifs. Les charges de travail sont spécifiées avec `--allWorkloads` ou `--add`. |
| `--includeOptional` | **Facultatif** : inclut les composants recommandés *et* facultatifs pour toutes les charges de travail contenues dans la disposition. Les charges de travail sont spécifiées avec `--add`.  |
| `--keepLayoutVersion` | **Nouveautés de la version 15.3, facultatif** : application des modifications à la disposition sans mettre à jour la version de la disposition. |
| `--verify` | **Nouveautés de la version 15.3, facultatif** : vérification du contenu d’une disposition. Tous les fichiers endommagés ou manquants sont listés. |
| `--fix` | **Nouveautés de la version 15.3, facultatif** : vérification du contenu d’une disposition. Si des fichiers sont endommagés ou manquants, ils sont retéléchargés. Un accès à Internet est obligatoire pour corriger une disposition. |
| `--clean <one or more paths to catalogs>` | **Nouveautés de la version 15.3, facultatif** : suppression des anciennes versions des composants d’une disposition qui a été mise à jour vers une version plus récente. |

| **Options d’installation avancées** | **Description** |
| ----------------------- | --------------- |
| `--channelId <id>` | **Facultatif** : ID de canal pour l’instance à installer. Cette option est requise pour la commande d’installation et est ignorée pour les autres commandes si `--installPath` est spécifié. |
| `--channelUri <uri>` | **Facultatif** : URI du manifeste de canal. Si les mises à jour ne sont pas souhaitées, `--channelUri` pouvez pointer vers un fichier inexistant (par exemple,--channelUri C:\doesntExist.chman). Cela peut être utilisé pour la commande d’installation. elle est ignorée pour les autres commandes. |
| `--installChannelUri <uri>` | **Facultatif** : URI du manifeste de canal à utiliser pour l’installation. L’URI spécifié par `--channelUri` (qui doit être spécifié en même temps que `--installChannelUri`) est utilisé pour détecter les mises à jour. Cela peut être utilisé pour la commande d’installation. elle est ignorée pour les autres commandes. |
| `--installCatalogUri <uri>` | **Facultatif** : URI du manifeste de catalogue à utiliser pour l’installation. Si spécifié, le gestionnaire de canal tente de télécharger le manifeste de catalogue à partir de cet URI avant d’utiliser l’URI du manifeste de canal d’installation. Ce paramètre est utilisé pour prendre en charge l’installation hors connexion, où le cache de disposition est créé avec le catalogue de produits déjà téléchargé. Cela peut être utilisé pour la commande d’installation. elle est ignorée pour les autres commandes. |
| `--productId <id>` | **Facultatif** : ID de produit pour l’instance à installer. Cette préproduction est préremplie dans des conditions d’installation normales. |
| `--wait` | **Facultatif** : le processus attend la fin de l’installation pour retourner un code de sortie. Cela est utile lorsque vous automatisez des installations et que vous devez attendre la fin de l’installation pour gérer le code de retour de cette installation. |
| `--locale <language-locale>` | **Facultatif** : permet de changer la langue d’affichage de l’interface utilisateur pour le programme d’installation proprement dit. Ce paramètre est conservé. Pour plus d’informations, consultez la section [Liste des paramètres régionaux de langue](#list-of-language-locales) de cette page.|
| `--cache` | **Nouveauté de la version 15.2, facultatif** : le cas échéant, les packages sont conservés après leur installation pour les réparations ultérieures. Cela remplace le paramètre de stratégie globale à utiliser pour les installations, réparations ou modifications ultérieures. La stratégie par défaut consiste à mettre les packages en cache. Option ignorée pour la commande de désinstallation. Pour plus d’informations, consultez [Désactiver ou déplacer le cache du package](disable-or-move-the-package-cache.md). |
| `--nocache` | **Nouveautés de la version 15.2, facultatif** : le cas échéant, les packages sont supprimés après avoir été installés ou réparés. Ils seront téléchargés à nouveau uniquement si nécessaire, puis supprimés après utilisation. Cela remplace le paramètre de stratégie globale à utiliser pour les installations, réparations ou modifications ultérieures. La stratégie par défaut consiste à mettre les packages en cache. Option ignorée pour la commande de désinstallation. Pour plus d’informations, consultez [Désactiver ou déplacer le cache du package](disable-or-move-the-package-cache.md). |
| `--noUpdateInstaller` | **Nouveautés de la version 15.2, facultatif** : Le cas échéant, empêche le programme d’installation de se mettre à jour quand le mode silencieux est spécifié. Le programme d’installation ne parvient pas à exécuter la commande et retourne un code de sortie différent de zéro si noUpdateInstaller est spécifié avec le mode silencieux quand une mise à jour du programme d’installation est obligatoire. |
| `--noWeb` | **Nouveauté de 15,3, facultatif**: le cas échéant, le programme d’installation de Visual Studio utilise les fichiers de votre répertoire de disposition pour installer Visual Studio. Si un utilisateur tente d’installer des composants qui ne sont pas dans la disposition, le programme d’installation échoue.  Pour plus d’informations, consultez [Déploiement à partir d’une installation réseau](create-a-network-installation-of-visual-studio.md). <br/><br/> **Important**: ce commutateur n’empêche pas le programme d’installation de Visual Studio de vérifier la présence de mises à jour. Pour plus d’informations, consultez [Contrôler les mises à jour applicables aux déploiements de Visual Studio à partir du réseau](controlling-updates-to-visual-studio-deployments.md). |
| `--path <name>=<path>` | **Nouveautés de la version 15.7, facultatif** : permet de spécifier des chemins d’installation personnalisés pour l’installation. Les noms de chemin pris en charge sont shared, cache et install. |
| `--path cache=<path>` | **Nouveautés de la version 15.7, facultatif** : utilise l’emplacement que vous spécifiez pour télécharger les fichiers d’installation. Cet emplacement peut être défini uniquement pendant la première installation de Visual Studio. Exemple : `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **Nouveautés de la version 15.7, facultatif** : contient des fichiers partagés pour les installations de Visual Studio côte à côte. Certains outils et kits SDK effectuent l’installation à un emplacement sur ce lecteur, tandis que d’autres peuvent l’effectuer sur un autre lecteur en passant outre ce paramétrage. Exemple : `--path shared="C:\VS\shared"` <br><br>Important : Ceci ne peut être défini qu’une seule fois, lors de la première installation de Visual Studio. |
| `--path install=<path>` | **Nouveautés de la version 15.7, facultatif** : équivaut à `–-installPath`. En particulier, les options `--installPath "C:\VS"` et `--path install="C:\VS"` sont équivalentes. Seule une de ces commandes peut être utilisée à la fois. |

::: moniker-end

::: moniker range="vs-2019"

| **Options de disposition** | **Description** |
| ----------------------- | --------------- |
| `--layout <dir>` | Spécifie un répertoire pour créer un cache d’installation hors connexion. Pour plus d’informations, consultez [Créer une installation réseau de Visual Studio](create-a-network-installation-of-visual-studio.md).|
| `--lang <one or more language-locales>` | **Facultatif** : utilisé avec `--layout` pour préparer un cache d’installation hors connexion avec des packages de ressources correspondant à la langue ou aux langues spécifiées. Pour plus d’informations, consultez la section [Liste des paramètres régionaux de langue](#list-of-language-locales) de cette page.|
| `--add <one or more workload or component IDs>` | **Facultatif** : un ou plusieurs ID de charge de travail ou composant à ajouter. Les composants obligatoires de l’artefact sont installés, mais pas les composants recommandés ni facultatifs. Vous pouvez contrôler globalement les autres composants à l’aide des options `--includeRecommended` et/ou `--includeOptional`. Pour un contrôle plus précis, vous pouvez ajouter `;includeRecommended` ou `;includeOptional` à l’ID (par exemple, `--add Workload1;includeRecommended` ou `--add Workload2;includeOptional`). Pour plus d’informations, consultez la page [ID de charge de travail et de composant](workload-and-component-ids.md). <br/>**Remarque** : Si `--add` est utilisé, seuls les composants et les charges de travail spécifiés ainsi que leurs dépendances sont téléchargés. Si `--add` n’est pas spécifié, tous les composants et charges de travail sont téléchargés vers la disposition.|
| `--includeRecommended` | **Facultatif** : inclut les composants recommandés pour toutes les charges de travail installées, mais pas les composants facultatifs. Les charges de travail sont spécifiées avec `--allWorkloads` ou `--add`. |
| `--includeOptional` | **Facultatif** : inclut les composants recommandés *et* facultatifs pour toutes les charges de travail contenues dans la disposition. Les charges de travail sont spécifiées avec `--add`.  |
| `--keepLayoutVersion` | **Facultatif**: appliquez les modifications à la disposition sans mettre à jour la version de la disposition. |
| `--verify` | **Facultatif**: Vérifiez le contenu d’une disposition. Tous les fichiers endommagés ou manquants sont listés. |
| `--fix` | **Facultatif**: Vérifiez le contenu d’une disposition.  Si des fichiers sont endommagés ou manquants, ils sont retéléchargés. Un accès à Internet est obligatoire pour corriger une disposition. |
| `--clean <one or more paths to catalogs>` | **Facultatif**: supprime les anciennes versions des composants d’une mise en page qui a été mise à jour vers une version plus récente. |

| **Options d’installation avancées** | **Description** |
| ----------------------- | --------------- |
| `--channelId <id>` | **Facultatif** : ID de canal pour l’instance à installer. Cette option est requise pour la commande d’installation et est ignorée pour les autres commandes si `--installPath` est spécifié. |
| `--channelUri <uri>` | **Facultatif** : URI du manifeste de canal. Si les mises à jour ne sont pas souhaitées, `--channelUri` pouvez pointer vers un fichier inexistant (par exemple,--channelUri C:\doesntExist.chman). Cela peut être utilisé pour la commande d’installation. elle est ignorée pour les autres commandes. |
| `--installChannelUri <uri>` | **Facultatif** : URI du manifeste de canal à utiliser pour l’installation. L’URI spécifié par `--channelUri` (qui doit être spécifié en même temps que `--installChannelUri`) est utilisé pour détecter les mises à jour. Cela peut être utilisé pour la commande d’installation. elle est ignorée pour les autres commandes. |
| `--installCatalogUri <uri>` | **Facultatif** : URI du manifeste de catalogue à utiliser pour l’installation. Si spécifié, le gestionnaire de canal tente de télécharger le manifeste de catalogue à partir de cet URI avant d’utiliser l’URI du manifeste de canal d’installation. Ce paramètre est utilisé pour prendre en charge l’installation hors connexion, où le cache de disposition est créé avec le catalogue de produits déjà téléchargé. Cela peut être utilisé pour la commande d’installation. elle est ignorée pour les autres commandes. |
| `--productId <id>` | **Facultatif** : ID de produit pour l’instance à installer. Cette préproduction est préremplie dans des conditions d’installation normales. |
| `--wait` | **Facultatif** : le processus attend la fin de l’installation pour retourner un code de sortie. Cela est utile lorsque vous automatisez des installations et que vous devez attendre la fin de l’installation pour gérer le code de retour de cette installation. |
| `--locale <language-locale>` | **Facultatif** : permet de changer la langue d’affichage de l’interface utilisateur pour le programme d’installation proprement dit. Ce paramètre est conservé. Pour plus d’informations, consultez la section [Liste des paramètres régionaux de langue](#list-of-language-locales) de cette page.|
| `--cache` | **Facultatif**: le cas échéant, les packages sont conservés après leur installation pour les réparations suivantes. Cela remplace le paramètre de stratégie globale à utiliser pour les installations, réparations ou modifications ultérieures. La stratégie par défaut consiste à mettre les packages en cache. Option ignorée pour la commande de désinstallation. Pour plus d’informations, consultez [Désactiver ou déplacer le cache du package](disable-or-move-the-package-cache.md). |
| `--nocache` | **Facultatif**: le cas échéant, les packages sont supprimés après avoir été installés ou réparés. Ils seront téléchargés à nouveau uniquement si nécessaire, puis supprimés après utilisation. Cela remplace le paramètre de stratégie globale à utiliser pour les installations, réparations ou modifications ultérieures. La stratégie par défaut consiste à mettre les packages en cache. Option ignorée pour la commande de désinstallation. Pour plus d’informations, consultez [Désactiver ou déplacer le cache du package](disable-or-move-the-package-cache.md). |
| `--noUpdateInstaller` | **Facultatif**: le cas échéant, empêche le programme d’installation de se mettre à jour lorsque le mode silencieux est spécifié. Le programme d’installation ne parvient pas à exécuter la commande et retourne un code de sortie différent de zéro si noUpdateInstaller est spécifié avec le mode silencieux quand une mise à jour du programme d’installation est obligatoire. |
| `--noWeb` | **Facultatif**: si elle est présente, le programme d’installation de Visual Studio utilise les fichiers de votre répertoire de disposition pour installer Visual Studio. Si un utilisateur tente d’installer des composants qui ne sont pas dans la disposition, le programme d’installation échoue.  Pour plus d’informations, consultez [Déploiement à partir d’une installation réseau](create-a-network-installation-of-visual-studio.md). <br/><br/> **Important**: ce commutateur n’empêche pas le programme d’installation de Visual Studio de vérifier la présence de mises à jour. Pour plus d’informations, consultez [Contrôler les mises à jour applicables aux déploiements de Visual Studio à partir du réseau](controlling-updates-to-visual-studio-deployments.md). **Nouveauté de 16.3.5**: ce commutateur empêche les erreurs et améliore les performances avec les installations et les mises à jour hors connexion.|
| `--path <name>=<path>` | **Facultatif**: utilisé pour spécifier les chemins d’installation personnalisés pour l’installation. Les noms de chemin pris en charge sont shared, cache et install. |
| `--path cache=<path>` | **Facultatif**: utilise l’emplacement que vous spécifiez pour télécharger les fichiers d’installation. Cet emplacement peut être défini uniquement pendant la première installation de Visual Studio. Exemple : `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **Facultatif**: contient des fichiers partagés pour les installations côte à côte de Visual Studio. Certains outils et kits SDK effectuent l’installation à un emplacement sur ce lecteur, tandis que d’autres peuvent l’effectuer sur un autre lecteur en passant outre ce paramétrage. Exemple : `--path shared="C:\VS\shared"` <br><br>Important : Ceci ne peut être défini qu’une seule fois, lors de la première installation de Visual Studio. |
| `--path install=<path>` | **Facultatif**: équivalent à `–-installPath`. En particulier, les options `--installPath "C:\VS"` et `--path install="C:\VS"` sont équivalentes. Seule une de ces commandes peut être utilisée à la fois. |

::: moniker-end

## <a name="list-of-workload-ids-and-component-ids"></a>Liste des ID de charge de travail et de composant

Pour obtenir la liste des ID de charge de travail et de composant triés par produit Visual Studio, consultez la page [ID de charge de travail et de composant Visual Studio](workload-and-component-ids.md).

## <a name="list-of-language-locales"></a>Liste des paramètres régionaux de langue

| **Paramètres régionaux de langue** | **Langue** |
| ----------------------- | --------------- |
| Cs-cz | Tchèque |
| De-de | Allemand |
| En-us | Anglais |
| Es-es | Espagnol |
| Fr-fr | Français |
| It-it | Italien |
| Ja-jp | Japonais |
| Ko-kr | Coréen |
| Pl-pl | Polonais |
| Pt-br | Portugais – Brésil |
| Ru-ru | Russe |
| Tr-tr | Turc |
| Zh-cn | Chinois (simplifié) |
| Zh-tw | Chinois (traditionnel) |

## <a name="error-codes"></a>Codes d’erreur

En fonction du résultat de l’opération, la variable d’environnement `%ERRORLEVEL%` a l’une des valeurs suivantes :

[!INCLUDE[install-error-codes-md](includes/install-error-codes-md.md)]

Chaque opération génère plusieurs fichiers journaux dans le répertoire `%TEMP%`, qui indiquent la progression de l’installation. Triez le dossier par date et recherchez les fichiers commençant par `dd_bootstrapper`, `dd_client` et `dd_setup` pour le programme d’amorçage, l’application du programme d’installation et le moteur d’installation, respectivement.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

- [Exemples de paramètres de ligne de commande pour l’installation de Visual Studio](command-line-parameter-examples.md)
- [Créer une installation hors connexion de Visual Studio](create-an-offline-installation-of-visual-studio.md)
- [Automatiser l’installation de Visual Studio avec un fichier réponse](automated-installation-with-response-file.md)
- [ID de charge de travail et de composant Visual Studio](workload-and-component-ids.md)
