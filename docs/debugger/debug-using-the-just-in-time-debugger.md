---
title: Déboguer à l’aide du débogueur juste à temps | Microsoft Docs
ms.custom: ''
ms.date: 07/06/17
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: ee4d79a5-a1d2-4418-a93f-dd57a53e1836
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aa31d9d9b536a614cc1000f7c25ae6fbb5e4d510
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39176439"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Déboguer à l’aide du débogueur juste à temps dans Visual Studio
Le débogage juste-à-temps lance Visual Studio automatiquement lorsqu’une exception ou un incident se produit dans une application qui s’exécute en dehors de Visual Studio. Cela vous permet de tester votre application lorsque Visual Studio n’est pas en cours d’exécution et commencez le débogage avec Visual Studio lorsqu’un problème survient.

Fonctionne avec le débogage juste-à-temps pour les applications de bureau Windows. Il ne fonctionne pas pour les applications Windows universelles, et il ne fonctionne pas pour le code managé qui est hébergé dans une application native, par exemple les visualiseurs.

> [!TIP]
> Si vous souhaitez simplement savoir comment répondre aux juste-à-temps boîte de dialogue du débogueur, consultez [cette rubrique](../debugger/just-in-time-debugging-in-visual-studio.md).

##  <a name="BKMK_Enabling"></a> Activer ou désactiver juste-à-temps le débogage
Vous pouvez activer ou désactiver le débogage à partir de Visual Studio juste-à-temps **Outils > Options** boîte de dialogue.

#### <a name="to-enable-or-disable-just-in-time-debugging"></a>Pour activer ou désactiver le débogage juste-à-temps

1.  Ouvrez Visual Studio avec des privilèges d’administrateur (avec le bouton droit et choisissez **exécuter en tant qu’administrateur**).

    Activation ou désactivation juste-à-temps débogage définit une clé de Registre et des privilèges d’administrateur peuvent être nécessaires pour modifier cette clé.

2. Dans le menu **Outils** , cliquez sur **Options**.

2.  Dans le **Options** boîte de dialogue, développez le **débogage** nœud.

3.  Dans le **débogage** nœud, sélectionnez **juste-à-temps**.

    ![Activer ou désactiver le débogage JIT](../debugger/media/dbg-jit-enable-or-disable.png "activer ou désactiver le débogage JIT")

4.  Dans le **activer le débogage de ces types de code** zone, sélectionnez ou désactivez les types de programmes adéquats : **managé**, **natif**, ou **Script**.

5.  Cliquez sur **OK**.

Le débogage juste-à-temps peut toujours être activé même si Visual Studio n'est plus installé sur votre ordinateur. Lorsque Visual Studio n’est pas installé, vous ne pouvez pas désactiver le débogage à partir de Visual Studio juste-à-temps **Options** boîte de dialogue. Dans ce cas, vous pouvez désactiver le débogage juste-à-temps en modifiant le Registre Windows.

#### <a name="to-disable-just-in-time-debugging-by-editing-the-registry"></a>Pour désactiver le débogage juste-à-temps en modifiant le Registre

1.  Sur le **Démarrer** menu, recherchez et exécutez `regedit.exe`

2.  Dans le **Éditeur du Registre** fenêtre, recherchez et supprimez les entrées de Registre suivantes :

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\DbgManagedDebugger

    ![Clé de Registre JIT](../debugger/media/dbg-jit-registry.png "clé de Registre JIT")

3.  Si votre ordinateur exécute un système d’exploitation de 64 bits, supprimez également les entrées de Registre suivantes :

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework\DbgManagedDebugger

4.  Veillez à ne pas supprimer ou modifier par inadvertance d'autres clés de Registre.

5.  Fermer le **Éditeur du Registre** fenêtre.

#### <a name="to-enable-just-in-time-debugging-of-a-windows-form"></a>Pour activer le débogage juste-à-temps d'un Windows Forms

