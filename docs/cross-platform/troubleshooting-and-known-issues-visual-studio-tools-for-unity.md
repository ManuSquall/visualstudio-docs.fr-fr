---
title: "Problèmes connus et dépannage (Visual Studio Tools pour Unity) | Microsoft Docs"
ms.custom: 
ms.date: 10/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
caps.latest.revision: "5"
author: conceptdev
ms.author: crdun
manager: crdun
ms.openlocfilehash: 338f80724598a3c89dcde3806511427b81bffca4
ms.sourcegitcommit: ebe9fb5eda724936f7a059d35d987c29dffdb50d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2017
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>Problèmes connus et dépannage (Visual Studio Tools pour Unity)
Dans cette section, vous allez trouver les solutions aux problèmes courants rencontrés par Visual Studio Tools pour Unity, ainsi que la description de problèmes identifiés. Vous apprendrez aussi comment vous pouvez aider à améliorer Visual Studio Tools pour Unity en signalant les erreurs.  

## <a name="troubleshooting"></a>Résolution des problèmes  
Pour résoudre certains problèmes courants avec Visual Studio Tools pour Unity, consultez les sections suivantes.  

### <a name="visual-studio-crashes"></a>Visual Studio est en panne
Cela peut être dû à un endommagement du cache MEF de Visual Studio.

Vous devez supprimer le dossier suivant pour réinitialiser le cache MEF (fermez Visual Studio avant de le faire) :

```batch
%localappdata%\Microsoft\VisualStudio\<version>\ComponentModelCache
```

Votre problème devrait être résolu. Si le problème persiste, exécutez une invite de commandes développeur pour Visual Studio en tant qu’administrateur et utilisez la commande suivante :

```batch
 devenv /setup
```

### <a name="issues-with-vs2015-and-intellisense-or-code-coloration"></a>Problèmes avec VS2015 et Intellisense ou coloration du code.
Vous devez tenter la mise à niveau vers Visual Studio 2015 Update 3.

### <a name="visual-studio-hangs"></a>Visual Studio se bloque
Plusieurs plug-ins Unity comme Parse, FMOD, UMP (Universal Media Player), ZFBrowser ou Embedded Browser utilisent des threads natifs. Un problème se pose quand un plug-in finit par attacher un thread natif au runtime, ce qui aboutit ensuite à des appels bloquants pour le système d’exploitation. Cela signifie qu’Unity ne peut pas interrompre ce thread pour le débogueur (ou le rechargement de domaine) et se bloque.

