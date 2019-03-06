---
title: Déboguer à l’aide du débogueur juste à temps | Microsoft Docs
ms.date: 09/24/2018
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c8a9661673adf6cdab2d9a880ce27197a4e53127
ms.sourcegitcommit: 1c8e07b98fc0a44b5ab90bcef77d9fac7b3eb452
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/25/2019
ms.locfileid: "56796554"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Déboguer à l’aide du débogueur juste à temps dans Visual Studio

Débogage juste-à-temps peut lancer Visual Studio automatiquement lorsqu’une application s’exécutant en dehors des erreurs de Visual Studio ou des pannes. Avec juste-à-temps de débogage, vous pouvez tester des applications en dehors de Visual Studio et ouvrez Visual Studio pour commencer le débogage lorsqu’un problème survient.

Fonctionne avec le débogage juste-à-temps pour les applications de bureau Windows. Il ne fonctionne pas pour les applications Windows universelles, ou pour le code managé qui est hébergé dans une application native, par exemple les visualiseurs.

> [!TIP]
> Si vous souhaitez simplement arrêter la boîte de dialogue d’apparaître, mais n’avez installé Visual Studio, consultez [désactiver le débogueur juste à temps](../debugger/just-in-time-debugging-in-visual-studio.md). Si vous aviez une fois Visual Studio installé, vous devrez peut-être [juste-à-temps de désactiver le débogage à partir du Registre Windows](#disable-just-in-time-debugging-from-the-windows-registry).

##  <a name="BKMK_Enabling"></a> Activer ou désactiver le débogage dans Visual Studio juste-à-temps

>[!NOTE]
>Pour activer ou désactiver le débogage juste-à-temps, vous devez exécuter Visual Studio en tant qu’administrateur. Activation ou désactivation juste-à-temps débogage définit une clé de Registre et des privilèges d’administrateur peuvent être nécessaires pour modifier cette clé. Pour ouvrir Visual Studio en tant qu’administrateur, avec le bouton droit de l’application de Visual Studio et choisissez **exécuter en tant qu’administrateur**.

Vous pouvez configurer le débogage à partir de Visual Studio juste-à-temps **outils** > **Options** (ou **déboguer** > **Options**) boîte de dialogue.

**Pour activer ou désactiver le débogage juste-à-temps :**

1. Sur le **outils** ou **déboguer** menu, sélectionnez **Options** > **débogage**  >   **Juste-à-temps**.

   ![Activer ou désactiver le débogage JIT](../debugger/media/dbg-jit-enable-or-disable.png "activer ou désactiver le débogage JIT")

1. Dans le **activer JIT pour ces types de code** , sélectionnez les types de code que vous souhaitez pour déboguer du débogage juste-à-temps : **managé**, **natif**, et/ou  **Script**.

1. Sélectionnez **OK**.

Si vous activez juste-à-temps débogueur, mais il ne s’ouvre pas lorsqu’une application se bloque ou d’erreurs, consultez [juste à temps de résoudre les problèmes de débogage](#jit_errors).

## <a name="disable-just-in-time-debugging-from-the-windows-registry"></a>Désactiver le débogage à partir du Registre Windows juste-à-temps

Le débogage juste-à-temps peut toujours être activé même si Visual Studio n'est plus installé sur votre ordinateur. Si Visual Studio n’est plus installé, vous pouvez désactiver le débogage en modifiant le Registre Windows juste-à-temps.

**Pour désactiver le débogage juste-à-temps en modifiant le registre :**

1.  À partir de la Windows **Démarrer** menu, exécutez le **Éditeur du Registre** (*regedit.exe*).

2.  Dans le **Éditeur du Registre** fenêtre, recherchez et supprimez les entrées de Registre suivantes :

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\DbgManagedDebugger**

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    ![Clé de Registre JIT](../debugger/media/dbg-jit-registry.png "clé de Registre JIT")

3.  Si votre ordinateur exécute un système d’exploitation de 64 bits, également supprimer les entrées de Registre suivantes :

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\DbgManagedDebugger**

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    Évitez de supprimer ou modifier d’autres clés de Registre.

5.  Fermer le **Éditeur du Registre** fenêtre.

## <a name="enable-just-in-time-debugging-of-a-windows-form"></a>Activer juste-à-temps de débogage d’un formulaire Windows

Par défaut, les applications Windows Form ont un gestionnaire d’exceptions de niveau supérieur qui permet à l’application continue de s’exécuter s’il peut être récupéré. Si une application Windows Forms lève une exception non gérée, elle affiche la boîte de dialogue suivante :

![Exception non gérée Windows Form](../debugger/media/windowsformsunhandledexception.png "exception non gérée Windows Form")

Pour activer le débogage au lieu de la gestion des erreurs Windows Form standard juste-à-temps, ajoutez ces paramètres :

-  Dans le `system.windows.forms` section de la *machine.config* ou  *\<nom de l’application >. exe.config* de fichiers, définissez le `jitDebugging` valeur `true`:

    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

-  Dans une application C++ Windows Form, définissez également `DebuggableAttribute` à `true` dans un *.config* fichier ou dans votre code. Si vous effectuez la compilation avec [/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format) et sans [/Og](/cpp/build/reference/og-global-optimizations), le compilateur définit cet attribut pour vous. Si vous souhaitez déboguer une version Release non optimisée, toutefois, vous devez définir `DebuggableAttribute` en ajoutant la ligne suivante de votre application *AssemblyInfo.cpp* fichier :

   ```cpp
   [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
   ```

   Pour plus d'informations, consultez <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="BKMK_Using_JIT"></a>Utiliser juste-à-temps de débogage
 Cet exemple vous guide tout au long de débogage lorsqu’une application lève une erreur juste-à-temps.

 - Vous devez disposer de Visual Studio est installé pour suivre ces étapes. Si vous n’avez pas Visual Studio, vous pouvez télécharger la version gratuite [Visual Studio Community Edition](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15).

 - Bien sûr juste-à-temps de rendre le débogage est [activé](#BKMK_Enabling) dans **outils** > **Options** > **débogage**  >  **Juste-à-temps**.

Pour cet exemple, vous allez effectuer un C# application console dans Visual Studio lève une [NullReferenceException](/dotnet/api/system.nullreferenceexception).

1. Dans Visual Studio, créez un C# application console (**fichier** > **New** > **projet** > **Visual C#**   >  **Application console**) nommé *ThrowsNullException*. Pour plus d’informations sur la création de projets dans Visual Studio, consultez [procédure pas à pas : créer une application simple](/visualstudio/get-started/csharp/tutorial-wpf).

1. Lorsque le projet s’ouvre dans Visual Studio, ouvrez le *Program.cs* fichier. Remplacez la méthode Main() par le code suivant, qui imprime une ligne dans la console et puis lève une exception NullReferenceException :

   ```csharp
   static void Main(string[] args)
   {
       Console.WriteLine("we will now throw a NullReferenceException");
       throw new NullReferenceException("this is the exception thrown by the console app");
   }
   ```

1. Pour générer la solution, choisissez le **déboguer** (valeur par défaut) ou **version** configuration, puis sélectionnez **Build** > **régénérer la Solution** .

   > [!NOTE]
   > - Choisissez **déboguer** configuration pour l’expérience de débogage complète.
   > - Si vous sélectionnez [version](../debugger/how-to-set-debug-and-release-configurations.md) configuration, vous devez désactiver l’option [uniquement mon Code](../debugger/just-my-code.md) pour cette procédure fonctionne. Sous **outils** > **Options** > **débogage**, désélectionnez **activer uniquement mon Code**.

   Pour plus d’informations sur les configurations de build, consultez [Présentation des configurations de build](../ide/understanding-build-configurations.md).

1. Ouvrez l’application intégrée *ThrowsNullException.exe* dans votre C# dossier du projet (*...\ThrowsNullException\ThrowsNullException\bin\Debug* ou *...\ThrowsNullException\ ThrowsNullException\bin\Release*).

   Vous devez voir la fenêtre de commande suivante :

   ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")

1. Le **choisir le débogueur juste à temps** boîte de dialogue s’ouvre.

   ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")

   Sous **débogueurs disponibles**, sélectionnez **nouvelle instance de \<votre préféré version/édition de Visual Studio >**, si ce n’est déjà fait.

1. Sélectionnez **OK**.

   Le projet ThrowsNullException s’ouvre dans une nouvelle instance de Visual Studio, avec l’exécution s’est arrêtée à la ligne qui a levé l’exception :

   ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

Vous pouvez démarrer le débogage à ce stade. Si vous déboguez une application réelle, vous devez savoir pourquoi le code lève l’exception.

> [!CAUTION]
> Si votre application contient du code non fiable, une boîte de dialogue sécurité s’affiche, ce qui vous permet de décider s’il faut continuer le débogage. Avant de continuer le débogage, décidez si vous faites confiance au code. Avez-vous écrit le code vous-même ? Si l'application s'exécute sur un ordinateur distant, reconnaissez-vous le nom du processus ? Si l’application s’exécute localement, envisagez la possibilité de code malveillant s’exécute sur votre ordinateur. Si vous décidez que le code est digne de confiance, sélectionnez **OK**. Sinon, sélectionnez **Annuler**.

## <a name="jit_errors"></a> Juste-à-temps de résoudre les problèmes de débogage

Si juste-à-temps de débogage ne démarre pas lorsqu’une application tombe en panne, même si elle est activée dans Visual Studio :

- Peut prendre le rapport d’erreurs Windows sur la gestion des erreurs sur votre ordinateur.

  Pour résoudre ce problème, utilisez l’Éditeur du Registre pour ajouter un **valeur DWORD** de **désactivé**, avec **données de la valeur** de **1**, aux clés de Registre suivantes :

  - **Rapport d’erreurs HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\Windows**

  - (Pour les ordinateurs 64 bits) : **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows\Windows rapport d’erreurs**

  Pour plus d’informations, consultez [. Paramètres de rapport d’erreurs Windows](https://docs.microsoft.com/windows/desktop/wer/wer-settings).

- Un problème connu de Windows peut être à l’origine juste-à-temps débogueur échec.

  La solution consiste à ajouter un **valeur DWORD** de **automatique**, avec **données de la valeur** de **1**, aux clés de Registre suivantes :

  - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug**

  - (Pour les ordinateurs 64 bits) : **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug**

Vous pouvez voir les messages d’erreur suivant juste-à-temps au cours de débogage :

- **Impossible de s'attacher au processus bloqué. Le programme spécifié n'est pas un programme Windows ou MS-DOS.**

    Le débogueur a essayé de s’attacher à un processus en cours d’exécution sous un autre utilisateur.

    Pour contourner ce problème, dans Visual Studio, ouvrez **déboguer** > **attacher au processus**, recherchez le processus à déboguer dans le **processus disponibles** liste. Si vous ne connaissez pas le nom du processus, recherchez l’ID de processus dans le **débogueur de Visual Studio juste à temps** boîte de dialogue. Sélectionnez le processus dans le **processus disponibles** liste, puis sélectionnez **attacher**. Sélectionnez **non** pour faire disparaître juste-à-temps boîte de dialogue de débogueur.

- **Impossible de démarrer le débogueur, car aucun utilisateur n'est connecté.**

    Il n’existe aucun utilisateur connecté à la console, il n’existe aucune session utilisateur pour afficher juste-à-temps boîte de dialogue de débogage.

    Pour résoudre ce problème, ouvrez une session sur l'ordinateur.

- **Classe non inscrite.**

    Le débogueur a essayé de créer une classe COM qui n’est pas inscrit, probablement en raison d’un problème d’installation.

    Pour résoudre ce problème, utilisez Visual Studio Installer pour réinstaller ou réparer votre installation de Visual Studio.

## <a name="see-also"></a>Voir aussi

- [Sécurité du débogueur](../debugger/debugger-security.md)
- [Présentation du débogueur](../debugger/debugger-feature-tour.md)
- [Options, débogage, juste-à-temps boîte de dialogue](../debugger/just-in-time-debugging-options-dialog-box.md)
- [Avertissement de sécurité : L’attachement à un processus appartenant à un utilisateur non approuvé peut être dangereux. Si les informations suivantes semblent suspectes ou si vous avez des doutes, ne faites pas d’attachement à ce processus](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
