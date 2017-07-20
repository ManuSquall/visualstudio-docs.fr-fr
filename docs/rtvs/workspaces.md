---
title: "Espaces de travail dans les Outils R pour Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 4/27/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d610279c-d6c3-4084-939a-bf042f64d4dd
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 8ac025a9da5c07cbc9efff416d07c93b91aa2c14
ms.contentlocale: fr-fr
ms.lasthandoff: 05/12/2017

---


## <a name="controlling-where-r-code-runs-with-workspaces"></a>Décider où s’exécute le code R avec des espaces de travail

Un espace de travail dans les Outils R pour Visual Studio (RTVS) vous permet de configurer où s’exécute une session R, c’est-à-dire sur des ordinateurs locaux ou distants. L’objectif est de vous permettre d’utiliser les deux avec une expérience utilisateur comparable afin que vous puissiez tirer parti d’ordinateurs basés sur le cloud potentiellement plus puissants.

Pour ouvrir la fenêtre **Espaces de travail**, utilisez la commande **Outils R > Fenêtres > Espaces de travail** ou appuyez sur Ctrl+9.

![Fenêtre Espaces de travail dans les Outils R pour Visual Studio (VS2017)](media/workspaces-window.png)

Dans cette fenêtre, la coche verte indique l’espace de travail actif auquel RTVS est lié. Vous définissez l’espace de travail actif en sélectionnant une flèche bleue. L’icône de paramètres (engrenage) à droite de chaque espace de travail vous permet de changer son nom, son emplacement et ses arguments de ligne de commande. Le X rouge supprime un espace de travail ajouté manuellement.

Dans cette rubrique :

