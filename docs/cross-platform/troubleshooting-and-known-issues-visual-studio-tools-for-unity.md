---
title: Problèmes connus et dépannage (Visual Studio Tools pour Unity) | Microsoft Docs
ms.custom: ''
ms.date: 07/03/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: df458124be9650319f47979f7d2d98801d06a61f
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153902"
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>Problèmes connus et dépannage (Visual Studio Tools pour Unity)

Dans cette section, vous allez trouver les solutions aux problèmes courants rencontrés par Visual Studio Tools pour Unity, ainsi que la description de problèmes identifiés. Vous apprendrez aussi comment vous pouvez aider à améliorer Visual Studio Tools pour Unity en signalant les erreurs.

## <a name="troubleshooting-the-connection-between-unity-and-visual-studio"></a>Résolution des problèmes de connexion entre Unity et Visual Studio

### <a name="confirm-editor-attaching-is-enabled"></a>Vérifier que l’attachement de l’éditeur est activé

Dans le menu Unity, sélectionnez **Edit (Edition) > Preferences (Préférences)**, puis sélectionnez l’onglet **External Tools (Outils externes)**. Vérifiez que la case **Editor Attaching (Attachement de l’éditeur)** est cochée. Pour plus d’informations, voir la [documentation sur les préférences d’Unity](https://docs.unity3d.com/Manual/Preferences.html).

### <a name="unable-to-attach"></a>Impossible de s’attacher

- Essayez de désactiver temporairement votre antivirus ou créez des règles d’exclusion pour VS et Unity.
- Essayez de désactiver temporairement votre pare-feu ou créez des règles d’autorisation de mise en réseau TCP/UDP entre VS et Unity.
- Certains programmes, comme TeamViewer, risquent d’interférer avec la détection des processus. Vous pouvez tenter d’arrêter temporairement tous les logiciels supplémentaires pour voir si cela change quelque chose.
- Ne renommez pas l’exécutable Unity principal, car VSTU surveille uniquement les processus « Unity.exe ».

## <a name="visual-studio-crashes"></a>Visual Studio est en panne

Ce problème peut être dû à un endommagement du cache MEF de Visual Studio.

Tentez de supprimer le dossier suivant pour réinitialiser le cache MEF (fermez Visual Studio avant) :

```batch
%localappdata%\Microsoft\VisualStudio\<version>\ComponentModelCache
```

Votre problème devrait être résolu. Si le problème persiste, exécutez une invite de commandes développeur pour Visual Studio en tant qu’administrateur et utilisez la commande suivante :

```batch
 devenv /setup
```

## <a name="visual-studio-hangs"></a>Visual Studio se bloque

Plusieurs plug-ins Unity comme Parse, FMOD, UMP (Universal Media Player), ZFBrowser ou Embedded Browser utilisent des threads natifs. Un problème se pose quand un plug-in finit par attacher un thread natif au runtime, ce qui aboutit ensuite à des appels bloquants pour le système d’exploitation. Cela signifie qu’Unity ne peut pas interrompre ce thread pour le débogueur (ou le rechargement de domaine) et se bloque.

Pour FMOD, il existe une solution, vous pouvez passer [l’indicateur](https://www.fmod.org/docs/content/generated/FMOD_STUDIO_INITFLAGS.html) d’initialisation FMOD_STUDIO_INIT_SYNCHRONOUS_UPDATE pour désactiver le traitement asynchrone et effectuer tout le traitement sur le thread principal.

## <a name="incompatible-project-in-visual-studio"></a>Projet incompatible dans Visual Studio

Tout d’abord, vérifiez que Visual Studio est configuré comme éditeur de script externe dans Unity (Edition/Préférences/Outils externes). Vérifiez ensuite que le plug-in Visual Studio est installé dans Unity (Aide/À propos de doit afficher un message comme Microsoft Visual Studio Tools pour Unity est activé en bas). Vérifiez ensuite que l’extension est correctement installée dans Visual Studio (Aide/À propos de).

## <a name="extra-reloads-or-visual-studio-losing-all-open-windows"></a>Rechargements supplémentaires ou perte de toutes les fenêtres de Visual Studio

Veillez à ne jamais toucher aux fichiers projet directement à partir d’un processeur de composants ou de tout autre outil. Si vous devez vraiment manipuler le fichier projet, utilisez pour cela l’API que nous exposons. Consultez la [section des problèmes de références d’assembly](#Assembly-reference-issues).

Si vous constatez des rechargements supplémentaires ou si Visual Studio perd toutes les fenêtres ouvertes lors du rechargement, vérifiez que les packs de ciblage .NET installés sont les bons. Pour plus d’informations, voir la section suivante sur les frameworks.

## <a name="the-debugger-does-not-break-on-exceptions"></a>Le débogueur ne s’arrête pas sur les exceptions

Lors de l’utilisation du runtime Unity hérité (équivalent de .NET 3.5), le débogueur s’arrête toujours quand une exception est non gérée (= en dehors d’un bloc try/catch). Si l’exception est gérée, le débogueur utilise la fenêtre Paramètres d’exception pour déterminer si un arrêt est nécessaire ou non.

Avec le nouveau runtime (équivalent de .NET 4.6), Unity introduit une nouvelle méthode de gestion des exceptions de l’utilisateur : toutes les exceptions sont considérées comme « gérées par l’utilisateur », même si elles sont en dehors d’un bloc try/catch. C’est pourquoi vous devez maintenant les vérifier explicitement dans la fenêtre Paramètres d’exception si vous voulez que le débogueur s’arrête.

Dans la fenêtre Paramètres d’exception (Déboguer > Fenêtres > Paramètres d’exception), développez le nœud d’une catégorie d’exceptions (par exemple Exceptions Common Language Runtime, c’est-à-dire les exceptions .NET), puis cochez la case correspondant à l’exception spécifique que vous voulez intercepter dans cette catégorie (par exemple System.NullReferenceException). Vous pouvez également sélectionner une catégorie entière d'exceptions.

## <a name="on-windows-visual-studio-asks-to-download-the-unity-target-framework"></a>Dans Windows, Visual Studio vous demande de télécharger la version cible de .Net Framework pour Unity

Visual Studio Tools pour Unity nécessite le .NET Framework 3.5, qui n’est pas installé par défaut sur Windows 8 ou 10. Pour résoudre ce problème, suivez les instructions de téléchargement et d’installation du .NET Framework 3.5.

Lors de l’utilisation du nouveau runtime Unity, les packs de ciblage .NET version 4.6 et 4.7.1 sont également nécessaires. Il est possible d’utiliser le programme d’installation VS2017 pour les installer rapidement (Modifier votre installation de VS2017, Composants individuels, Catégorie .NET, sélectionnez tous les packs de ciblage 4.x).

## <a name="assembly-reference-issues"></a>Problèmes de référence d’assembly

Si votre projet est complexe côté référence ou si vous souhaitez mieux contrôler cette étape de génération, vous pouvez utiliser notre [API](../cross-platform/customize-project-files-created-by-vstu.md) pour manipuler le contenu du projet ou de la solution généré. Vous pouvez également utiliser des [fichiers réponse](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) dans votre projet Unity et nous les traiterons.

## <a name="breakpoints-with-a-warning"></a>Points d’arrêt avec un avertissement

Si Visual Studio ne parvient pas à trouver un emplacement source pour un point d’arrêt spécifique, un avertissement s’affiche autour de votre point d’arrêt. Vérifiez que le script utilisé est correctement chargé/utilisé dans la scène Unity actuelle.

## <a name="breakpoints-not-hit"></a>Points d’arrêt non atteints

Vérifiez que le script utilisé est correctement chargé/utilisé dans la scène Unity actuelle. Quittez à la fois Visual Studio et Unity, puis supprimez tous les fichiers générés (*.csproj, *.sln) et l’intégralité du dossier de bibliothèque.

## <a name="unable-to-debug-android-players"></a>Impossible de déboguer les lecteurs Android

Nous utilisons la multidiffusion pour la détection de lecteur (qui est le mécanisme par défaut utilisé par Unity), mais nous utilisons par la suite une connexion TCP standard pour attacher le débogueur. La phase de détection représente le principal problème des appareils Android.

Wi-Fi est polyvalent, mais très lent comparé à USB en raison de la latence. Nous avons constaté un manque de prise en charge de multidiffusion appropriée pour certains routeurs ou appareils (les séries Nexus sont bien connues pour cela).

USB est très rapide pour le débogage, et Visual Studio Tools pour Unity est maintenant en mesure de détecter les périphériques USB et de communiquer avec le serveur adb pour transférer correctement des ports pour le débogage.

## <a name="issues-with-visual-studio-2015-and-intellisense-or-code-coloration"></a>Problèmes avec Visual Studio 2015 et IntelliSense ou la coloration du code

Tentez de mettre à niveau Visual Studio 2015 vers la mise à jour 3.

## <a name="known-issues"></a>Problèmes connus

 Il existe des problèmes connus dans Visual Studio Tools pour Unity qui résultent de la façon dont le débogueur interagit avec une version antérieure de Unity du compilateur C#. Nous nous efforçons de vous aider à résoudre ces problèmes, mais vous rencontrerez peut-être les problèmes suivants d’ici-là :

- Lors du débogage, il arrive que Unity s'arrête.

- Lors du débogage, il arrive que Unity se bloque.

- L'exécution pas à pas et la reprise des méthodes ne fonctionnent parfois pas très bien, en particulier dans les itérateurs ou dans les instructions switch.

## <a name="reporting-errors"></a>Signalement des erreurs

 Aidez-nous à améliorer la qualité de Visual Studio Tools for Unity en envoyant des rapports d'erreurs lorsque vous êtes confronté à un arrêt, un blocage ou autres erreurs. Ceci nous permet d'examiner et de résoudre les problèmes de Visual Studio Tools pour Unity. Merci !

### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>Comment signaler une erreur lorsque Visual Studio se bloque

 Il a été établi que Visual Studio se bloque parfois lors du débogage avec Visual Studio Tools pour Unity, mais nous avons besoin de plus de données pour comprendre ce problème. Vous pouvez nous aider à enquêter sur le problème en suivant les étapes ci-dessous.

##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>Pour signaler que Visual Studio se bloque pendant le débogage avec Visual Studio Tools pour Unity

*Sur Windows :*

1. Ouvrez une nouvelle instance de Visual Studio.

1. Ouvrez la boîte de dialogue Attacher au processus. Dans la nouvelle instance de Visual Studio, dans le menu principal, choisissez **Déboguer**, **Attacher au processus**.

1. Attachez le débogueur à l'instance figée de Visual Studio. Dans la boîte de dialogue **Attacher au processus** , sélectionnez l'instance figée de Visual Studio à partir de la table **Processus disponibles** , puis choisissez le bouton **Attacher** .

1. Interrompez le débogueur. Dans la nouvelle instance de Visual Studio, dans le menu principal, choisissez **Déboguer**, **Interrompre tout** ou appuyez simplement sur **Ctrl+Alt+Pause**.

1. Créez un vidage de thread. Dans la fenêtre Commande, entrez la commande suivante et appuyez sur **Entrée** :

    ```powershell
    Debug.ListCallStack /AllThreads /ShowExternalCode
    ```

    Vous devrez peut-être afficher d'abord la fenêtre **Commande** . Dans Visual Studio, dans le menu principal, choisissez **Affichage**, **Autres fenêtres**, **Fenêtre Commande**.

*Sur Mac :*

1. Ouvrez un terminal et obtenez le PID de Visual Studio pour Mac :

    ```shell
    ps aux | grep "[V]isual Studio.app"
    ```

1. Lancez le débogueur lldb :

    ```shell
    lldb
    ```

1. Attachez à l’instance de Visual Studio pour Mac à l’aide du PID :

    ```shell
    process attach --pid THE_PID_OF_THE_VSFM_PROCESS
    ```

1. Récupérez le StackTrace pour tous les threads :

    ```shell
    bt all
    ```

Enfin, envoyez le vidage de thread à [vstusp@microsoft.com](mailto:vstusp@microsoft.com), ainsi qu’une description de ce que vous faisiez quand Visual Studio s’est bloqué.