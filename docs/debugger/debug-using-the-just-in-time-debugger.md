---
title: Déboguer à l’aide du débogueur juste-à-temps | Microsoft Docs
description: Déboguez à l’aide du débogueur juste-à-temps dans Visual Studio. Le débogage juste-à-temps peut lancer Visual Studio automatiquement quand une application rencontre des erreurs ou se bloque.
ms.custom: SEO-VS-2020
ms.date: 09/24/2018
ms.topic: how-to
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3bdd35056706491ace6e5e6b2f7c3f6a45464d2e
ms.sourcegitcommit: a0f5e7188838c5989c9cc78d99fb29bb2813501e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2021
ms.locfileid: "109729245"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Déboguer à l’aide du débogueur juste-à-temps dans Visual Studio

Le débogage juste-à-temps peut lancer Visual Studio automatiquement quand une application en cours d’exécution en dehors de Visual Studio rencontre des erreurs ou se bloque. Avec le débogage juste-à-temps, vous pouvez tester des applications en dehors de Visual Studio et ouvrir Visual Studio pour commencer le débogage lorsqu’un problème se produit.

Le débogage juste-à-temps fonctionne pour les applications de bureau Windows. Il ne fonctionne pas pour les applications Windows universelles, ni pour le code managé hébergé dans une application native, comme les visualiseurs.

