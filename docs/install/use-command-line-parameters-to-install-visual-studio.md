---
title: "Utiliser les paramètres de ligne de commande pour installer Visual Studio │ Microsoft Docs"
ms.custom: 
ms.date: 05/06/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: 90e19f6e693733162065754b441fb213fd0bd9f8
ms.contentlocale: fr-fr
ms.lasthandoff: 07/18/2017

---
# <a name="use-command-line-parameters-to-install-visual-studio-2017"></a>Utiliser les paramètres de ligne de commande pour installer Visual Studio 2017
Quand vous installez Visual Studio 2017 à partir d’une invite de commandes, vous pouvez utiliser divers paramètres de ligne de commande pour contrôler ou personnaliser l’installation. À partir de la ligne de commande, vous pouvez effectuer les tâches suivantes :

- Démarrer l’installation avec certaines options présélectionnées.
- Automatiser le processus d’installation.
- Créer un cache (disposition) des fichiers d’installation pour une utilisation ultérieure.

Les options de ligne de commande sont utilisées conjointement avec le programme d’amorçage du programme d’installation, qui est le petit fichier (environ 1 Mo) qui lance le processus de téléchargement. Le programme d’amorçage est le premier exécutable qui est lancé quand vous effectuez un téléchargement à partir du site Visual Studio. Vous pouvez obtenir un lien direct vers le programme d’amorçage de la version la plus récente de l’édition du produit que vous installez à partir des liens suivants :

