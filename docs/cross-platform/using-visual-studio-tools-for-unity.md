---
title: Utilisation de Visual Studio Tools pour Unity | Microsoft Docs
ms.custom: ''
ms.date: 07/03/2018
ms.technology: vs-unity-tools
ms.topic: how-to
ms.assetid: e67ec9a2-a449-413e-8930-9a471bd43a06
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: f65945f28a577201c1308694bb7196d464330dc1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85815160"
---
# <a name="use-visual-studio-tools-for-unity"></a>Utiliser Visual Studio Tools pour Unity

Dans cette section, vous allez apprendre à utiliser les fonctionnalités d’intégration et de productivité de Visual Studio Tools pour Unity, ainsi qu’à utiliser le débogueur Visual Studio pour le développement Unity.

## <a name="open-unity-scripts-in-visual-studio"></a>Ouvrir des scripts Unity dans Visual Studio

Une fois Visual Studio [défini comme éditeur de scripts externe pour Unity](getting-started-with-visual-studio-tools-for-unity.md#configure-unity-for-use-with-visual-studio), le fait d’ouvrir un script à partir de l’éditeur Unity lance automatiquement Visual Studio (ou bascule sur la fenêtre ouverte) sur le script en question. Double-cliquez sur l’un des scripts de votre projet Unity.

Vous pouvez aussi lancer Visual Studio sans ouvrir de script dans l’éditeur de code source, en sélectionnant **Ouvrir un projet C#** dans le menu **Ressources** de Unity.

![Ouvrir un projet C#](media/vstu_open-csharp-project.png)

## <a name="unity-documentation-access"></a>Accès à la documentation Unity

Vous pouvez accéder rapidement à la documentation sur les scripts Unity à partir de Visual Studio. Si Visual Studio Tools pour Unity ne trouve pas la documentation de l'API en local, il la recherche en ligne.

- Dans Visual Studio, mettez en surbrillance ou placez le curseur sur l’API Unity pour laquelle vous souhaitez en savoir plus, puis appuyez sur **CTRL** + **ALT** + **M**, **CTRL** + **H**

## <a name="intellisense-for-unity-api-messages"></a>IntelliSense pour les messages de l’API Unity

La saisie semi-automatique de code IntelliSense facilite l’implémentation de messages de l’API Unity dans des scripts MonoBehaviour ; par ailleurs, elle aide à découvrir l’API Unity. Pour utiliser IntelliSense pour les messages Unity :

1. Placez le curseur sur une nouvelle ligne dans le corps d’une classe qui dérive de `MonoBehaviour`.

2. Commencez à taper le nom d’un message Unity, par exemple, `OnTriggerEnter`.

3. Une fois les lettres « **ontri** » tapées, une liste de suggestions IntelliSense apparaît.

   ![Using IntelliSense](media/vstu_intellisense1.png)

4. Vous pouvez changer la sélection dans la liste de trois façons :

    - Avec les flèches **Haut** et **Bas**.

    - En cliquant avec la souris sur l’élément souhaité.

    - En continuant de taper le nom de l’élément souhaité.

5. IntelliSense peut insérer le message Unity sélectionné, y compris tous les paramètres nécessaires :

    - En appuyant sur **Tab**.

    - En appuyant sur **ENTRÉE**.

    - En double-cliquant sur l’élément sélectionné.

   ![Insérer un message Unity à partir d’IntelliSense](media/vstu_intellisense2.png)

## <a name="unity-monobehavior-scripting-wizard"></a>Assistant de script MonoBehavior d'Unity

Vous pouvez utiliser l’Assistant MonoBehavior pour afficher la liste de toutes les méthodes de l’API Unity et implémenter rapidement une définition vide. Cette fonctionnalité, en particulier avec l’option **Générer des commentaires de méthode** activée, est utile pour découvrir ce qui est disponible dans l’API Unity.

Pour créer des définitions de méthode MonoBehavior vides avec l’Assistant MonoBehavior :

1. Dans Visual Studio, placez le curseur à l’endroit où vous souhaitez insérer les méthodes, puis appuyez sur **CTRL** + **MAJ** + **M** pour lancer l’Assistant monobehavior.

2. Dans la fenêtre **Créer des méthodes de script**, cochez la case à côté du nom de chaque méthode que vous voulez ajouter.

3. Utilisez la liste déroulante **Version du framework** pour sélectionner la version souhaitée.

4. Par défaut, les méthodes sont insérées à l’endroit où se trouve le curseur. Vous pouvez également les placer après n’importe quelle méthode déjà implémentée dans votre classe en remplaçant la valeur de la liste déroulante **Point d’insertion** par l’emplacement souhaité.

5. Si vous voulez que l’Assistant génère des commentaires pour les méthodes que vous avez sélectionnées, cochez la case **Générer des commentaires de méthode**. Ces commentaires ont pour but de vous aider à comprendre à quel moment la méthode est appelée et quelles sont ses responsabilités générales.

6. Cliquez sur le bouton **OK** pour quitter l’Assistant et insérer les méthodes dans votre code.

   ![La boîte de dialogue de l'Assistant MonoBehavior.](../cross-platform/media/vstu_monobehavior_wizard_full.png "vstu_monobehavior_wizard_full")

## <a name="unity-project-explorer"></a>Explorateur de projets de Unity

![La fenêtre de l'explorateur de projet Unity.](../cross-platform/media/vstu_unity_project_explorer.png "vstu_unity_project_explorer")

L’Explorateur de projets Unity affiche tous les fichiers projet et répertoires Unity de la même manière que l’éditeur Unity. Ce n’est pas la même chose que de parcourir les scripts Unity avec l’Explorateur de solutions normal de Visual Studio, qui les organise en projets et une solution générée par Visual Studio.

- Dans le menu principal de Visual Studio, choisissez **Affichage > Explorateur de projets Unity**. Raccourci clavier : **ALT** + **MAJ** + **E**

   ![Afficher la fenêtre de l'explorateur de projet Unity.](../cross-platform/media/vstu_view_unity_project_explorer.png "vstu_view_unity_project_explorer")

## <a name="unity-debugging"></a>Débogage Unity

Visual Studio Tools pour Unity vous permet de déboguer les scripts de l'éditeur et de jeu de votre projet Unity à l'aide du puissant débogueur de Visual Studio.

### <a name="debug-in-the-unity-editor"></a>Déboguer dans l’éditeur Unity

#### <a name="start-debugging"></a>Démarrer le débogage

1. Connectez Visual Studio à Unity en cliquant sur le bouton **Lire** intitulé **Attacher à Unity**, ou utilisez le raccourci clavier **F5**.

   ![Cliquer sur Lire dans Visual Studio](media/vstu_play-button.png)

2. Basculez sur Unity et cliquez sur le bouton **Lire** pour exécuter le jeu dans l’éditeur.

   ![Cliquer sur Lire dans Unity](media/vstu_unity-play-button.png)

3. Quand le jeu s’exécute dans l’éditeur Unity, tout en étant connecté à Visual Studio, les points d’arrêt rencontrés suspendent l’exécution du jeu et affichent la ligne de code concernée dans Visual Studio.

#### <a name="stop-debugging"></a>Arrêter le débogage

- Cliquez sur le bouton **Arrêter** dans Visual Studio, ou utilisez le raccourci clavier **Maj+F5**.

  ![Cliquer sur Arrêter dans Visual Studio](media/vstu_stop-debugger.png)

Pour plus d’informations sur le débogage dans Visual Studio, voir [Premier aperçu du débogueur Visual Studio](../debugger/debugger-feature-tour.md).

#### <a name="attach-to-unity-and-play"></a>Attacher à Unity et lire

Pour plus de commodité, vous pouvez remplacer le bouton **Attacher à Unity** par le mode **Attacher à Unity et lire**.

1. Cliquez sur la petite **flèche vers le bas** à côté du bouton **Attacher à Unity**.

1. Sélectionnez **Attacher à Unity et lire** dans le menu déroulant.

    ![Attacher et lire](media/vstu_attach-and-play.png)

Le bouton Lire est à présent intitulé **Attacher à Unity et lire**. Ce bouton et le raccourci clavier **F5** ont maintenant pour effet de basculer automatiquement vers l’éditeur Unity et d’exécuter le jeu dans l’éditeur, en plus d’attacher le débogueur Visual Studio.

Le bouton **Arrêter** dans Visual Studio et le raccourci clavier **Maj**+**F5** ont maintenant pour effet d’arrêter automatiquement le jeu dans l’éditeur Unity.

### <a name="debug-unity-player-builds"></a>Déboguer les builds des lecteurs Unity

Il est possible de déboguer les builds de développement de différents lecteurs Unity avec Visual Studio.

#### <a name="enable-script-debugging-in-a-unity-player"></a>Activer le débogage de script dans un lecteur Unity

1. Dans Unity, ouvrez les paramètres de build en sélectionnant **Fichier > Paramètres de build**.

2. Dans la fenêtre Paramètres de build, cochez les cases **Build de développement** et **Débogage de script**.

   ![Configurez les paramètres de génération Unity pour le débogage.](../cross-platform/media/vstu_debugging_build_settings.png "vstu_debugging_build_settings")

#### <a name="select-a-unity-instance-to-attach-the-debugger-to"></a>Sélectionner une instance de Unity pour y attacher le débogueur

- Dans le menu principal de Visual Studio, choisissez **Déboguer > Attacher le débogueur Unity**.

   ![Attachez le débogueur Unity.](../cross-platform/media/vstu_debugging_attach_unity_debugger.png "vstu_debugging_attach_unity_debugger")

   La boîte de dialogue **Sélectionner l’instance Unity** affiche des informations sur chaque instance Unity à laquelle vous pouvez vous connecter.

   ![Choisissez une instance de Unity à laquelle vous connecter.](../cross-platform/media/vstu_attach-debugger.png "vstu_connection_to_unity")

   **Projet**

   Nom du projet Unity qui s'exécute dans cette instance Unity.

   **Machine** Nom de l’ordinateur ou de l’appareil sur lequel cette instance Unity est en cours d’exécution.

   **Type** **Éditeur** si cette instance Unity est en cours d’exécution dans l’éditeur Unity ; **Lecteur** si cette instance Unity est un lecteur autonome.

   **Port** Numéro de port du socket UDP sur lequel communique cette instance Unity.

> [!IMPORTANT]
> Étant donné que Visual Studio Tools pour Unity et l'instance Unity communiquent via un socket réseau UDP, votre pare-feu peut l'interroger. Dans ce cas, vous devez autoriser la connexion de telle sorte que VSTU et Unity puissent communiquer.

### <a name="debug-a-dll-in-your-unity-project"></a>Déboguer une DLL dans votre projet Unity

De nombreux développeurs Unity écrivent des composants de code en tant que DLL externes afin que les fonctionnalités qu'ils développent puissent être facilement partagées avec d'autres projets. Visual Studio Tools pour Unity facilite le débogage du code dans ces DLL, sans heurt avec tout autre code de votre projet Unity.

> [!NOTE]
> À ce stade, Visual Studio Tools pour Unity prend uniquement en charge les DLL managées. Il ne gère pas le débogage des DLL de code natif, telles que celles écrites en C++.

Notez que le scénario décrit ici suppose que vous disposiez du code source, autrement dit, que vous développiez ou réutilisez votre propre code tiers, ou que vous ayez le code source d'une bibliothèque tierce et que vous prévoyiez de le déployer dans votre projet Unity en tant que DLL. Ce scénario ne décrit pas le débogage d'une DLL pour laquelle vous n'avez pas le code source.

#### <a name="to-debug-a-managed-dll-project-used-in-your-unity-project"></a>Pour déboguer un projet DLL managée utilisé dans votre projet Unity

1. Ajoutez votre projet DLL existant à la solution Visual Studio générée par Visual Studio Tools pour Unity. Moins couramment, vous pouvez aussi démarrer un nouveau projet de DLL managée pour qu'il contienne les composants de code de votre projet Unity ; si tel est le cas, vous pouvez à la place ajouter un nouveau projet DLL managée à la solution Visual Studio. Pour plus d’informations sur l’ajout d’un projet nouveau ou existant à une solution, consultez [Comment : ajouter des projets à une solution](https://msdn.microsoft.com/library/ff460187.aspx).

   ![Ajoutez votre projet DLL existant à la solution.](../cross-platform/media/vstu_debugging_dll_add_existing.png "vstu_debugging_dll_add_existing")

   Dans les deux cas, Visual Studio Tools pour Unity conserve la référence de projet, même s'il doit régénérer les fichiers projet et solution ; par conséquent, vous ne devez effectuer ces étapes qu'une seule fois.

2. Référencez le bon profil du framework Unity dans le projet DLL. Dans Visual Studio, dans les propriétés du projet DLL, définissez la propriété **Framework cible** avec la version du Framework Unity que vous utilisez. Il s'agit de la bibliothèque des classes de base Unity qui correspond à la compatibilité d'API ciblée par votre projet, comme les bibliothèques de classes de base Unity complètes, micro ou web. De cette façon, votre DLL ne peut pas appeler les méthodes du framework qui existent dans d'autres frameworks ou niveaux de compatibilité, mais qui n'existent peut-être pas dans la version du framework Unity que vous utilisez.

> [!NOTE]
> Ce qui suit n’est requis que si vous utilisez le runtime hérité d’Unity. Si vous utilisez le nouveau runtime Unity, vous n’avez plus besoin d’utiliser ces profils 3.5 dédiés. Utilisez un profil 4.x .NET compatible avec votre version d’Unity.

   ![Définissez l'infrastructure Unity comme infrastructure cible de la DLL.](../cross-platform/media/vstu_debugging_dll_target_framework.png "vstu_debugging_dll_target_framework")

3. Copiez la DLL dans le dossier Composants de votre projet Unity. Dans Unity, les composants désignent les fichiers regroupés et déployés au même titre que votre application Unity afin de pouvoir être chargés au moment de l'exécution. Étant donné que les dll sont liées au moment de l’exécution, les dll doivent être déployées en tant que ressources. Pour que la DLL soit déployée comme composant, l'éditeur Unity requiert que les DLL soient placées dans le dossier Composants de votre projet Unity. Il existe deux façons de procéder :

   - Modifier les paramètres de génération de votre projet DLL pour inclure une tâche post-génération qui copie les fichiers DLL et PDB résultants de son dossier de sortie vers le dossier **Composants** de votre projet Unity.

   - Modifier les paramètres de génération de votre projet DLL pour définir son dossier de sortie comme dossier **Composants** de votre projet Unity. Les fichiers DLL et PDB seront placés dans le dossier **Composants**.

   Les fichiers PDB sont nécessaires pour le débogage, car ils contiennent les symboles de débogage de la DLL et mappent le code de la DLL sur la forme de son code source. Si vous ciblez le runtime hérité, Visual Studio Tools pour Unity utilise les informations à partir de la DLL et des fichiers PDB pour créer un fichier DLL.MDB, qui est le format des symboles de débogage utilisé par le moteur de script Unity hérité. Si vous ciblez le nouveau runtime, et Portable-PDB, Visual Studio Tools pour Unity n’essaie pas convertir les symboles, car le nouveau runtime Unity peut consommer les fichiers Portable-PDB en mode natif.

   Des informations supplémentaires sur la création de fichiers PDB sont disponibles [ici](../debugger/how-to-set-debug-and-release-configurations.md). Si vous ciblez le nouveau runtime, assurez-vous que l’option « Informations de débogage » est définie sur « Portable », afin de générer correctement un fichier Portable-PDB. Si vous ciblez le runtime hérité, vous devez utiliser l’option « Complet ».

4. Déboguez votre code. Vous pouvez maintenant déboguer le code source de votre DLL ainsi que le code source de votre projet Unity, et utiliser toutes les fonctionnalités de débogage auxquelles vous êtes habitué, telles que les points d'arrêt et le parcours du code pas à pas.

## <a name="keyboard-shortcuts"></a>Raccourcis clavier

Vous pouvez accéder rapidement aux fonctionnalités des outils Unity pour Visual Studio à l'aide de leurs raccourcis clavier. Voici un résumé des raccourcis disponibles.

|Commande|Raccourci|Nom de la commande du raccourci|
|-------------|--------------|---------------------------|
|Ouvrir l'Assistant MonoBehavior|**CTRL** + **MAJ** + **M**|**EditorContextMenus.CodeWindow.ImplementMonoBehaviours**|
|Ouvrir l'Explorateur de projets Unity|**ALT** + **MAJ** + **E**|**View.UnityProjectExplorer**|
|Accéder à la documentation Unity|**CTRL** + **ALT** + **M, CTRL** + **H**|**Help.UnityAPIReference**|
|Attacher au débogueur Unity (lecteur ou éditeur)|**_pas de valeur par défaut_**|**Debug.AttachUnityDebugger**|

Vous pouvez modifier les combinaisons de touches de raccourci si vous n'aimez pas la valeur par défaut. Pour plus d’informations sur la modification des combinaisons par défaut, consultez [Identifier et personnaliser les raccourcis clavier dans Visual Studio](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).