> [!TIP]
> Si vous souhaitez simplement arrêter l’affichage de la boîte de dialogue débogueur juste-à-temps, mais que Visual Studio n’est pas installé, consultez [désactiver le débogueur juste-à-temps](../debugger/just-in-time-debugging-in-visual-studio.md). Si vous avez installé Visual Studio, vous devrez peut-être [désactiver le débogage juste-à-temps à partir du Registre Windows](#disable-just-in-time-debugging-from-the-windows-registry).

## <a name="enable-or-disable-just-in-time-debugging-in-visual-studio"></a><a name="BKMK_Enabling"></a> Activer ou désactiver le débogage juste-à-temps dans Visual Studio

>[!NOTE]
>Pour activer ou désactiver le débogage juste-à-temps, vous devez exécuter Visual Studio en tant qu’administrateur. L’activation ou la désactivation du débogage juste-à-temps définit une clé de Registre et des privilèges d’administrateur peuvent être nécessaires pour modifier cette clé. Pour ouvrir Visual Studio en tant qu’administrateur, cliquez avec le bouton droit sur l’application Visual Studio et choisissez **exécuter en tant qu’administrateur**.

Vous pouvez configurer le débogage juste-à-temps à partir de la boîte de dialogue Options des **Outils** Visual Studio  >   (ou options de **débogage**  >  ).

**Pour activer ou désactiver le débogage juste-à-temps :**

1. Dans le menu **Outils** ou **Déboguer** , sélectionnez **options**  >  **débogage**  >  **juste-à-temps**.

   ![Activer ou désactiver le débogage juste-à-temps](../debugger/media/dbg-jit-enable-or-disable.png "Activer ou désactiver le débogage juste-à-temps")

1. Dans la zone **activer le débogage juste-à-temps pour ces types de code** , sélectionnez les types de code pour lesquels vous souhaitez déboguer le débogage juste-à-temps : **managé**, **natif** et/ou **script**.

1. Sélectionnez **OK**.

Si vous activez le débogueur juste-à-temps, mais qu’il ne s’ouvre pas quand une application se bloque ou des erreurs, consultez [résoudre les problèmes de débogage juste-à-temps](#jit_errors).

## <a name="disable-just-in-time-debugging-from-the-windows-registry"></a>Désactiver le débogage juste-à-temps à partir du Registre Windows

Le débogage juste-à-temps peut toujours être activé même si Visual Studio n'est plus installé sur votre ordinateur. Si Visual Studio n’est plus installé, vous pouvez désactiver le débogage juste-à-temps en modifiant le Registre Windows.

**Pour désactiver le débogage juste-à-temps en modifiant le registre :**

1. Dans le menu **Démarrer** de Windows, exécutez l' **éditeur du registre** (*regedit.exe*).

2. Dans la fenêtre de l' **éditeur du Registre** , recherchez et supprimez les entrées de Registre suivantes :

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    ![Clé de Registre JIT](../debugger/media/dbg-jit-registry.png "Clé de Registre JIT")

3. Si votre ordinateur exécute un système d’exploitation 64 bits, supprimez également les entrées de Registre suivantes :

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    Veillez à ne pas supprimer ou modifier d’autres clés de registre.

5. Fermez la fenêtre **Éditeur du Registre**.

## <a name="enable-just-in-time-debugging-of-a-windows-form"></a>Activer le débogage juste-à-temps d’un Windows Form

Par défaut, les applications Windows Forms ont un gestionnaire d’exceptions de niveau supérieur qui permet à l’application de continuer à s’exécuter si elle peut effectuer une récupération. Si une application Windows Forms lève une exception non gérée, elle affiche la boîte de dialogue suivante :

![Exception non gérée Windows Form](../debugger/media/windowsformsunhandledexception.png "Exception non gérée Windows Form")

Pour activer le débogage juste-à-temps au lieu de la gestion des erreurs Windows Forms standard, ajoutez les paramètres suivants :

- Dans la `system.windows.forms` section du fichier *machine.config* ou *\<app name>.exe.config* , définissez la `jitDebugging` valeur sur `true` :

    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

- Dans une application Windows Forms C++, définissez également `DebuggableAttribute` sur `true` dans un fichier *. config* ou dans votre code. Si vous effectuez la compilation avec [/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format) et sans [/Og](/cpp/build/reference/og-global-optimizations), le compilateur définit cet attribut pour vous. Toutefois, si vous souhaitez déboguer une version Release non optimisée, vous devez définir `DebuggableAttribute` en ajoutant la ligne suivante dans le fichier *AssemblyInfo. cpp* de votre application :

   ```cpp
   [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
   ```

   Pour plus d’informations, consultez <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="use-just-in-time-debugging"></a><a name="BKMK_Using_JIT"></a>Utiliser le débogage juste-à-temps
Cet exemple vous guide tout au long du débogage juste-à-temps lorsqu’une application génère une erreur.

- Vous devez avoir installé Visual Studio pour suivre ces étapes. Si vous ne disposez pas de Visual Studio, vous pouvez télécharger gratuitement [Visual Studio Community Edition](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15).

- Assurez-vous que le débogage juste-à-temps est [activé](#BKMK_Enabling) dans **Outils**  >  **options**  >  **débogage**  >  **juste-à-temps**.

Pour cet exemple, vous allez créer une application console C# dans Visual Studio qui lève une [exception NullReferenceException](/dotnet/api/system.nullreferenceexception).

1. Dans Visual Studio, créez une application console C# (**fichier**  >  **nouveau**  >  **projet**  >    >  **application console** Visual C#) nommée *ThrowsNullException*. Pour plus d’informations sur la création de projets dans Visual Studio, consultez [procédure pas à pas : création d’une application simple](../get-started/csharp/tutorial-wpf.md).

1. Lorsque le projet s’ouvre dans Visual Studio, ouvrez le fichier *Program. cs* . Remplacez la méthode main () par le code suivant, qui imprime une ligne dans la console, puis lève une exception NullReferenceException :

   ```csharp
   static void Main(string[] args)
   {
       Console.WriteLine("we will now throw a NullReferenceException");
       throw new NullReferenceException("this is the exception thrown by the console app");
   }
   ```

1. Pour générer la solution, choisissez la configuration **Debug** (par défaut) ou **Release** , puis sélectionnez **générer** la  >  **solution de régénération**.

   > [!NOTE]
   > - Choisissez configuration de **débogage** pour l’expérience de débogage complète.
   > - Si vous sélectionnez la configuration [Release](../debugger/how-to-set-debug-and-release-configurations.md) , vous devez désactiver [uniquement mon code](../debugger/just-my-code.md) pour que cette procédure fonctionne. Sous **Outils**  >  **options**  >  **débogage**, désélectionnez **activer uniquement mon code**.

   Pour plus d’informations sur les configurations de build, consultez [Présentation des configurations de build](../ide/understanding-build-configurations.md).

1. Ouvrez le *ThrowsNullException.exe* d’application généré dans le dossier de votre projet C# (*. ..\ThrowsNullException\ThrowsNullException\bin\Debug* ou *. ..\ThrowsNullException\ThrowsNullException\bin\Release*).

   La fenêtre de commande suivante doit s’afficher :

   ![Capture d’écran de la console pour ThrowsNullException.exe, qui lève une exception de référence null non gérée (System. NullReferenceException).](../debugger/media/throwsnullexceptionconsole.png)

1. La boîte de dialogue **choisir le débogueur juste-à-temps** s’ouvre.

   ![Capture d’écran de la boîte de dialogue choisir le débogueur juste-à-temps, qui apparaît une fois que l’exception apparaît dans la fenêtre de console ThrowsNullException.exe.](../debugger/media/justintimedialog.png)

   Sous **débogueurs disponibles**, sélectionnez **nouvelle instance de \<your preferred Visual Studio version/edition>**, si elle n’est pas déjà sélectionnée.

1. Sélectionnez **OK**.

   Le projet ThrowsNullException s’ouvre dans une nouvelle instance de Visual Studio, avec l’exécution arrêtée à la ligne qui a levé l’exception :

   ![Capture d’écran du projet ThrowsNullException dans Visual Studio, avec mise en surbrillance de la ligne de code source qui a levé l’exception.](../debugger/media/nullreferencesecondinstance.png)

Vous pouvez démarrer le débogage à ce stade. Si vous déboguez une application réelle, vous devez déterminer la raison pour laquelle le code a levé l’exception.

> [!CAUTION]
> Si votre application contient du code non fiable, une boîte de dialogue d’avertissement de sécurité s’affiche, vous permettant de décider s’il faut poursuivre le débogage. Avant de continuer le débogage, déterminez si vous faites confiance au code. Avez-vous écrit le code vous-même ? Si l'application s'exécute sur un ordinateur distant, reconnaissez-vous le nom du processus ? Si l’application s’exécute localement, pensez à la possibilité que du code malveillant s’exécute sur votre ordinateur. Si vous décidez que le code est digne de confiance, sélectionnez **OK**. Sinon, sélectionnez **Annuler**.

## <a name="troubleshoot-just-in-time-debugging"></a><a name="jit_errors"></a> Résoudre les problèmes de débogage juste-à-temps

Si le débogage juste-à-temps ne démarre pas lorsqu’une application se bloque, même si elle est activée dans Visual Studio :

- Rapport d’erreurs Windows peut prendre en charge la gestion des erreurs sur votre ordinateur.

  Pour résoudre ce problème, utilisez l’éditeur du Registre pour ajouter une **valeur DWORD** **Disabled**, avec les **données de valeur** **1**, aux clés de Registre suivantes :

  - **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\Windows Error Reporting**

  - (Pour les ordinateurs 64 bits) : **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows\Windows Error Reporting**

  Pour plus d’informations, consultez [. Paramètres WER](/windows/desktop/wer/wer-settings).

- Un problème connu de Windows peut être à l’origine de l’échec du débogueur juste-à-temps.

  Le correctif consiste à ajouter la **valeur DWORD** **auto**, avec les **données** de valeur **1**, aux clés de Registre suivantes :

  - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug**

  - (Pour les ordinateurs 64 bits) : **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug**

Vous pouvez voir les messages d’erreur suivants lors du débogage juste-à-temps :

- **Impossible de s’attacher au processus bloqué. Le programme spécifié n’est pas un programme Windows ou MS-DOS.**

    Le débogueur a essayé de s’attacher à un processus qui s’exécute sous un autre utilisateur.

    Pour contourner ce problème, dans Visual Studio, ouvrez **Déboguer**  >  **attacher au processus** (ou appuyez sur **CTRL**  +  **ALT**  +  **P**), puis recherchez le processus que vous souhaitez déboguer dans la liste **processus disponibles** . Si vous ne connaissez pas le nom du processus, recherchez l’ID du processus dans la boîte de dialogue **Débogueur juste-à-temps Visual Studio** . Sélectionnez le processus dans la liste **processus disponibles** , puis cliquez sur **attacher**. Sélectionnez **non** pour fermer la boîte de dialogue du débogueur juste-à-temps.

- **Impossible de démarrer le débogueur, car aucun utilisateur n'est connecté.**

    Aucun utilisateur n’a ouvert de session sur la console. il n’existe donc aucune session utilisateur pour afficher la boîte de dialogue de débogage juste-à-temps.

    Pour résoudre ce problème, ouvrez une session sur l'ordinateur.

- **Classe non inscrite.**

    Le débogueur a essayé de créer une classe COM qui n’est pas inscrite, probablement en raison d’un problème d’installation.

    Pour résoudre ce problème, utilisez la Visual Studio Installer pour réinstaller ou réparer votre installation de Visual Studio.

## <a name="see-also"></a>Voir aussi

- [Sécurité du débogueur](../debugger/debugger-security.md)
- [Présentation du débogueur](../debugger/debugger-feature-tour.md)
- [Options, débogage, boîte de dialogue juste-à-temps](../debugger/just-in-time-debugging-options-dialog-box.md)
- [Avertissement de sécurité Attachement à un processus appartenant à un utilisateur non fiable peut être dangereux. Si les informations suivantes semblent suspectes ou si vous avez des doutes, ne faites pas d’attachement à ce processus](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
