---
title: Espaces de travail R
description: Guide pratique pour contrôler l’emplacement d’exécution du code R avec des espaces de travail dans Visual Studio.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 3627a8944941fc77bb9b19fe3dd0a1549f41892a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961584"
---
# <a name="control-where-r-code-runs-with-workspaces"></a>Décider où s’exécute le code R avec des espaces de travail

Un espace de travail dans les Outils R pour Visual Studio (RTVS) vous permet de configurer où s’exécute une session R, c’est-à-dire sur des ordinateurs locaux ou distants. L’objectif est de vous permettre d’utiliser les deux avec une expérience utilisateur comparable afin que vous puissiez tirer parti d’ordinateurs basés sur le cloud potentiellement plus puissants.

Pour ouvrir la fenêtre **Espaces de travail**, utilisez la commande **Outils R** > **Fenêtres** > **Espaces de travail** ou appuyez sur **Ctrl**+**9**.

![Fenêtre Espaces de travail dans les Outils R pour Visual Studio (VS2017)](media/workspaces-window.png)

Dans cette fenêtre, la coche verte indique l’espace de travail actif auquel RTVS est lié. Vous définissez l’espace de travail actif en sélectionnant une flèche bleue. L’icône de paramètres (engrenage) à droite de chaque espace de travail vous permet de changer son nom, son emplacement et ses arguments de ligne de commande. Le X rouge supprime un espace de travail ajouté manuellement.

## <a name="save-and-reset-a-workspace"></a>Enregistrer et réinitialiser un espace de travail