1.  Par défaut, les applications Windows Forms ont un gestionnaire d’exceptions de haut niveau qui permet au programme de continuer à s’exécuter s’il peut être récupéré. Par exemple, si votre application Windows Forms lève une exception non gérée, vous verrez une boîte de dialogue comme suit :

     ![WindowsFormsUnhandledException](../debugger/media/windowsformsunhandledexception.png "WindowsFormsUnhandledException")

     Pour activer juste-à-temps le débogage d’une application Windows Forms, vous devez effectuer les étapes supplémentaires suivantes :

2.  Définir le `jitDebugging` valeur `true` dans le `system.windows.form` section du fichier machine.config ou  *\<nom_application >*. fichier exe.config :

    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

3.  Dans une application Windows Forms C++, vous devez également définir `DebuggableAttribute` dans un fichier .config ou dans votre code. Si vous compilez avec [/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format) et sans [/Og](/cpp/build/reference/og-global-optimizations), le compilateur définit cet attribut pour vous. Toutefois, si vous souhaitez déboguer une version Release non optimisée, vous devez le définir vous-même. Pour ce faire, ajoutez la ligne suivante au fichier AssemblyInfo.cpp de votre application :

    ```cpp
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
    ```

     Pour plus d'informations, consultez <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="a-namebkmkusingjituse-just-in-time-debugging"></a><a name="BKMK_Using_JIT">Utiliser le débogage juste-à-temps
 Cette section montre que se passe-t-il quand un fichier exécutable lève une exception.

 Vous devez disposer de Visual Studio est installé pour suivre ces étapes. Si vous n’avez pas Visual Studio, vous pouvez télécharger la version gratuite [Visual Studio Community Edition](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15).

 Assurez-vous que juste-à-temps de débogage est [activé](#BKMK_Enabling).

 Dans le cadre de cette section, nous veillerons à ce une application de console c# dans Visual Studio lève une [NullReferenceException](/dotnet/api/system.nullreferenceexception).

 Dans Visual Studio, créez une application de console c# (**fichier > Nouveau > projet > Visual c# > Application Console**) nommé **ThrowsNullException**. Pour plus d’informations sur la création de projets dans Visual Studio, consultez [procédure pas à pas : créer une Application Simple](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md).

 Lorsque le projet s’ouvre dans Visual Studio, ouvrez le fichier Program.cs. Remplacez la méthode Main() par le code suivant, qui imprime une ligne dans la console et puis lève une exception NullReferenceException :

```csharp
static void Main(string[] args)
{
    Console.WriteLine("we will now throw a NullReferenceException");
    throw new NullReferenceException("this is the exception thrown by the console app");
}
```

> [!IMPORTANT]
>  Afin que cette procédure fonctionne un [configuration release](../debugger/how-to-set-debug-and-release-configurations.md), vous devez désactiver [uniquement mon Code](../debugger/just-my-code.md). Dans Visual Studio, cliquez sur **Outils > Options**. Dans le **Options** boîte de dialogue, sélectionnez **débogage**. Décochez la case **activer uniquement mon Code**.

 Générez la solution (dans Visual Studio, choisissez **Générer > regénérer la Solution**). Vous pouvez choisir le débogage ou la configuration Release (choisissez **déboguer** pour l’expérience de débogage complète). Pour plus d’informations sur les configurations de build, consultez [Présentation des configurations de build](../ide/understanding-build-configurations.md).

 Le processus de génération crée un exécutable ThrowsNullException.exe. Vous pouvez le trouver sous le dossier où vous avez créé le projet c# : **...\ThrowsNullException\ThrowsNullException\bin\Debug** ou **...\ThrowsNullException\ThrowsNullException\bin\Release**.

 Double-cliquez sur le ThrowsNullException.exe. Vous devez voir une fenêtre de commande comme suit :

 ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")

 Après quelques secondes, un message d’erreur apparaît :

 ![ThrowsNullExceptionError](../debugger/media/throwsnullexceptionerror.png "ThrowsNullExceptionError")

 Ne cliquez pas sur **Annuler**! Après quelques secondes, vous devriez voir deux boutons, **déboguer** et **fermer le programme**. Cliquez sur **déboguer**.

> [!CAUTION]
>  Si votre application contient le code non fiable, une boîte de dialogue avec un avertissement de sécurité s’affiche. Cette boîte de dialogue vous permet de décider s'il faut poursuivre ou non le débogage. Avant de continuer le débogage, déterminez si vous faites confiance au code. Avez-vous écrit le code vous-même ? Faites-vous confiance à l'auteur du code ? Si l'application s'exécute sur un ordinateur distant, reconnaissez-vous le nom du processus ? Même si l'application s'exécute localement, cela ne signifie pas nécessairement qu'elle peut être approuvée. Envisagez la possibilité de code malveillant s’exécute sur votre ordinateur. Si vous décidez que le code vous vous apprêtez à déboguer est fiable, cliquez sur **déboguer**. Sinon, cliquez sur **ne déboguez pas**.

 Le **débogueur de Visual Studio juste à temps** fenêtre s’affiche :

 ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")

 Sous **débogueurs possibles**, vous devez voir que la **nouvelle instance de Microsoft Visual Studio <available version>**  ligne est sélectionnée. S’il n’est pas déjà sélectionné, sélectionnez maintenant.

 En bas de la fenêtre, sous **vous souhaitez déboguer à l’aide du débogueur sélectionné ?**, cliquez sur **Oui**.

 Le projet ThrowsNullException s’ouvre dans une nouvelle instance de Visual Studio, avec l’exécution s’est arrêtée à la ligne qui lève l’exception :

 ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

 Vous pouvez démarrer le débogage à ce stade. S’il s’agissait d’une application réelle, vous devez savoir pourquoi le code lève l’exception.

## <a name="just-in-time-debugging-errors"></a>Erreurs du débogage juste-à-temps
 Si vous ne voyez pas la boîte de dialogue lorsque le programme se bloque, le problème est peut-être en raison des paramètres de rapport d’erreurs Windows sur votre ordinateur. Pour plus d’informations, consultez [. Paramètres de rapport d’erreurs Windows](/windows-hardware/drivers/dashboard/windows-error-reporting-getting-started).

 Vous pouvez voir s'afficher les messages d'erreur suivants associés au débogage juste-à-temps.

-   **Impossible de s’attacher au processus bloqué. Le programme spécifié n’est pas un programme Windows ou MS-DOS.**

     Cette erreur se produit lorsque vous essayez d’attacher à un processus en cours d’exécution en tant qu’un autre utilisateur.

     Pour contourner ce problème, démarrez Visual Studio, ouvrez le **attacher au processus** boîte de dialogue à partir de la **déboguer** menu, puis recherchez le processus à déboguer dans la **processus disponibles**liste. Si vous ne connaissez pas le nom du processus, examinez le **débogueur de Visual Studio juste à temps** boîte de dialogue et notez l’ID de processus. Sélectionnez le processus dans le **processus disponibles** liste et cliquez sur **attacher**. Dans le **débogueur de Visual Studio juste à temps** boîte de dialogue, cliquez sur **non** pour faire disparaître la boîte de dialogue.

-   **Débogueur n’a pas pu être démarré, car aucun utilisateur n’est connecté.**

     Cette erreur se produit lorsque le débogage juste-à-temps tente de démarrer Visual Studio sur un ordinateur où aucun utilisateur n'a ouvert de session sur la console. Dans la mesure où aucun utilisateur n'a ouvert de session, il n'y a aucune session utilisateur pour afficher la boîte de dialogue Débogage juste-à-temps.

     Pour résoudre ce problème, ouvrez une session sur l'ordinateur.

-   **Classe non inscrite.**

     Cette erreur indique que le débogueur a essayé de créer une classe COM qui n'est pas inscrite, probablement en raison d'un problème d'installation.

     Pour résoudre ce problème, utilisez le disque d'installation pour réinstaller ou réparer votre installation de Visual Studio.

## <a name="see-also"></a>Voir aussi
 [Sécurité du débogueur](../debugger/debugger-security.md) [principes fondamentaux du débogueur](../debugger/getting-started-with-the-debugger.md) [juste-à-temps, débogage, boîte de dialogue Options](../debugger/just-in-time-debugging-options-dialog-box.md) [avertissement de sécurité : l’attachement à un processus appartenant à un utilisateur non fiable peut être dangereux. Si les informations suivantes semblent suspectes ou si vous avez des doutes, ne faites pas d’attachement à ce processus](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
