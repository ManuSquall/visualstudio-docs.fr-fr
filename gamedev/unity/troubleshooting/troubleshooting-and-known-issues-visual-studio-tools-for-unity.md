---
title: Problèmes connus et dépannage (Outils Visual Studio pour Unity)
description: En savoir plus sur la résolution des problèmes dans Outils Visual Studio pour Unity. Consultez les descriptions des problèmes connus et découvrez les solutions à ces problèmes.
ms.custom: ''
ms.date: 04/15/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: troubleshooting
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 37ee35fa66d37f9b85af01f5012e8ede76e877de
ms.sourcegitcommit: 3e1ff87fba290f9e60fb4049d011bb8661255d58
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2021
ms.locfileid: "107879367"
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>Problèmes connus et dépannage (Outils Visual Studio pour Unity)

Dans cette section, vous allez trouver les solutions aux problèmes courants rencontrés par Visual Studio Tools pour Unity, ainsi que la description de problèmes identifiés. Vous apprendrez aussi comment vous pouvez aider à améliorer Visual Studio Tools pour Unity en signalant les erreurs.

## <a name="troubleshooting-the-connection-between-unity-and-visual-studio"></a>Résolution des problèmes de connexion entre Unity et Visual Studio

### <a name="confirm-editor-attaching-is-enabled-or-code-optimization-on-startup-is-set-to-debug"></a>Confirmer `Editor Attaching` est activé ou `Code Optimization On Startup` défini sur `Debug`

Dans le menu Unity, sélectionnez `Edit / Preferences` .

Selon la version Unity utilisée :
- Vérifiez que `Code Optimization On Startup` a la valeur `Debug` .
- Ou sélectionnez l' `External Tools` onglet. Confirmez que la `Editor Attaching` case à cocher est activée. 