Par défaut, RTVS n’enregistre pas l’état de l’espace de travail quand vous fermez et rouvrez un projet. Vous pouvez changer ce comportement dans les [Options d’espace de travail](options-for-r-tools-in-visual-studio.md#workspace).

La   >    >  commande de **réinitialisation** de session outils R et le bouton Réinitialiser de la barre d’outils dans la fenêtre interactive réinitialisent également l’état de l’espace de travail à tout moment. Dans le cas d’espaces de travail distants, une réinitialisation supprime le profil utilisateur créé lors de la première connexion au serveur distant, ce qui supprime tous les fichiers stockés à cet endroit.

## <a name="local-workspaces"></a>Espaces de travail locaux

La liste des espaces de travail locaux affiche tous les interpréteurs R que vous avez installés sur votre ordinateur.

Au démarrage de Visual Studio, il tente de détecter automatiquement toutes les versions de R que vous avez installées en examinant la clé de Registre **HKEY_LOCAL_MACHINE\Software\R-Core\\** . Comme cette vérification est effectuée uniquement au démarrage, vous devez redémarrer Visual Studio si vous installez un nouvel interpréteur R.

RTVS peut ne pas détecter un interpréteur R installé de manière non standard (par exemple, quand vous copiez simplement des fichiers dans un dossier au lieu d’exécuter un programme d’installation). Dans ce cas, créez manuellement un nouvel espace de travail R local comme suit :

1. Sélectionnez le bouton **Ajouter** dans la fenêtre Espaces de travail.
1. Entrez un nom pour le nouvel espace de travail.
1. Entrez le chemin du dossier racine R, qui est celui qui contient le dossier *bin* avec l’interpréteur, ainsi que les arguments de ligne de commande facultatifs à passer à l’interpréteur au démarrage de RTVS.
1. Lorsque vous avez terminé, sélectionnez **Enregistrer**.

![Ajout d’un nouvel espace de travail](media/workspaces-add-new.png)

## <a name="remote-workspaces"></a>Espaces de travail distants

Les espaces de travail distants vous permettent de vous connecter à une session R sur un ordinateur distant. (Consultez [Configurer des espaces de travail distants](setting-up-remote-r-workspaces.md) pour savoir comment configurer un ordinateur dans ce but.)

Comme Visual Studio ne détecte pas automatiquement les espaces de travail distants, vous devez les ajouter manuellement à l’aide du bouton **Ajouter** dans la fenêtre Espaces de travail, comme décrit dans la section précédente. Dans ce cas, entrez l’URI de l’ordinateur distant au lieu d’un chemin local.

> [!Important]
> Les espaces de travail distants sont identifiés par un URI qui *doit utiliser le protocole HTTPS* pour garantir la confidentialité et l’intégrité de la communication avec l’ordinateur distant. Visual Studio ne peut pas se connecter à un ordinateur distant qui ne prend pas en charge le protocole HTTPS.

> [!Note]
> Les espaces de travail distants sont en préversion. Nous travaillons à une meilleure implémentation du problème de synchronisation des fichiers dans une version future et nous sommes à l’écoute de vos suggestions et commentaires.

## <a name="remote-workspace-logon"></a>Connexion à un espace de travail distant

Vous devez utiliser un nom d’utilisateur et un mot de passe pour vous connecter à l’espace de travail à distance.

### <a name="logon-to-windows-workspace"></a>Se connecter à un espace de travail Windows

Si votre ordinateur distant est configuré pour utiliser votre compte de domaine, vous pouvez utiliser la connexion au domaine pour accéder à un espace de travail distant. Si ce n’est pas le cas, vous devez utiliser le format `machine-name\username` pour vous connecter avec un compte d’ordinateur sur l’ordinateur distant.

### <a name="logon-to-linux-workspace"></a>Se connecter à un espace de travail Linux

Pour vous connecter à un compte Linux, utilisez le format `<<unix>>\username`. Par exemple, si vous avez un compte nommé `ruser`, vous devez entrer `<<unix>>\ruser` pour le nom d’utilisateur.

## <a name="switch-between-workspaces"></a>Basculer entre les espaces de travail

RTVS est lié à un seul espace de travail à la fois. L’espace de travail lié est indiqué par une petite coche verte dans la fenêtre Espaces de travail. Par défaut, RTVS est lié au dernier espace de travail local ouvert dans une session précédente.

Pour changer l’espace de travail actif, sélectionnez la flèche bleue à côté de l’espace de travail de votre choix. Vous êtes alors invité à enregistrer votre session, l’espace de travail actuel se ferme et vous basculez sur le nouvel espace de travail.

> [!Tip]
> Pour désactiver l’invite d’enregistrement, sélectionnez la commande **Outils R**,  >   puis activez la case à cocher **afficher la boîte de dialogue de confirmation avant de changer d’espace de travail** `No` . Consultez [Options de l’espace de travail](options-for-r-tools-in-visual-studio.md#workspace).

Si vous essayez de basculer vers un espace de travail local qui a été désinstallé ou un espace de travail distant non disponible, il est possible que RTVS ne soit lié à aucun espace de travail. Par conséquent, vous pouvez obtenir une erreur quand vous entrez du code dans la fenêtre interactive ou tentez d’exécuter le code d’une autre façon :

![Erreur quand aucun espace de travail n’est lié à RTVS](media/workspaces-disconnected-interactive-window.png)

Pour corriger ce problème, basculez vers un autre espace de travail dans la fenêtre Espaces de travail. Si aucun espace de travail n’est disponible, vous devez installer un interpréteur R. Vous pouvez également essayer de redémarrer Visual Studio si vous avez installé un interpréteur quand Visual Studio était déjà en cours d’exécution.

### <a name="switch-to-a-remote-workspace"></a>Basculer vers un espace de travail distant

RTVS vous demande vos informations d’identification quand vous vous connectez pour la première fois à un espace de travail distant, puis met en cache ces informations d’identification (à l’aide du stockage sécurisé des informations d’identification de Windows) pour les sessions ultérieures. La communication avec le serveur distant est ensuite établie en toute sécurité sur HTTPS (ce qui est obligatoire).

Selon la configuration du serveur, vous pouvez obtenir un avertissement de certificat à la connexion qui indique : « Le certificat de sécurité présenté par le serveur Remote R Services ne nous permet pas de prouver que vous êtes en train de vous connecter à l’ordinateur (nom). ».

![Avertissement du certificat auto-signé lors de la connexion à un espace de travail distant](media/workspaces-remote-self-signed-certificate-warning.png)

Le certificat est un document présenté à RTVS par l’ordinateur auquel vous essayez de vous connecter. Il contient un champ permettant d’identifier l’URI de l’ordinateur. L’avertissement s’affiche quand RTVS détecte une incompatibilité entre l’URI du certificat et l’URI utilisé pour se connecter à l’ordinateur, ce qui indique que la sécurité du serveur est peut-être compromise.

Toutefois, cet avertissement s’affiche également si un *certificat auto-signé* a été utilisé pour activer HTTPS sur l’ordinateur distant au lieu d’en utiliser un d’un fournisseur approuvé. Pour plus d’informations, consultez [Configurer des espaces de travail distants](setting-up-remote-r-workspaces.md).

## <a name="directories-on-local-and-remote-computers"></a>Répertoires sur des ordinateurs locaux et distants

Par défaut, quand vous démarrez un nouvel interpréteur R dans un espace de travail local, votre répertoire de travail actuel est *%userprofile%\Documents*. Vous pouvez modifier le répertoire à tout moment à l’aide des commandes du  >  **Répertoire de travail** outils R ou en cliquant avec le bouton droit sur un projet dans Visual Studio Explorateur de solutions et en sélectionnant des commandes telles que **définir le répertoire de travail ici**.

Lors de votre première connexion à un ordinateur distant, RTVS crée automatiquement un profil utilisateur d’après vos informations d’identification, ce qui permet de définir le répertoire de travail sur le dossier *Documents* sous ce profil. Ce dossier est utilisé pour toutes les sessions à distance suivantes qui utilisent les mêmes informations d’identification.

Par conséquent, l’endroit exact où s’exécute votre code peut différer entre les espaces de travail locaux et distants. Dans votre code, utilisez donc toujours des chemins relatifs vers les fichiers de données de sorte que votre code soit portable entre les espaces de travail.

Notez également qu’avec les espaces de travail distants, tous les fichiers du répertoire de travail restent en place entre les sessions pour le même profil utilisateur. Comme indiqué précédemment, vous pouvez supprimer ces fichiers à l’aide de la commande de  >    >  **réinitialisation** de session des outils R (ou du bouton Réinitialiser dans la fenêtre interactive) lors de l’utilisation d’un espace de travail distant. Cette commande supprime à nouveau le profil utilisateur du serveur, qui est recréé quand vous vous reconnectez.

## <a name="copy-project-files-to-remote-workspaces"></a>Copier des fichiers projet dans des espaces de travail distants

Quand vous utilisez des projets R dans Visual Studio, l’ordinateur local a toujours les derniers fichiers projet, même quand vous utilisez un espace de travail distant. Autrement dit, quand vous ouvrez un projet dans Visual Studio (ce qui implique généralement l’ouverture d’une solution contenant ce projet), RTVS suppose que le contenu du projet réside entièrement sur l’ordinateur local. L’espace de travail distant est, en fait, un simple hôte temporaire pour les fichiers du projet et toutes les sorties du code. Cela signifie, par exemple, que lors du chargement d’un fichier à l’aide de `source` dans la fenêtre interactive, ce fichier doit déjà être sur l’ordinateur distant dans le chemin que vous fournissez ou dans le répertoire de travail actuel de l’interpréteur R distant (défini avec la fonction `setwd()`).

Les fichiers sont copiés sur le serveur distant comme suit :

- Pour utiliser des fichiers à distance par le biais de la fenêtre interactive, vous devez d’abord les copier manuellement en cliquant dessus avec le bouton droit (ou sur le projet) dans l’Explorateur de solutions et en sélectionnant **Source sélectionnée**. Les fichiers individuels sont copiés dans le répertoire de travail sur le serveur. Quand vous copiez un projet, RTVS crée un dossier pour le projet.

- Vous pouvez également copier des fichiers en les sélectionnant dans l’Explorateur de solutions, puis en sélectionnant **Approvisionner les fichier(s) sélectionné(s)**. Cette action les charge dans la fenêtre interactive où ils sont exécutés. Si la session est connectée à un ordinateur distant, les fichiers y sont d’abord copiés.

- Quand RTVS est lié à un espace de travail distant et que vous appuyez sur **F5**, sélectionnez **Déboguer** > **Démarrer le débogage** ou démarrez l’exécution de votre code, RTVS copie automatiquement par défaut le fichier du projet dans l’espace de travail distant (voir ci-dessous pour savoir comment gérer ce comportement).

- Tous les fichiers qui existent déjà sur le serveur sont remplacés.

> [!Note]
> Comme RTVS ne peut pas intercepter correctement tous les appels de fonction R, l’appel de fonctions comme `source()` ou `runApp()` (pour les applications Shiny) dans la fenêtre interactive ne copie *pas* les fichiers dans l’espace de travail distant.

Les [propriétés de projet](r-projects-in-visual-studio.md#project-properties) contrôlent si RTVS copie les fichiers quand un projet est exécuté et quels fichiers exactement sont copiés. Pour ouvrir cette page, sélectionnez la commande de menu **projet**  >  **(Name) Propriétés** , ou cliquez avec le bouton droit sur le projet dans Explorateur de solutions et sélectionnez **Propriétés**.

![Onglet d’exécution Propriétés du projet avec les paramètres de transfert de fichiers](media/workspaces-remote-file-transfer-filter-settings.png)

Ici, la propriété **Transférer des fichiers à l’exécution** détermine si RTVS doit copier automatiquement les fichiers projet. La valeur de **Fichiers à transférer** filtre ensuite exactement les fichiers à transférer. La valeur par défaut consiste à copier uniquement les fichiers *. R*, *. RMD*, *.sql*, *.md* et *.cpp*. Ce comportement permet d’éviter la copie par inadvertance de fichiers de données volumineux sur le serveur à chaque exécution.

## <a name="copy-files-from-a-remote-workspace"></a>Copier des fichiers à partir d’un espace de travail distant

Si votre script R génère des fichiers sur le serveur, vous pouvez copier ces fichiers sur le client à l’aide de la fonction `rtvs::fetch_file`. Cette fonction accepte, au minimum, le chemin distant du fichier que vous voulez copier sur votre ordinateur et éventuellement le chemin cible sur votre ordinateur. Si vous ne spécifiez pas de chemin, le fichier est copié dans votre dossier *%userprofile%\Downloads*.
