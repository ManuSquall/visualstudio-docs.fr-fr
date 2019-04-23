---
title: Utiliser les paramètres de ligne de commande pour installer Visual Studio
titleSuffix: ''
description: Découvrez comment utiliser les paramètres de ligne de commande pour contrôler ou personnaliser votre installation de Visual Studio.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 8e999df4fc1269025c9adc038c1a17dd586a3081
ms.sourcegitcommit: d4bea2867a4f0c3b044fd334a54407c0fe87f9e8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58790483"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>Utiliser les paramètres de ligne de commande pour installer Visual Studio

Lorsque vous installez Visual Studio à partir d’une invite de commandes, vous pouvez utiliser divers paramètres de ligne de commande pour contrôler ou personnaliser l’installation. À partir de la ligne de commande, vous pouvez effectuer les actions suivantes :

- Démarrer l’installation avec certaines options présélectionnées.
- Automatiser le processus d’installation.
- Créer un cache (disposition) des fichiers d’installation pour une utilisation ultérieure.

Les options de ligne de commande sont utilisées conjointement avec le programme d’amorçage du programme d’installation, qui est le petit fichier (environ 1 Mo) qui lance le processus de téléchargement. Le programme d’amorçage est le premier exécutable qui est lancé quand vous effectuez un téléchargement à partir du site Visual Studio. Utilisez les liens suivants pour obtenir un lien direct vers le programme d’amorçage de la version la plus récente de l’édition du produit que vous installez :

::: moniker range="vs-2017"

- [Visual Studio Enterprise 2017](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2017)
- [Visual Studio Professional 2017](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2017)
- [Visual Studio Community 2017](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2017)

::: moniker-end

::: moniker range="vs-2019"

- [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)
- [Visual Studio 2019 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)
- [Visual Studio 2019 Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)

::: moniker-end

## <a name="command-line-parameters"></a>Paramètres de ligne de commande

 Les paramètres de ligne de commande Visual Studio ne respectent pas la casse.

> Syntaxe : `vs_enterprise.exe [command] <options>...`

(Remplacez `vs_enterprise.exe` comme il convient pour l’édition du produit que vous installez.)

>[!TIP]
> Pour obtenir des exemples supplémentaires sur l’utilisation de la ligne de commande afin d’installer Visual Studio, consultez la page [Exemples de paramètres de ligne de commande](command-line-parameter-examples.md).

| **Commande** | **Description** |
| ----------------------- | --------------- |
| (vide) | Installe le produit. |
| `modify` | Modifie un produit installé. |
| `update` | Met à jour un produit installé. |
| `repair` | Répare un produit installé. |
| `uninstall` | Désinstalle un produit installé. |
| `export` | **Nouveautés dans la version 15.9** : Exporte la sélection de l’installation dans un fichier de configuration d’installation. **Remarque** : Peut uniquement être utilisé avec vs_installer.exe. |

## <a name="install-options"></a>Options d’installation