Pour plus d’informations, voir la [documentation sur les préférences d’Unity](https://docs.unity3d.com/Manual/Preferences.html).

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

## <a name="visual-studio-stops-responding"></a>Visual Studio ne répond plus

Plusieurs plug-ins Unity comme Parse, FMOD, UMP (Universal Media Player), ZFBrowser ou Embedded Browser utilisent des threads natifs. Un problème se pose quand un plug-in finit par attacher un thread natif au runtime, ce qui aboutit ensuite à des appels bloquants pour le système d’exploitation. Cela signifie que Unity ne peut pas interrompre ce thread pour le débogueur (ou le rechargement de domaine) et cesser de répondre.

Pour FMOD, il existe une solution, vous pouvez passer [l’indicateur](https://www.fmod.com/resources/documentation-studio?version=2.0&page=https://fmod.com/resources/documentation-api?version=2.0&page=studio-api-system.html#fmod_studio_initflags) d’initialisation `FMOD_STUDIO_INIT_SYNCHRONOUS_UPDATE` pour désactiver le traitement asynchrone et effectuer tout le traitement sur le thread principal.

## <a name="incompatible-project-in-visual-studio"></a>Projet incompatible dans Visual Studio

La chose la plus importante à savoir est que Visual Studio enregistre l’État « incompatible » dans les paramètres du projet et ne tente pas de recharger un projet tant que vous n’utilisez pas explicitement `Reload Project` . Ainsi, après chaque étape de résolution des problèmes, veillez à essayer de rouvrir la solution et essayez de cliquer avec le bouton droit sur tous les projets incompatibles, puis choisissez `Reload Project` .

1. Vérifiez que Visual Studio est défini comme éditeur de script externe dans Unity à l’aide de `Edit / Preferences / External Tools` .
2. Selon votre version Unity :
   - Vérifiez que le plug-in Visual Studio est installé dans Unity. `Help / About` doit afficher un message comme Microsoft Visual Studio Tools pour Unity est activé en bas.
   - Unity 2020. x + : Vérifiez que vous utilisez le dernier package de l’éditeur Visual Studio dans `Window / Package Manager` .
3. Essayez de supprimer tous les projets/fichiers de solution et le `.vs` dossier de votre projet.
4. Essayez de recréer les projets/la solution à l’aide `Open C# Project` de ou `Edit / Preferences / External tools / Regenerate Project files` .
5. Vérifiez que vous avez installé la charge de travail Game/Unity dans Visual Studio.
6. Essayez de nettoyer le cache MEF comme expliqué [ici](#visual-studio-crashes).
7. Essayez de réinstaller Visual Studio (à l’aide de la charge de travail Game/Unity uniquement pour démarrer).
8. Essayez de désactiver des extensions tierces en cas d’interférence avec l’extension Unity dans `Tools / Extensions` .

## <a name="extra-reloads-or-visual-studio-losing-all-open-windows"></a>Rechargements supplémentaires ou perte de toutes les fenêtres de Visual Studio

Veillez à ne jamais toucher aux fichiers projet directement à partir d’un processeur de composants ou de tout autre outil. Si vous devez vraiment manipuler le fichier projet, utilisez pour cela l’API que nous exposons. Consultez la [section des problèmes de références d’assembly](#assembly-reference-or-project-property-issues).

Si vous constatez des rechargements supplémentaires ou si Visual Studio perd toutes les fenêtres ouvertes lors du rechargement, vérifiez que les packs de ciblage .NET installés sont les bons. Pour plus d’informations, voir la section suivante sur les frameworks.

## <a name="the-debugger-does-not-break-on-exceptions"></a>Le débogueur ne s’arrête pas sur les exceptions

Lors de l’utilisation du runtime Unity hérité (équivalent de .NET 3.5), le débogueur s’arrête toujours quand une exception est non gérée (= en dehors d’un bloc try/catch). Si l’exception est gérée, le débogueur utilise la fenêtre Paramètres d’exception pour déterminer si un arrêt est nécessaire ou non.

Avec le nouveau runtime (équivalent de .NET 4.6), Unity introduit une nouvelle méthode de gestion des exceptions de l’utilisateur : toutes les exceptions sont considérées comme « gérées par l’utilisateur », même si elles sont en dehors d’un bloc try/catch. C’est pourquoi vous devez maintenant les vérifier explicitement dans la fenêtre Paramètres d’exception si vous voulez que le débogueur s’arrête.

Dans la fenêtre Paramètres d’exception (Déboguer > Fenêtres > Paramètres d’exception), développez le nœud d’une catégorie d’exceptions (par exemple Exceptions Common Language Runtime, c’est-à-dire les exceptions .NET), puis cochez la case correspondant à l’exception spécifique que vous voulez intercepter dans cette catégorie (par exemple System.NullReferenceException). Vous pouvez également sélectionner une catégorie entière d'exceptions.

## <a name="on-windows-visual-studio-asks-to-download-the-unity-target-framework"></a>Dans Windows, Visual Studio vous demande de télécharger la version cible de .Net Framework pour Unity

Lors de l’utilisation du runtime Unity hérité (.NET 3,5 équivalent), Outils Visual Studio pour Unity nécessite le .NET Framework 3,5, qui n’est pas installé par défaut sur Windows 8 ou 10. Pour résoudre ce problème, suivez les instructions de téléchargement et d’installation du .NET Framework 3.5.

Lors de l’utilisation du nouveau Runtime Unity, les packs de ciblage .NET version 4,6 ou 4.7.1 sont également requis en fonction de la version Unity. Il est possible d’utiliser le programme d’installation de Visual Studio pour les installer rapidement (modifier votre installation, composants individuels, catégorie .NET, sélectionner tous les packs de ciblage 4. x).

## <a name="assembly-reference-or-project-property-issues"></a>Problèmes de référence d’assembly ou de propriété de projet

Si votre projet est complexe côté référence ou si vous souhaitez mieux contrôler cette étape de génération, vous pouvez utiliser notre [API](../extensibility/customize-project-files-created-by-vstu.md) pour manipuler le contenu du projet ou de la solution généré. Vous pouvez également utiliser des [fichiers réponse](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) dans votre projet Unity et nous les traiterons.

Avec les versions récentes de Visual Studio et Unity, la meilleure approche semble utiliser un `Directory.Build.props` fichier personnalisé avec vos projets générés. Vous pourrez ensuite contribuer à la structure du projet sans interférer avec le processus de génération. Plus d’informations [ici](https://docs.microsoft.com/visualstudio/msbuild/customize-your-build#directorybuildprops-and-directorybuildtargets).

## <a name="breakpoints-with-a-warning"></a>Points d’arrêt avec un avertissement

Si Visual Studio ne parvient pas à trouver un emplacement source pour un point d’arrêt spécifique, un avertissement s’affiche autour de votre point d’arrêt. Vérifiez que le script utilisé est correctement chargé/utilisé dans la scène Unity actuelle.

## <a name="breakpoints-not-hit"></a>Points d’arrêt non atteints

Vérifiez que le script utilisé est correctement chargé/utilisé dans la scène Unity actuelle. Quittez Visual Studio et Unity, puis supprimez tous les fichiers générés ( \* . csproj, \* . sln), le `.vs` dossier et tout le dossier de bibliothèque. Vous trouverez plus d’informations sur le débogage C# sur le [site Web](https://docs.unity3d.com/Manual/ManagedCodeDebugging.html)Unity.

## <a name="unable-to-debug-android-players"></a>Impossible de déboguer les lecteurs Android

Nous utilisons la multidiffusion pour la détection de lecteur (qui est le mécanisme par défaut utilisé par Unity), mais nous utilisons par la suite une connexion TCP standard pour attacher le débogueur. La phase de détection représente le principal problème des appareils Android.

Wi-Fi est polyvalent, mais très lent comparé à USB en raison de la latence. Nous avons constaté un manque de prise en charge de multidiffusion appropriée pour certains routeurs ou appareils (les séries Nexus sont bien connues pour cela).

USB est très rapide pour le débogage, et Visual Studio Tools pour Unity est maintenant en mesure de détecter les périphériques USB et de communiquer avec le serveur adb pour transférer correctement des ports pour le débogage.

## <a name="issues-with-intellisense-or-code-coloration"></a>Problèmes avec IntelliSense ou la coloration du code

Essayez de mettre à niveau Visual Studio vers la dernière version. Essayez les mêmes étapes de dépannage que pour les [projets incompatibles](#incompatible-project-in-visual-studio).

## <a name="known-issues"></a>Problèmes connus

Il existe des problèmes connus dans Visual Studio Tools pour Unity qui résultent de la façon dont le débogueur interagit avec une version antérieure de Unity du compilateur C#. Nous nous efforçons de vous aider à résoudre ces problèmes, mais vous rencontrerez peut-être les problèmes suivants d’ici-là :

- Lors du débogage, il arrive que Unity s'arrête.

- Lors du débogage, il arrive que Unity se bloque.

- L'exécution pas à pas et la reprise des méthodes ne fonctionnent parfois pas très bien, en particulier dans les itérateurs ou dans les instructions switch.

## <a name="report-errors"></a>Signaler les erreurs

Aidez-nous à améliorer la qualité de Visual Studio Tools for Unity en envoyant des rapports d'erreurs lorsque vous êtes confronté à un arrêt, un blocage ou autres erreurs. Ceci nous permet d'examiner et de résoudre les problèmes de Visual Studio Tools pour Unity. Merci !

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

*Sur Mac :*

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

Enfin, envoyez le vidage de thread à [vstusp@microsoft.com](mailto:vstusp@microsoft.com) , ainsi qu’une description de ce que vous avez fait quand Visual Studio est devenu figé.

## <a name="see-also"></a>Voir aussi

- [Résolution des problèmes de Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)
