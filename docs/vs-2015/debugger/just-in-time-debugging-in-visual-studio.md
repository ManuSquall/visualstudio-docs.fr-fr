---
title: le débogage juste-à-temps
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
- CSharp
- VB
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
caps.latest.revision: 51
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ca4c3e5016377758e8910c15bf992e629778c0e9
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "59001441"
---
# <a name="just-in-time-debugging-in-visual-studio"></a>Débogage just-in-time dans Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le débogage juste-à-temps lance Visual Studio automatiquement lorsqu’une exception ou un incident se produit dans une application qui s’exécute en dehors de Visual Studio. Cela vous permet de tester votre application lorsque Visual Studio n’est pas en cours d’exécution et commencez le débogage avec Visual Studio lorsqu’un problème survient.

Fonctionne avec le débogage juste-à-temps pour les applications de bureau Windows. Il ne fonctionne pas pour les applications Windows universelles, et il ne fonctionne pas pour le code managé qui est hébergé dans une application native, par exemple les visualiseurs.

## <a name="BKMK_Scenario"></a> Avez-vous juste-à-temps débogueur boîte de dialogue apparaît lorsque vous tentez d’exécuter une application ?

Les actions que vous devez prendre lorsque vous voyez le Visual Studio juste-à-temps boîte de dialogue de débogueur dépendent de ce que vous essayez de faire :

#### <a name="if-you-want-to-get-rid-of-the-dialog-box-and-just-run-the-app-normally"></a>Si vous souhaitez vous débarrasser de la boîte de dialogue et juste exécuter normalement l’application