| **Option d’installation** | **Description** |
| ----------------------- | --------------- |
| `--installPath <dir>` | Répertoire d’installation de l’instance à installer. Pour la commande d’installation, cette option est **facultative** et il s’agit de l’emplacement où l’instance doit être installée. Pour les autres commandes, cette option est **requise** et il s’agit de l’emplacement où l’instance précédente a été installée. |
| `--addProductLang <language-locale>` | **Facultatif** : Lors d’une installation ou d’une modification, cette option détermine les modules linguistiques de l’interface utilisateur qui sont installés sur le produit. Elle peut apparaître plusieurs fois sur la ligne de commande pour ajouter plusieurs modules linguistiques. Si elle est absente, l’installation utilise les paramètres régionaux de l’ordinateur. Pour plus d’informations, consultez la section [Liste des paramètres régionaux de langue](#list-of-language-locales) de cette page.|
| `--removeProductLang <language-locale>` | **Facultatif** : Lors d’une installation ou d’une modification, cette option détermine les modules linguistiques de l’interface utilisateur qui doivent être supprimés du produit. Elle peut apparaître plusieurs fois sur la ligne de commande pour ajouter plusieurs modules linguistiques. Pour plus d’informations, consultez la section [Liste des paramètres régionaux de langue](#list-of-language-locales) de cette page.|
| `--add <one or more workload or component IDs>` | **Facultatif** : Un ou plusieurs ID de charge de travail ou composant à ajouter. Les composants obligatoires de l’artefact sont installés, mais pas les composants recommandés ni facultatifs. Vous pouvez contrôler globalement les autres composants à l’aide des options `--includeRecommended` et/ou `--includeOptional`. Pour inclure plusieurs charges de travail ou composants, répétez la commande `--add` (par exemple, `--add Workload1 --add Workload2`). Pour un contrôle plus précis, vous pouvez ajouter `;includeRecommended` ou `;includeOptional` à l’ID (par exemple, `--add Workload1;includeRecommended` ou `--add Workload2;includeRecommended;includeOptional`). Pour plus d’informations, consultez la page [ID de charge de travail et de composant](workload-and-component-ids.md). Vous pouvez répéter cette option si nécessaire.|
| `--remove <one or more workload or component IDs>` | **Facultatif** : Un ou plusieurs ID de charge de travail ou composant à supprimer. Pour plus d’informations, consultez notre page [ID de charge de travail et de composant](workload-and-component-ids.md). Vous pouvez répéter cette option si nécessaire.|
| `--in <path>` | **Facultatif** : URI ou chemin d’un fichier réponse.  |
| `--all` | **Facultatif** : Indique s’il faut installer tous les composants et charges de travail d’un produit. |
| `--allWorkloads` | **Facultatif** : Installe toutes les charges de travail et tous les composants, mais n’installe pas les composants recommandés ou facultatifs. |
| `--includeRecommended` | **Facultatif** : Inclut les composants recommandés pour toutes les charges de travail installées, mais pas les composants facultatifs. Les charges de travail sont spécifiées avec `--allWorkloads` ou `--add`. |
| `--includeOptional` | **Facultatif** : Inclut les composants facultatifs pour toutes les charges de travail installées, mais pas les composants recommandés. Les charges de travail sont spécifiées avec `--allWorkloads` ou `--add`.  |
| `--quiet, -q` | **Facultatif** : Ne pas afficher l’interface utilisateur pendant l’installation. |
| `--passive, -p` | **Facultatif** : Afficher l’interface utilisateur, mais ne pas demander d’intervention de l’utilisateur. |
| `--norestart` | **Facultatif** : Les commandes avec `--passive` ou `--quiet` ne redémarrent pas automatiquement la machine (si nécessaire).  Option ignorée si ni `--passive` ni `--quiet` ne sont spécifiés.  |
| `--nickname <name>` | **Facultatif** : Définit le surnom à attribuer à un produit installé. La longueur du surnom ne peut pas dépasser 10 caractères.  |
| `--productKey` | **Facultatif** : Définit la clé de produit à utiliser pour un produit installé. Elle est composée de 25 caractères alphanumériques au format `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` ou `xxxxxxxxxxxxxxxxxxxxxxxxx`. |
| `--help, --?, -h, -?` | Permet d’afficher une version hors connexion de cette page. |
| `--config <path>` | **Facultatif** et **nouveautés de la version 15.9** : Pendant une opération d’installation ou de modification, cette option détermine les charges de travail et composants à ajouter en fonction d’un fichier de configuration d’installation déjà enregistré. Cette opération étant additive, elle ne supprime aucune charge de travail ou composant ne figurant pas dans le fichier. De plus, les éléments qui ne s’appliquent pas au produit ne sont pas ajoutés. Pendant une opération d’exportation, cette option détermine l’emplacement auquel enregistrer le fichier de configuration d’installation. |

> [!IMPORTANT]
> Lorsque vous spécifiez plusieurs charges de travail et plusieurs composants, vous devez répéter le commutateur de ligne de commande `--add` ou `--remove` pour chaque élément.

## <a name="layout-options"></a>Options de disposition

| **Options de disposition** | **Description** |
| ----------------------- | --------------- |
| `--layout <dir>` | Spécifie un répertoire pour créer un cache d’installation hors connexion. Pour plus d’informations, consultez [Créer une installation réseau de Visual Studio](create-a-network-installation-of-visual-studio.md).|
| `--lang <one or more language-locales>` | **Facultatif** : Utilisé avec `--layout` pour préparer un cache d’installation hors connexion avec des packages de ressources correspondant à la langue ou aux langues spécifiées. Pour plus d’informations, consultez la section [Liste des paramètres régionaux de langue](#list-of-language-locales) de cette page.|
| `--add <one or more workload or component IDs>` | **Facultatif** : Un ou plusieurs ID de charge de travail ou composant à ajouter. Les composants obligatoires de l’artefact sont installés, mais pas les composants recommandés ni facultatifs. Vous pouvez contrôler globalement les autres composants à l’aide des options `--includeRecommended` et/ou `--includeOptional`. Pour un contrôle plus précis, vous pouvez ajouter `;includeRecommended` ou `;includeOptional` à l’ID (par exemple, `--add Workload1;includeRecommended` ou `--add Workload2;includeOptional`). Pour plus d’informations, consultez la page [ID de charge de travail et de composant](workload-and-component-ids.md). <br/>**Remarque** : Si `--add` est utilisé, seuls les composants et les charges de travail spécifiés ainsi que leurs dépendances sont téléchargés. Si `--add` n’est pas spécifié, l’ensemble des charges de travail et des composants est téléchargé sur la disposition.|
| `--includeRecommended` | **Facultatif** : Inclut les composants recommandés pour toutes les charges de travail installées, mais pas les composants facultatifs. Les charges de travail sont spécifiées avec `--allWorkloads` ou `--add`. |
| `--includeOptional` | **Facultatif** : Inclut les composants recommandés *et* facultatifs pour toutes les charges de travail contenues dans la disposition. Les charges de travail sont spécifiées avec `--add`.  |
| `--keepLayoutVersion` | **Nouveautés de la version 15.3, facultatif** : Application des modifications à la disposition sans mettre à jour la version de la disposition. |
| `--verify` | **Nouveautés de la version 15.3, facultatif** : Vérification du contenu d’une disposition. Tous les fichiers endommagés ou manquants sont listés. |
| `--fix` | **Nouveautés de la version 15.3, facultatif** : Vérification du contenu d’une disposition.  Si des fichiers sont endommagés ou manquants, ils sont retéléchargés. Un accès à Internet est obligatoire pour corriger une disposition. |
| `--clean <one or more paths to catalogs>` | **Nouveautés de la version 15.3, facultatif** : Suppression des anciennes versions des composants d’une disposition qui a été mise à jour vers une version plus récente. |

| **Options d’installation avancées** | **Description** |
| ----------------------- | --------------- |
| `--channelId <id>` | **Facultatif** : ID de canal pour l’instance à installer. Cette option est requise pour la commande d’installation, ignorée pour les autres commandes si `--installPath` est spécifié. |
| `--channelUri <uri>` | **Facultatif** : URI du manifeste de canal. Si les mises à jour ne sont pas souhaitées, `--channelUri` peut pointer vers un fichier non existant. (par exemple, --channelUri C:\doesntExist.chman). Cette option peut être utilisée pour la commande d’installation. Elle est ignorée pour les autres commandes. |
| `--installChannelUri <uri>` | **Facultatif** : URI du manifeste de canal à utiliser pour l’installation. L’URI spécifié par `--channelUri` (qui doit être spécifié en même temps que `--installChannelUri`) est utilisé pour détecter les mises à jour. Cette option peut être utilisée pour la commande d’installation. Elle est ignorée pour les autres commandes. |
| `--installCatalogUri <uri>` | **Facultatif** : URI du manifeste de catalogue à utiliser pour l’installation. Si spécifié, le gestionnaire de canal tente de télécharger le manifeste de catalogue à partir de cet URI avant d’utiliser l’URI du manifeste de canal d’installation. Ce paramètre est utilisé pour prendre en charge l’installation hors connexion, où le cache de disposition est créé avec le catalogue de produits déjà téléchargé. Cette option peut être utilisée pour la commande d’installation. Elle est ignorée pour les autres commandes. |
| `--productId <id>` | **Facultatif** : ID de produit pour l’instance à installer. Ce champ est prérempli dans des conditions d’installation normale. |
| `--wait` | **Facultatif** : Le processus attend la fin de l’installation pour retourner un code de sortie. Cela est utile lorsque vous automatisez des installations et que vous devez attendre la fin de l’installation pour gérer le code de retour de cette installation. |
| `--locale <language-locale>` | **Facultatif** : Changer la langue d’affichage de l’interface utilisateur pour le programme d’installation proprement dit. Ce paramètre est conservé. Pour plus d’informations, consultez la section [Liste des paramètres régionaux de langue](#list-of-language-locales) de cette page.|
| `--cache` | **Nouveautés de la version 15.2, facultatif** : Le cas échéant, les packages sont conservés après leur installation pour les réparations ultérieures. Cela remplace le paramètre de stratégie globale à utiliser pour les installations, réparations ou modifications ultérieures. La stratégie par défaut consiste à mettre les packages en cache. Option ignorée pour la commande de désinstallation. Pour plus d’informations, consultez [Désactiver ou déplacer le cache du package](disable-or-move-the-package-cache.md). |
| `--nocache` | **Nouveautés de la version 15.2, facultatif** : Le cas échéant, les packages sont supprimés après avoir été installés ou réparés. Ils seront à nouveau téléchargés uniquement si nécessaire et à nouveau supprimés après utilisation. Cela remplace le paramètre de stratégie globale à utiliser pour les installations, réparations ou modifications ultérieures. La stratégie par défaut consiste à mettre les packages en cache. Option ignorée pour la commande de désinstallation. Pour plus d’informations, consultez [Désactiver ou déplacer le cache du package](disable-or-move-the-package-cache.md). |
| `--noUpdateInstaller` | **Nouveautés de la version 15.2, facultatif** : Le cas échéant, empêche la mise à jour du programme d’installation quand le mode silencieux est spécifié. Le programme d’installation ne parvient pas à exécuter la commande et retourne un code de sortie différent de zéro si noUpdateInstaller est spécifié avec le mode silencieux quand une mise à jour du programme d’installation est obligatoire. |
| `--noWeb` | **Nouveautés de la version 15.3, facultatif** : S’il est présent, le programme d’installation de Visual Studio utilise les fichiers dans votre répertoire de disposition pour installer Visual Studio. Si un utilisateur tente d’installer des composants qui ne sont pas dans la disposition, le programme d’installation échoue.  Pour plus d’informations, consultez [Déploiement à partir d’une installation réseau](create-a-network-installation-of-visual-studio.md). <br/><br/> **Important** : Cela n’empêche pas le programme d’installation de Visual Studio de vérifier la présence de mises à jour. Pour plus d’informations, consultez [Contrôler les mises à jour applicables aux déploiements de Visual Studio à partir du réseau](controlling-updates-to-visual-studio-deployments.md).|
| `--path <name>=<path>` | **Nouveautés de la version 15.7, facultatif** : Permet de spécifier des chemins d’installation personnalisés pour l’installation. Les noms de chemin pris en charge sont shared, cache et install. |
| `--path cache=<path>` | **Nouveautés de la version 15.7, facultatif** : Utilise l’emplacement que vous spécifiez pour télécharger les fichiers d’installation. Cet emplacement peut être défini uniquement pendant la première installation de Visual Studio. Exemple : `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **Nouveautés de la version 15.7, facultatif** : Contient des fichiers partagés pour les installations de Visual Studio côte à côte. Certains outils et kits SDK effectuent l’installation à un emplacement sur ce lecteur, tandis que d’autres peuvent l’effectuer sur un autre lecteur en passant outre ce paramétrage. Exemple : `--path shared="C:\VS\shared"` <br><br>Important : Ceci ne peut être défini qu’une seule fois, lors de la première installation de Visual Studio. |
| `--path install=<path>` | **Nouveautés de la version 15.7, facultatif** : Équivalent à `–-installPath`. En particulier, les options `--installPath "C:\VS"` et `--path install="C:\VS"` sont équivalentes. Seule une des deux options peut être utilisée à la fois. |

## <a name="list-of-workload-ids-and-component-ids"></a>Liste des ID de charge de travail et de composant

Pour obtenir la liste des ID de charge de travail et de composant triés par produit Visual Studio, consultez la page [ID de charge de travail et de composant Visual Studio](workload-and-component-ids.md).

## <a name="list-of-language-locales"></a>Liste des paramètres régionaux de langue

| **Paramètres régionaux de langue** | **Language** |
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
| Pt-br | Portugais - Brésil |
| Ru-ru | Russe |
| Tr-tr | Turc |
| Zh-cn | Chinois (simplifié) |
| Zh-tw | Chinois (traditionnel) |

## <a name="error-codes"></a>Codes d’erreur

En fonction du résultat de l’opération, la variable d’environnement `%ERRORLEVEL%` a l’une des valeurs suivantes :

| **Valeur** | **Résultat** |
| --------- | ---------- |
| 0 | Opération effectuée avec succès |
| 1602 | Opération annulée |
| 3010 | Opération effectuée avec succès, mais l’installation nécessite un redémarrage avant de pouvoir être utilisée |
| 5004 | Opération annulée |
| 5007 | L’opération a été bloquée - l’ordinateur ne répond pas à la configuration requise |
| Autre | Une condition d’échec s’est produite - Pour plus d’informations, consultez les journaux |

Chaque opération génère plusieurs fichiers journaux dans le répertoire `%TEMP%`, qui indiquent la progression de l’installation. Triez le dossier par date et recherchez les fichiers commençant par `dd_bootstrapper`, `dd_client` et `dd_setup` pour le programme d’amorçage, l’application du programme d’installation et le moteur d’installation, respectivement.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

- [Exemples de paramètres de ligne de commande pour l’installation de Visual Studio](command-line-parameter-examples.md)
- [Créer une installation hors connexion de Visual Studio](create-an-offline-installation-of-visual-studio.md)
- [Automatiser l’installation de Visual Studio avec un fichier réponse](automated-installation-with-response-file.md)
- [ID de charge de travail et de composant Visual Studio](workload-and-component-ids.md)