- [Enregistrement et réinitialisation d’un espace de travail](#saving-and-resetting-a-workspace)
- [Espaces de travail locaux](#local-workspaces)
- [Espaces de travail distants](#remote-workspaces)
- [Basculement entre espaces de travail](#switching-between-workspaces)
- [Répertoires sur des ordinateurs locaux et distants](#directories-on-local-and-remote-computers)
- [Copie de fichiers projet dans des espaces de travail distants](#copying-project-files-to-remote-workspaces)
- [Copie de fichiers à partir d’un espace de travail distant](#copying-files-from-a-remote-workspace)

## <a name="saving-and-resetting-a-workspace"></a>Enregistrement et réinitialisation d’un espace de travail

Par défaut, RTVS n’enregistre pas l’état de l’espace de travail quand vous fermez et rouvrez un projet. Vous pouvez changer ce comportement dans les [Options d’espace de travail](options.md#workspace).

La commande **Outils R > Session > Réinitialiser** et le bouton de réinitialisation sur la barre d’outils de la fenêtre interactive réinitialisent également l’état de l’espace de travail à tout moment. Dans le cas d’espaces de travail distants, une réinitialisation a pour effet de supprimer le profil utilisateur créé lors de la première connexion au serveur distant, ce qui supprime tous les fichiers stockés à cet endroit.

## <a name="local-workspaces"></a>Espaces de travail locaux

La liste des espaces de travail locaux affiche tous les interpréteurs R que vous avez installés sur votre ordinateur. 

RTVS essaie de détecter automatiquement toutes les versions de R que vous avez installées en examinant la clé de Registre `HKEY_LOCAL_MACHINE\Software\R-Core\` au démarrage de Visual Studio. Comme cette vérification est effectuée uniquement au démarrage, vous devez redémarrer Visual Studio si vous installez un nouvel interpréteur R.

RTVS peut ne pas détecter un interpréteur R installé de manière non standard (par exemple, quand vous copiez simplement des fichiers dans un dossier au lieu d’exécuter un programme d’installation). Dans ce cas, créez manuellement un nouvel espace de travail R local comme suit :

1. Sélectionnez le bouton **Ajouter** dans la fenêtre Espaces de travail.
1. Entrez un nom pour le nouvel espace de travail.
1. Entrez le chemin du dossier racine R, qui est celui qui contient le dossier `bin` avec l’interpréteur, et les arguments de ligne de commande facultatifs à passer à l’interpréteur au démarrage de RTVS.
1. Sélectionnez **Enregistrer** quand vous avez terminé.

![Ajout d’un nouvel espace de travail](media/workspaces-add-new.png)

## <a name="remote-workspaces"></a>Espaces de travail distants

Les espaces de travail distants vous permettent de vous connecter à une session R sur un ordinateur distant. (Consultez [Configuration des espaces de travail distants](workspaces-remote-setup.md) pour savoir comment configurer un ordinateur dans ce but.)

Les espaces de travail distants ne sont pas détectés automatiquement par RTVS, donc vous devez les ajouter manuellement à l’aide du bouton **Ajouter** dans la fenêtre Espaces de travail, comme décrit dans la section précédente. Dans ce cas, entrez l’URI de l’ordinateur distant au lieu d’un chemin local.

> [!Important]
> Les espaces de travail distants sont identifiés par un URI qui *doit utiliser le protocole HTTPS* pour garantir la confidentialité et l’intégrité de la communication avec l’ordinateur distant. RTVS ne se connecte pas à un ordinateur distant qui ne prend pas en charge le protocole HTTPS.

> [!Note]
> Les espaces de travail distants sont en préversion. Nous travaillons à une meilleure implémentation du problème de synchronisation des fichiers dans une version future et nous sommes à l’écoute de vos suggestions ou commentaires pour vous offrir une meilleure expérience.


## <a name="switching-between-workspaces"></a>Basculement entre espaces de travail

RTVS est lié à un seul espace de travail à la fois, ce qui est indiqué par une petite coche verte à côté de l’espace de travail dans la fenêtre Espaces de travail. Par défaut, RTVS est lié au dernier espace de travail local que vous avez ouvert dans la session précédente.

Pour changer l’espace de travail actif, sélectionnez la flèche bleue à côté de l’espace de travail de votre choix. Vous êtes alors invité à enregistrer votre session, l’espace de travail actuel se ferme et vous basculez sur le nouvel espace de travail.

> [!Tip]
> Pour désactiver l’invite d’enregistrement, sélectionnez la commande **Outils R > Options** et définissez l’option **Afficher la boîte de dialogue de confirmation avant de changer d’espace de travail** sur `No`. Consultez [Options de l’espace de travail](options.md#workspace).

Si vous essayez de basculer sur un espace de travail local qui a été désinstallé ou sur un espace de travail distant non disponible, vous pouvez vous retrouver avec un projet RTVS qui n’est lié à aucun espace de travail. Par conséquent, vous pouvez obtenir une erreur comme celle indiquée ci-dessous quand vous entrez du code dans la fenêtre interactive ou que vous tentez d’exécuter le code d’une autre façon. Pour corriger ce problème, basculez simplement sur un autre espace de travail dans la fenêtre Espaces de travail. Si aucun espace de travail n’est disponible, vous devez installer un interpréteur R. Vous pouvez également essayer de redémarrer Visual Studio si vous avez installé un interpréteur quand Visual Studio était déjà en cours d’exécution.

![Erreur quand aucun espace de travail n’est lié à RTVS](media/workspaces-disconnected-interactive-window.png)

### <a name="switching-to-a-remote-workspace"></a>Basculement sur un espace de travail distant

RTVS vous demande vos informations d’identification quand vous vous connectez pour la première fois à un espace de travail distant, puis met en cache ces informations d’identification (à l’aide du stockage sécurisé des informations d’identification de Windows) pour les sessions ultérieures. La communication avec le serveur distant est ensuite établie en toute sécurité sur HTTPS (ce qui est obligatoire).

Selon la configuration du serveur, vous pouvez obtenir un avertissement de certificat à la connexion : « Le certificat de sécurité présenté par le serveur Remote R Services ne nous permet pas de prouver que vous êtes en train de vous connecter à l’ordinateur (nom). ».

![Avertissement du certificat auto-signé lors de la connexion à un espace de travail distant](media/workspaces-remote-self-signed-certificate-warning.png)

Le certificat est un document présenté à RTVS par l’ordinateur auquel vous essayez de vous connecter, qui contient un champ permettant d’identifier l’URI de l’ordinateur. L’avertissement s’affiche quand RTVS détecte une incompatibilité entre l’URI du certificat et l’URI utilisé pour se connecter à l’ordinateur, ce qui indique que la sécurité du serveur est peut-être compromise.

Toutefois, cet avertissement s’affiche également si un *certificat auto-signé* a été utilisé pour activer HTTPS sur l’ordinateur distant au lieu d’en utiliser un d’un fournisseur approuvé. Pour plus d’informations, consultez [Configuration des espaces de travail distants](workspaces-remote-setup.md).

## <a name="directories-on-local-and-remote-computers"></a>Répertoires sur des ordinateurs locaux et distants

Par défaut, quand vous démarrez un nouvel interpréteur R dans un espace de travail local, votre répertoire de travail actuel est `%userprofile%\Documents`. Vous pouvez le changer à tout moment à l’aide des commandes **Outils R > Répertoire de travail** ou en cliquant avec le bouton droit sur un projet dans l’Explorateur de solutions Visual Studio et en sélectionnant des commandes de type **Définir le répertoire de travail ici**.

Sur les ordinateurs distants, RTVS crée automatiquement un profil utilisateur d’après les informations d’identification entrées lors de votre première connexion au serveur, le répertoire de travail est donc le dossier `Documents` sous ce profil. Il est utilisé pour toutes les sessions à distance suivantes qui utilisent les mêmes informations d’identification. 

Par conséquent, l’endroit exact où s’exécute votre code peut différer entre les espaces de travail locaux et distants. Évitez d’utiliser des chemins absolus vers des fichiers de données dans votre code, car celui-ci n’est probablement pas portable entre les espaces de travail. Utilisez plutôt des chemins relatifs.

Notez également qu’avec les espaces de travail distants, tous les fichiers du répertoire de travail restent en place entre les sessions pour le même profil utilisateur. Comme indiqué précédemment, vous pouvez les supprimer en utilisant la commande **Outils R > Session > Réinitialiser** (ou le bouton de réinitialisation dans la fenêtre interactive) lors de l’utilisation d’un espace de travail distant. Cette opération supprime à nouveau le profil utilisateur du serveur, qui est recréé quand vous vous reconnectez.

## <a name="copying-project-files-to-remote-workspaces"></a>Copie de fichiers projet dans des espaces de travail distants

Quand vous utilisez des projets R dans Visual Studio, l’ordinateur local a toujours les derniers fichiers projet, même quand vous utilisez un espace de travail distant. Autrement dit, quand vous ouvrez un projet dans Visual Studio (ce qui implique généralement l’ouverture d’une solution contenant ce projet), RTVS suppose que le contenu du projet réside entièrement sur l’ordinateur local. L’espace de travail distant est, en fait, un simple hôte temporaire pour les fichiers du projet et toutes les sorties du code. Cela signifie, par exemple, que lors du chargement d’un fichier à l’aide de `source` dans la fenêtre interactive, ce fichier doit déjà être sur l’ordinateur distant dans le chemin que vous fournissez ou dans le répertoire de travail actuel de l’interpréteur R distant (défini avec la fonction `setwd()`).

Les fichiers sont copiés sur le serveur distant comme suit :

- Pour utiliser des fichiers à distance par le biais de la fenêtre interactive, vous devez d’abord les copier manuellement en cliquant dessus avec le bouton droit (ou sur le projet) dans l’Explorateur de solutions et en sélectionnant **Source sélectionnée**. Les fichiers individuels sont copiés dans le répertoire de travail sur le serveur. Quand vous copiez un projet, RTVS crée un dossier pour le projet.

- Vous pouvez également copier des fichiers en les sélectionnant dans l’Explorateur de solutions, puis en sélectionnant **Approvisionner les fichier(s) sélectionné(s)**. Les fichiers sont chargés dans la fenêtre interactive où ils sont exécutés. Si la session est connectée à un ordinateur distant, les fichiers y sont d’abord copiés.

- Quand RTVS est lié à un espace de travail distant et que vous appuyez sur F5, sélectionnez **Déboguer > Démarrer le débogage** ou démarrez l’exécution de votre code, RTVS copie automatiquement par défaut le fichier du projet dans l’espace de travail distant (voir ci-dessous pour savoir comment gérer cette opération).

- Tous les fichiers qui existent déjà sur le serveur sont remplacés.

> [!Note]
> Comme RTVS ne peut pas intercepter correctement tous les appels de fonction R, l’appel de fonctions comme `source()` ou `runApp()` (pour les applications Shiny) à partir de la fenêtre interactive ne copie *pas* les fichiers dans l’espace de travail distant.

Vous pouvez contrôler si RTVS doit copier les fichiers quand le projet est exécuté et quels fichiers sont des copies dans les [propriétés de projet](projects.md#project-properties). Pour ouvrir cette page, sélectionnez la commande de menu **Projet > Propriétés de (nom)** ou cliquez avec le bouton droit sur le projet dans l’Explorateur de solutions et sélectionnez **Propriétés...**.

![Onglet d’exécution Propriétés du projet avec les paramètres de transfert de fichiers](media/workspaces-remote-file-transfer-filter-settings.png)

Ici, **Transférer des fichiers à l’exécution** détermine si RTVS doit copier automatiquement les fichiers projet. La valeur de **Fichiers à transférer** filtre ensuite exactement les fichiers à transférer. La valeur par défaut est de copier uniquement les fichiers `.R`, `.Rmd`, `.sql`, `.md` et `.cpp`. Cela permet d’éviter la copie par inadvertance sur le serveur de fichiers de données volumineux à chaque exécution. 

## <a name="copying-files-from-a-remote-workspace"></a>Copie de fichiers à partir d’un espace de travail distant

Si votre script R génère des fichiers sur le serveur, vous pouvez copier ces fichiers sur le client à l’aide de la fonction `rtvs::fetch_file`. Cette fonction accepte, au minimum, le chemin distant du fichier que vous voulez copier sur votre ordinateur et éventuellement le chemin sur votre ordinateur où vous voulez que ce fichier soit copié. Si vous ne spécifiez pas de chemin, le fichier est copié dans votre dossier `%userprofile%\Downloads`.