Pour FMOD, il existe une solution, vous pouvez passer [l’indicateur](https://www.fmod.org/docs/content/generated/FMOD_STUDIO_INITFLAGS.html) d’initialisation FMOD_STUDIO_INIT_SYNCHRONOUS_UPDATE pour désactiver le traitement asynchrone et effectuer tout le traitement sur le thread principal.

### <a name="incompatible-project-in-visual-studio"></a>Projet incompatible dans Visual Studio
Tout d’abord, vérifiez que Visual Studio est configuré comme éditeur de script externe dans Unity (Edition/Préférences/Outils externes). Vérifiez ensuite que le plug-in Visual Studio est installé dans Unity (Aide/À propos de doit afficher un message comme Microsoft Visual Studio Tools pour Unity est activé en bas). Vérifiez ensuite que l’extension est correctement installée dans Visual Studio (Aide/À propos de).

### <a name="assembly-reference-issues"></a>Problèmes de référence d’assembly
Si votre projet est complexe côté référence ou si vous souhaitez mieux contrôler cette étape de génération, vous pouvez utiliser notre [API](../cross-platform/customize-project-files-created-by-vstu.md) pour manipuler le contenu du projet ou de la solution généré. Vous pouvez également utiliser des [fichiers réponse](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) dans votre projet Unity et nous les traiterons.

### <a name="breakpoints-with-a-warning"></a>Points d’arrêt avec un avertissement
Si Visual Studio ne parvient pas à trouver un emplacement source pour un point d’arrêt spécifique, un avertissement s’affiche autour de votre point d’arrêt. Vérifiez que le comportement que vous utilisez est correctement chargé/utilisé dans la scène Unity actuelle.

### <a name="breakpoints-not-hit"></a>Points d’arrêt non atteints
 Vérifiez que le comportement que vous utilisez est correctement chargé/utilisé dans la scène Unity actuelle. Quittez à la fois Visual Studio et Unity, puis supprimez tous les fichiers générés (*.csproj, *.sln) et l’intégralité du dossier de bibliothèque.

### <a name="unable-to-attach"></a>Impossible de s’attacher
-   Essayez de désactiver temporairement votre antivirus ou créez des règles d’exclusion pour VS et Unity.
-   Essayez de désactiver temporairement votre pare-feu ou créez des règles d’autorisation de mise en réseau TCP/UDP entre VS et Unity.
-   Comme nous avons déterminé que des programmes comme TeamViewer interfèrent avec la détection de processus, vous pouvez peut-être essayer d’arrêter temporairement tout logiciel supplémentaire pour voir si cela change quelque chose.
-   Ne renommez pas l’exécutable Unity principal, car VSTU surveille uniquement les processus « Unity.exe ».

### <a name="unable-to-debug-android-players"></a>Impossible de déboguer les lecteurs Android
Nous utilisons la multidiffusion pour la détection de lecteur (qui est le mécanisme par défaut utilisé par Unity), mais nous utilisons par la suite une connexion TCP standard pour attacher le débogueur. La phase de détection représente le principal problème des appareils Android.

USB est extrêmement rapide pour le débogage, mais non compatible avec le mécanisme de détection de lecteur Unity.
Wi-Fi est plus polyvalent, mais très lent comparé à USB en raison de la latence. Nous avons constaté un manque de prise en charge de multidiffusion appropriée pour certains routeurs ou appareils (les séries Nexus sont bien connues pour cela).

Vous pouvez essayer la procédure suivante en utilisant USB pour afficher les ports ouverts sur l’appareil connecté (avec le lecteur opérationnel pour pouvoir voir le port de débogage, toujours sous la forme 56xxx) :

```shell  
adb shell netstat
```  

Transférez le port sur le PC local :

```shell  
adb forward tcp:56xxx tcp:56xxx
```  

Connectez ensuite VSTU à l’aide du port transféré 127.0.0.1:56xxx.

### <a name="migrating-from-unityvs-to-visual-studio-tools-for-unity"></a>Migration de UnityVS vers Visual Studio Tools pour Unity  
 Si vous procédez à une migration à partir de UnityVS vers Visual Studio Tools pour Unity, vous devez générer de nouvelles solutions Visual Studio pour vos projets Unity.  

##### <a name="to-migrate-your-unity-project-from-unityvs-18-to-visual-studio-tools-for-unity-19"></a>Pour migrer votre projet Unity de UnityVS 1.8 vers Visual Studio Tools pour Unity 1.9  

1.  Supprimez les anciens fichiers solution et projet de votre projet Unity. Dans le répertoire racine de votre projet Unity, recherchez les fichiers Visual Studio .sln et *.proj, puis supprimez-les.  

2.  Importez le package Visual Studio Tools pour Unity dans votre projet Unity. Pour plus d'informations sur l'importation du package VSTU, consultez Configurer Visual Studio Tools pour Unity dans la page [Prise en main](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) .  

3.  Générez les nouveaux fichiers solution et projet. Si vous souhaitez les générer maintenant, dans l'éditeur Unity, dans le menu principal, choisissez **Visual Studio Tools**, **Générer les fichiers projet**. Sinon, vous pouvez ignorer cette étape si vous le souhaitez. Visual Studio Tools pour Unity génère les nouveaux fichiers automatiquement lorsque vous choisissez **Visual Studio Tools**, **Ouvrir dans Visual Studio**.  

### <a name="on-windows-visual-studio-asks-to-download-the-unity-target-framework"></a>Dans Windows, Visual Studio vous demande de télécharger la version cible de .Net Framework pour Unity  
 Visual Studio Tools pour Unity a besoin de .Net Framework 3.5, qui n’est pas installé par défaut sur Windows 8 ni 10. Pour résoudre ce problème, suivez les instructions de téléchargement et d’installation de .Net Framework 3.5.  

## <a name="known-issues"></a>Problèmes connus  
 Il existe des problèmes connus dans Visual Studio Tools pour Unity qui résultent de la façon dont le débogueur interagit avec une version antérieure de Unity du compilateur C#. Nous nous efforçons de vous aider à résoudre ces problèmes, mais vous rencontrerez peut-être les problèmes suivants d’ici-là :  

-   Lors du débogage, il arrive que Unity s'arrête.  

-   Lors du débogage, il arrive que Unity se bloque.  

-   L'exécution pas à pas et la reprise des méthodes ne fonctionnent parfois pas très bien, en particulier dans les itérateurs ou dans les instructions switch.  

## <a name="reporting-errors"></a>Signalement des erreurs  
 Aidez-nous à améliorer la qualité de Visual Studio Tools for Unity en envoyant des rapports d'erreurs lorsque vous êtes confronté à un arrêt, un blocage ou autres erreurs. Ceci nous permet d'examiner et de résoudre les problèmes de Visual Studio Tools pour Unity. Merci !  

### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>Comment signaler une erreur lorsque Visual Studio se bloque  
 Il a été établi que Visual Studio se bloque parfois lors du débogage avec Visual Studio Tools pour Unity, mais nous avons besoin de plus de données pour comprendre ce problème. Vous pouvez nous aider à enquêter sur le problème en suivant les étapes ci-dessous.  

##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>Pour signaler que Visual Studio se bloque pendant le débogage avec Visual Studio Tools pour Unity

*Sur Windows :*  

1.  Ouvrez une nouvelle instance de Visual Studio.

2.  Ouvrez la boîte de dialogue Attacher au processus. Dans la nouvelle instance de Visual Studio, dans le menu principal, choisissez **Déboguer**, **Attacher au processus**.  

3.  Attachez le débogueur à l'instance figée de Visual Studio. Dans la boîte de dialogue **Attacher au processus** , sélectionnez l'instance figée de Visual Studio à partir de la table **Processus disponibles** , puis choisissez le bouton **Attacher** .  

4.  Interrompez le débogueur. Dans la nouvelle instance de Visual Studio, dans le menu principal, choisissez **Déboguer**, **Interrompre tout** ou appuyez simplement sur **Ctrl+Alt+Pause**.  

5.  Créez un vidage de thread. Dans la fenêtre Commande, entrez la commande suivante et appuyez sur **Entrée** :  

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