1. (Les utilisateurs expérimentés) Si vous avez installé Visual Studio (ou si vous l’ai déjà installé et supprimiez), [juste-à-temps de désactiver le débogage](#BKMK_Enabling) et essayez à nouveau exécuter l’application.

2. Si vous exécutez une application web dans Internet Explorer, désactivez le débogage de script.

    Désactiver le débogage de script dans la boîte de dialogue Options Internet. Vous pouvez accéder à cet élément depuis le **le panneau de configuration** / **réseau et Internet** / **Options Internet** (les étapes exactes dépendent de votre version de Windows et Internet Explorer).

    ![JITInternetOptions](../debugger/media/jitinternetoptions.png "JITInternetOptions")

3. Ouvrez à nouveau la page web où vous avez trouvé l’erreur. Si cela ne résout pas le problème, contactez le propriétaire de l’application web pour résoudre le problème.

4. Si vous exécutez un autre type d’application de Windows, vous devrez contacter le propriétaire de l’application pour corriger cette erreur, puis réinstaller la version corrigée de l’application.

#### <a name="if-you-want-to-fix-or-debug-the-error-advanced-users"></a>Si vous souhaitez corriger ou de déboguer l’erreur (utilisateurs expérimentés)

- Vous devez avoir [Visual Studio installé](https://visualstudio.microsoft.com/vs/older-downloads/) pour afficher les informations détaillées sur l’erreur et essayez de déboguer. Consultez [JIT à l’aide de](#BKMK_Using_JIT) pour obtenir des instructions détaillées. Si vous ne pouvez pas résoudre l’erreur et corriger l’application, contactez le propriétaire de l’application pour résoudre l’erreur.

##  <a name="BKMK_Enabling"></a> Activer ou désactiver juste-à-temps le débogage
 Vous pouvez activer ou désactiver le débogage à partir de Visual Studio juste-à-temps **Outils / Options** boîte de dialogue.

#### <a name="to-enable-or-disable-just-in-time-debugging"></a>Pour activer ou désactiver le débogage juste-à-temps

1. Ouvrez Visual Studio. Dans le menu **Outils**, cliquez sur **Options**.

2. Dans le **Options** boîte de dialogue, sélectionnez le **débogage** dossier.

3. Dans le **débogage** dossier, sélectionnez le **juste-à-temps** page.

4. Dans le **activer le débogage de ces types de code** zone, sélectionnez ou désactivez les types de programmes adéquats : **Managed**, **natif**, ou **Script**.

    Pour désactiver le débogage juste-à-temps, vous devez travailler avec des privilèges de niveau administrateur. L'activation du débogage juste-à-temps définit une clé de Registre, que vous ne pouvez modifier que si vous disposez des privilèges d'administrateur.

5. Cliquez sur **OK**.

   Le débogage juste-à-temps peut toujours être activé même si Visual Studio n'est plus installé sur votre ordinateur. Lorsque Visual Studio n’est pas installé, vous ne pouvez pas désactiver le débogage à partir de Visual Studio juste-à-temps **Options** boîte de dialogue. Dans ce cas, vous pouvez désactiver le débogage juste-à-temps en modifiant le Registre Windows.

#### <a name="to-disable-just-in-time-debugging-by-editing-the-registry"></a>Pour désactiver le débogage juste-à-temps en modifiant le Registre

1.  Sur le **Démarrer** menu, recherchez et exécutez `regedit.exe`

2.  Dans le **Éditeur du Registre** fenêtre, recherchez, puis supprimez les entrées de Registre suivante :

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\DbgManagedDebugger

3.  Si votre ordinateur exécute un système d’exploitation de 64 bits, supprimez également les entrées de Registre suivantes :

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\DbgManagedDebugger

4.  Veillez à ne pas supprimer ou modifier par inadvertance d'autres clés de Registre.

5.  Fermer le **Éditeur du Registre** fenêtre.

> [!NOTE]
>  Si vous essayez de désactiver le débogage d’une application côté serveur juste-à-temps et que ces étapes ne résolvent pas le problème, désactivez le débogage côté serveur dans les paramètres d’application IIS et recommencez.

#### <a name="to-enable-just-in-time-debugging-of-a-windows-form"></a>Pour activer le débogage juste-à-temps d'un Windows Forms

1.  Par défaut, les applications Windows Forms ont un gestionnaire d’exceptions de haut niveau qui permet au programme de continuer à s’exécuter s’il peut être récupéré. Par exemple, si votre application Windows Forms lève une exception non gérée, vous verrez une boîte de dialogue comme suit :

     ![WindowsFormsUnhandledException](../debugger/media/windowsformsunhandledexception.png "WindowsFormsUnhandledException")

     Pour activer juste-à-temps le débogage d’une application Windows Forms, vous devez effectuer les étapes supplémentaires suivantes :

2.  Définir le `jitDebugging` valeur `true` dans le `system.windows.form` section du fichier machine.config ou  *\<nom_application >*. fichier exe.config :

    ```
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

3.  Dans une application Windows Forms C++, vous devez également définir `DebuggableAttribute` dans un fichier .config ou dans votre code. Si vous effectuez la compilation avec [/Zi](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) et sans [/Og](http://msdn.microsoft.com/library/d10630cc-b9cf-4e97-bde3-8d7ee79e9435), le compilateur définit cet attribut pour vous. Toutefois, si vous souhaitez déboguer une version Release non optimisée, vous devez le définir vous-même. Pour ce faire, ajoutez la ligne suivante au fichier AssemblyInfo.cpp de votre application :

    ```
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
    ```

     Pour plus d'informations, consultez <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="a-namebkmkusingjituse-just-in-time-debugging"></a><a name="BKMK_Using_JIT">Utiliser le débogage juste-à-temps
 Cette section montre que se passe-t-il quand un fichier exécutable lève une exception.

 Vous devez disposer de Visual Studio est installé pour suivre ces étapes. Si vous n’avez pas Visual Studio, vous pouvez télécharger la version gratuite [Visual Studio 2015 Community Edition](https://visualstudio.microsoft.com/vs/older-downloads/).

 Lorsque vous installez Visual Studio, le débogage juste-à-temps est activé par défaut.

 Dans le cadre de cette section, nous veillerons à ce une application de console c# dans Visual Studio lève une <xref:System.NullReferenceException>.

 Dans Visual Studio, créez une application de console c# (**fichier / nouveau / projet / Visual C# / Application Console**) nommé **ThrowsNullException**. Pour plus d’informations sur la création de projets dans Visual Studio, consultez [procédure pas à pas : Créer une Application Simple](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md).

 Lorsque le projet s’ouvre dans Visual Studio, ouvrez le fichier Program.cs. Remplacez la méthode Main() par le code suivant, qui imprime une ligne dans la console et puis lève une exception NullReferenceException :

```csharp
static void Main(string[] args)
{
    Console.WriteLine("we will now throw a NullReferenceException");
    throw new NullReferenceException("this is the exception thrown by the console app");
}
```

> [!IMPORTANT]
>  Afin que cette procédure fonctionne un [configuration release](../debugger/how-to-set-debug-and-release-configurations.md), vous devez désactiver [uniquement mon Code](../debugger/just-my-code.md). Dans Visual Studio, cliquez sur **Outils / Options**. Dans le **Options** boîte de dialogue, sélectionnez **débogage**. Décochez la case **activer uniquement mon Code**.

 Générez la solution (dans Visual Studio, choisissez **générer / régénérer la Solution**). Vous pouvez choisir le débogage ou la configuration Release. Pour plus d’informations sur les configurations de build, consultez [Présentation des configurations de build](../ide/understanding-build-configurations.md).

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

 Sous **débogueurs possibles**, vous devez voir que la **nouvelle instance de Microsoft Visual Studio 2015** ligne est sélectionnée. S’il n’est pas déjà sélectionné, sélectionnez maintenant.

 En bas de la fenêtre, sous **vous souhaitez déboguer à l’aide du débogueur sélectionné ?**, cliquez sur **Oui**.

 Le projet ThrowsNullException s’ouvre dans une nouvelle instance de Visual Studio, avec l’exécution s’est arrêtée à la ligne qui lève l’exception :

 ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

 Vous pouvez démarrer le débogage à ce stade. S’il s’agissait d’une application réelle, vous devez savoir pourquoi le code lève l’exception.

## <a name="just-in-time-debugging-errors"></a>Erreurs du débogage juste-à-temps
 Si vous ne voyez pas la boîte de dialogue lorsque le programme se bloque, le problème est peut-être en raison des paramètres de rapport d’erreurs Windows sur votre ordinateur. Pour plus d’informations, consultez [. Paramètres de rapport d’erreurs Windows](https://msdn.microsoft.com/library/windows/desktop/bb513638\(v=vs.85\).aspx).

 Vous pouvez voir s'afficher les messages d'erreur suivants associés au débogage juste-à-temps.

-   **Impossible de s'attacher au processus bloqué. Le programme spécifié n'est pas un programme Windows ou MS-DOS.**

     Cette erreur se produit lorsque vous essayez d’attacher à un processus en cours d’exécution en tant qu’un autre utilisateur.

     Pour contourner ce problème, démarrez Visual Studio, ouvrez le **attacher au processus** boîte de dialogue à partir de la **déboguer** menu, puis recherchez le processus à déboguer dans la **processus disponibles**liste. Si vous ne connaissez pas le nom du processus, examinez le **débogueur de Visual Studio juste à temps** boîte de dialogue et notez l’ID de processus. Sélectionnez le processus dans le **processus disponibles** liste et cliquez sur **attacher**. Dans le **débogueur de Visual Studio juste à temps** boîte de dialogue, cliquez sur **non** pour faire disparaître la boîte de dialogue.

-   **Impossible de démarrer le débogueur, car aucun utilisateur n'est connecté.**

     Cette erreur se produit lorsque le débogage juste-à-temps tente de démarrer Visual Studio sur un ordinateur où aucun utilisateur n'a ouvert de session sur la console. Dans la mesure où aucun utilisateur n'a ouvert de session, il n'y a aucune session utilisateur pour afficher la boîte de dialogue Débogage juste-à-temps.

     Pour résoudre ce problème, ouvrez une session sur l'ordinateur.

-   **Classe non inscrite.**

     Cette erreur indique que le débogueur a essayé de créer une classe COM qui n'est pas inscrite, probablement en raison d'un problème d'installation.

     Pour résoudre ce problème, utilisez le disque d'installation pour réinstaller ou réparer votre installation de Visual Studio.

## <a name="see-also"></a>Voir aussi
 [Sécurité du débogueur](../debugger/debugger-security.md) [principes de base du débogueur](../debugger/debugger-basics.md) [juste-à-temps, débogage, Options, boîte de dialogue](../debugger/just-in-time-debugging-options-dialog-box.md) [avertissement de sécurité : l’attachement à un processus appartenant à un utilisateur non approuvé peut être dangereux. Si les informations suivantes semblent suspectes ou si vous avez des doutes, ne faites pas d’attachement à ce processus](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015)