* [Visual Studio Enterprise 2017](https://aka.ms/vs/15/release/vs_enterprise.exe)
* [Visual Studio Professional 2017](https://aka.ms/vs/15/release/vs_professional.exe)
* [Visual Studio Community 2017](https://aka.ms/vs/15/release/vs_community.exe)

## <a name="list-of-command-line-parameters"></a>Liste des paramètres de ligne de commande  
 Les paramètres de ligne de commande Visual Studio ne respectent pas la casse.

> Syntaxe : `vs_enterprise.exe [command] <options>...`

(Remplacez `vs_enterprise.exe` comme il convient pour l’édition du produit que vous installez. Pour obtenir des exemples, consultez la page [Exemples de paramètres de ligne de commande](command-line-parameter-examples.md).)

| **Commande** | **Description** |
| ----------------------- | --------------- |
| (vide) | Installe le produit. |
| `modify` | Modifie un produit installé. |
| `update` | Met à jour un produit installé. |
| `repair` | Répare un produit installé. |
| `uninstall` | Désinstalle un produit installé. |

| **Option d’installation** | **Description** |
| ----------------------- | --------------- |
| `--installPath <dir>` | Répertoire d’installation de l’instance à installer. Pour la commande d’installation, cette option est **facultative** et il s’agit de l’emplacement où l’instance doit être installée. Pour les autres commandes, cette option est **requise** et il s’agit de l’emplacement où l’instance précédente a été installée. |
| `--addProductLang <language-locale>` | **Facultatif** : lors d’une installation ou d’une modification, cette option détermine les modules linguistiques de l’interface utilisateur qui doivent être installés pour le produit. Elle peut apparaître plusieurs fois sur la ligne de commande pour ajouter plusieurs modules linguistiques. Si elle est absente, l’installation utilise les paramètres régionaux de l’ordinateur. Pour plus d’informations, consultez la section [Liste des paramètres régionaux de langue](#list-of-language-locales) de cette page.|
| `--removeProductLang <language-locale>` | **Facultatif** : lors d’une installation ou d’une modification, cette option détermine les modules linguistiques de l’interface utilisateur qui doivent être supprimés du produit. Elle peut apparaître plusieurs fois sur la ligne de commande pour ajouter plusieurs modules linguistiques. Pour plus d’informations, consultez la section [Liste des paramètres régionaux de langue](#list-of-language-locales) de cette page.|
| `--add <workload or component ID>` | **Facultatif** : ID de charge de travail ou de composant à ajouter. Les composants obligatoires de l’artefact sont installés, mais pas les composants recommandés ni facultatifs. Vous pouvez contrôler globalement les autres composants à l’aide des options `--includeRecommended` et/ou `--includeOptional`. Pour un contrôle plus précis, vous pouvez ajouter `;includeRecommended` ou `;includeOptional` à l’ID (par exemple, `--add Workload1;includeRecommended` ou `--add Workload2;includeRecommended;includeOptional`). Pour plus d’informations, consultez notre page [ID de charge de travail et de composant](workload-and-component-ids.md). Vous pouvez répéter cette option si nécessaire.|
| `--remove <workload or component ID>` | **Facultatif** : ID de charge de travail ou de composant à supprimer. Pour plus d’informations, consultez notre page [ID de charge de travail et de composant](workload-and-component-ids.md). Vous pouvez répéter cette option si nécessaire.|
| `--in <path>` | **Facultatif** : URI ou chemin d’un fichier réponse.  |
| `--all` | **Facultatif** : indique s’il faut installer tous les composants et charges de travail d’un produit. |
| `--allWorkloads` | **Facultatif** : installe toutes les charges de travail et leurs composants obligatoires, mais n’installe pas les composants recommandés et facultatifs. |
| `--includeRecommended` | **Facultatif** : inclut les composants recommandés pour toutes les charges de travail installées, mais pas les composants facultatifs. Les charges de travail sont spécifiées avec `--allWorkloads` ou `--add`. |
| `--includeOptional` | **Facultatif** : inclut les composants facultatifs pour toutes les charges de travail installées, mais pas les composants recommandés. Les charges de travail sont spécifiées avec `--allWorkloads` ou `--add`.  |
| `--quiet, -q` | **Facultatif** : ne pas afficher l’interface utilisateur pendant l’installation. |
| `--passive, -p` | **Facultatif** : afficher l’interface utilisateur, mais ne pas demander d’intervention de l’utilisateur. |
| `--norestart` | **Facultatif** : les commandes avec `--passive` ou `--quiet` ne redémarrent pas automatiquement l’ordinateur (si nécessaire). Option ignorée si ni `--passive` ni `--quiet` ne sont spécifiés.  |
| `--nickname <name>` | **Facultatif** : définit le surnom à attribuer à un produit installé. La longueur du surnom ne peut pas dépasser 10 caractères.  |
| `--productKey` | **Facultatif** : définit la clé de produit à utiliser pour un produit installé. Elle est composée de 25 caractères alphanumériques au format `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` ou `xxxxxxxxxxxxxxxxxxxxxxxxx`. |
| `--help, --?, -h, -?` | Permet d’afficher une version hors connexion de cette page. |

> Remarque : Lorsque vous spécifiez plusieurs charges de travail et plusieurs composants, vous devez répéter le commutateur de ligne de commande `--add` ou `--remove` pour chaque élément.

| **Options de disposition** | **Description** |
| ----------------------- | --------------- |
| `--layout <dir>` | Spécifie un répertoire pour créer un cache d’installation hors connexion. Pour plus d’informations, consultez [Créer une installation réseau de Visual Studio](create-a-network-installation-of-visual-studio.md).|
| `--lang <one or more language-locales>` | **Facultatif** : utilisé avec `--layout` pour préparer un cache d’installation hors connexion avec des packages de ressources correspondant à la langue ou aux langues spécifiées. Pour plus d’informations, consultez la section [Liste des paramètres régionaux de langue](#list-of-language-locales) de cette page.|
| `--add <one or more workload or component IDs>` | **Facultatif** : un ou plusieurs ID de charge de travail ou composant à ajouter. Les composants obligatoires de l’artefact sont installés, mais pas les composants recommandés ni facultatifs. Vous pouvez contrôler globalement les autres composants à l’aide des options `--includeRecommended` et/ou `--includeOptional`. Pour un contrôle plus précis, vous pouvez ajouter `;includeRecommended` ou `;includeOptional` à l’ID (par exemple, `--add Workload1;includeRecommended` ou `--add Workload2;includeOptional`). Pour plus d’informations, consultez notre page [ID de charge de travail et de composant](workload-and-component-ids.md). <br/>**Remarque** : Si `--add` est utilisé, seuls les composants et les charges de travail spécifiés ainsi que leurs dépendances sont téléchargés. Si `--add` n’est pas spécifié, l’ensemble des charges de travail et composants est téléchargé sur la disposition.|
| `--includeRecommended` | **Facultatif** : inclut les composants recommandés pour toutes les charges de travail installées, mais pas les composants facultatifs. Les charges de travail sont spécifiées avec `--allWorkloads` ou `--add`. |
| `--includeOptional` | **Facultatif** : inclut les composants recommandés *et* facultatifs pour toutes les charges de travail contenues dans la disposition. Les charges de travail sont spécifiées avec `--add`.  |


| **Options d’installation avancées** | **Description** |
| ----------------------- | --------------- |
| `--channelId <id>` | **Facultatif** : ID de canal pour l’instance à installer. Cette option est requise pour la commande d’installation, ignorée pour les autres commandes si `--installPath` est spécifié. |
| `--channelUri <uri>` | **Facultatif** : URI du manifeste de canal. Cette option peut être utilisée pour la commande d’installation. Elle est ignorée pour les autres commandes. |
| `--installChannelUri <uri>` | **Facultatif** : URI du manifeste de canal à utiliser pour l’installation. L’URI spécifié par `--channelUri` (qui doit être spécifié en même temps que `--installChannelUri`) est utilisé pour détecter les mises à jour. Si les mises à jour ne sont pas souhaitées, vous devez spécifier `--channelUri` sans argument. Cette option peut être utilisée pour la commande d’installation. Elle est ignorée pour les autres commandes. |
| `--installCatalogUri <uri>` | **Facultatif** : URI du manifeste de catalogue à utiliser pour l’installation. Si spécifié, le gestionnaire de canal va tenter de télécharger le manifeste de catalogue à partir de cet URI avant d’utiliser l’URI du manifeste de canal d’installation. Ce paramètre est utilisé pour prendre en charge l’installation hors connexion, où le cache de disposition est créé avec le catalogue de produits déjà téléchargé. Cette option peut être utilisée pour la commande d’installation. Elle est ignorée pour les autres commandes. |
| `--productId <id>` | **Facultatif** : ID de produit pour l’instance à installer. Ce champ est prérempli dans des conditions d’installation normale. |
| `--wait` | **Facultatif** : le processus attend la fin de l’installation pour retourner du code de sortie. Cela est utile lorsque vous automatisez des installations et que vous devez attendre la fin de l’installation pour gérer le code de retour de cette installation. |
| `--locale <language-locale>` | **Facultatif** : permet de changer la langue d’affichage de l’interface utilisateur pour le programme d’installation proprement dit. Ce paramètre est conservé. Pour plus d’informations, consultez la section [Liste des paramètres régionaux de langue](#list-of-language-locales) de cette page.|
| `--cache` | **Nouveauté de la version 15.2, facultatif** : le cas échéant, les packages sont conservés après leur installation pour les réparations ultérieures. Cela remplace le paramètre de stratégie globale à utiliser pour les installations, réparations ou modifications ultérieures. La stratégie par défaut consiste à mettre les packages en cache. Option ignorée pour la commande de désinstallation. Pour plus d’informations, consultez [Désactiver ou déplacer le cache du package](disable-or-move-the-package-cache.md). |
| `--nocache` | **Nouveauté de la version 15.2, facultatif** : le cas échéant, les packages sont supprimés après avoir été installés ou réparés. Ils seront à nouveau téléchargés uniquement si nécessaire et à nouveau supprimés après utilisation. Cela remplace le paramètre de stratégie globale à utiliser pour les installations, réparations ou modifications ultérieures. La stratégie par défaut consiste à mettre les packages en cache. Option ignorée pour la commande de désinstallation. Pour plus d’informations, consultez [Désactiver ou déplacer le cache du package](disable-or-move-the-package-cache.md). |

## <a name="list-of-workload-ids-and-component-ids"></a>Liste des ID de charge de travail et de composant
Pour obtenir la liste des ID de charge de travail et de composant triés par produit Visual Studio, consultez la page [ID de charge de travail et de composant Visual Studio 2017](workload-and-component-ids.md).

## <a name="list-of-language-locales"></a>Liste des paramètres régionaux de langue
| **Paramètres régionaux de langue** | **Langue** |
| ----------------------- | --------------- |
| cs-CZ | Tchèque |
| de-DE | Allemand |
| en-US | Anglais |
| es-ES | Espagnol |
| fr-FR | Français |
| it-IT | Italien |
| ja-JP | Japonais |
| ko-KR | Coréen |
| pl-PL | Polonais |
| pt-BR | Portugais - Brésil |
| ru-RU | Russe |
| tr-TR | Turc |
| zh-CN | Chinois (simplifié) |
| zh-TW | Chinois (traditionnel) |

## <a name="error-codes"></a>Codes d’erreur
En fonction du résultat de l’opération, la variable d’environnement `%ERRORLEVEL%` a l’une des valeurs suivantes :

| **Valeur** | **Résultat** |
| --------- | ---------- |
| 0 | Opération effectuée avec succès |
| 3010 | Opération effectuée avec succès, mais l’installation nécessite un redémarrage avant de pouvoir être utilisée |
| Autre | Une condition d’échec s’est produite - Pour plus d’informations, consultez les journaux |

Chaque opération génère, dans le répertoire `%TEMP%`, plusieurs fichiers journaux qui indiquent la progression de l’installation. Triez le dossier par date et recherchez les fichiers commençant par `dd_bootstrapper`, `dd_client` et `dd_setup` pour le programme d’amorçage, l’application du programme d’installation et le moteur d’installation, respectivement.

## <a name="see-also"></a>Voir aussi

 * [Installer Visual Studio 2017](install-visual-studio.md)
 * [Créer une installation hors connexion de Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
 * [Exemples de paramètres de ligne de commande pour l’installation de Visual Studio 2017](command-line-parameter-examples.md)
 * [Automatiser l’installation de Visual Studio avec un fichier réponse](automated-installation-with-response-file.md)
 * [Signaler un problème avec Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

