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
ms.openlocfilehash: ad2814dffa75809a318dc7cebe7831b5ecec7d29
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690605"
---
# <a name="just-in-time-debugging-in-visual-studio"></a>Débogage just-in-time dans Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le débogage juste-à-temps lance Visual Studio automatiquement lorsqu’une exception ou un incident se produit dans une application qui s’exécute en dehors de Visual Studio. Cela vous permet de tester votre application lorsque Visual Studio n’est pas en cours d’exécution et de commencer le débogage avec Visual Studio lorsqu’un problème se produit.

Le débogage juste-à-temps fonctionne pour les applications de bureau Windows. Il ne fonctionne pas pour les applications universelles Windows et il ne fonctionne pas pour le code managé hébergé dans une application native, telle que les visualiseurs.

## <a name="did-the-just-in-time-debugger-dialog-box-appear-when-trying-to-run-an-app"></a><a name="BKMK_Scenario"></a> La boîte de dialogue du débogueur juste-à-temps s’affiche-t-elle lors de la tentative d’exécution d’une application ?

Les mesures que vous devez prendre lorsque vous voyez la boîte de dialogue débogueur juste-à-temps de Visual Studio dépendent de ce que vous essayez de faire :

#### <a name="if-you-want-to-get-rid-of-the-dialog-box-and-just-run-the-app-normally"></a>Si vous souhaitez vous débarrasser de la boîte de dialogue et exécuter simplement l’application normalement

1. (Utilisateurs avancés) Si vous avez installé Visual Studio (ou si vous l’avez installé précédemment et que vous l’avez supprimé), [désactivez le débogage juste-à-temps](#BKMK_Enabling) et réessayez d’exécuter l’application.

2. Si vous exécutez une application Web dans Internet Explorer, désactivez le débogage de script.

    Désactivez le débogage de script dans la boîte de dialogue Options Internet. Vous pouvez y accéder à partir du **panneau de configuration**  /  **Network and Internet**  /  **Options Internet** et Internet (les étapes exactes dépendent de votre version de Windows et d’Internet Explorer).

    ![JITInternetOptions](../debugger/media/jitinternetoptions.png "JITInternetOptions")

3. Rouvrez la page Web où vous avez trouvé l’erreur. Si cela ne résout pas le problème, contactez le propriétaire de l’application Web pour résoudre le problème.

4. Si vous exécutez un autre type d’application Windows, vous devrez contacter le propriétaire de l’application pour corriger l’erreur, puis réinstaller la version corrigée de l’application.

#### <a name="if-you-want-to-fix-or-debug-the-error-advanced-users"></a>Si vous souhaitez corriger ou déboguer l’erreur (utilisateurs expérimentés)

- Vous devez avoir [installé Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) pour afficher les informations détaillées sur l’erreur et tenter de la déboguer. Pour obtenir des instructions détaillées, consultez [utilisation de JIT](#BKMK_Using_JIT) . Si vous ne parvenez pas à résoudre l’erreur et à corriger l’application, contactez le propriétaire de l’application pour résoudre l’erreur.

## <a name="enable-or-disable-just-in-time-debugging"></a><a name="BKMK_Enabling"></a> Activer ou désactiver le débogage juste-à-temps
 Vous pouvez activer ou désactiver le débogage juste-à-temps à partir de la boîte de dialogue **Outils/Options** de Visual Studio.

#### <a name="to-enable-or-disable-just-in-time-debugging"></a>Pour activer ou désactiver le débogage juste-à-temps

1. Ouvrez Visual Studio. Dans le menu **Outils** , cliquez sur **Options**.

2. Dans la boîte de dialogue **options** , sélectionnez le dossier **débogage** .

3. Dans le dossier **débogage** , sélectionnez la page **juste-à-temps** .

4. Dans la zone **activer le débogage juste-à-temps de ces types de code** , sélectionnez ou désactivez les types de programmes appropriés : **managé**, **natif**ou **script**.

    Pour désactiver le débogage juste-à-temps, vous devez travailler avec des privilèges de niveau administrateur. L'activation du débogage juste-à-temps définit une clé de Registre, que vous ne pouvez modifier que si vous disposez des privilèges d'administrateur.

5. Cliquez sur **OK**.

   Le débogage juste-à-temps peut toujours être activé même si Visual Studio n'est plus installé sur votre ordinateur. Lorsque Visual Studio n’est pas installé, vous ne pouvez pas désactiver le débogage juste-à-temps dans la boîte de dialogue **options** de Visual Studio. Dans ce cas, vous pouvez désactiver le débogage juste-à-temps en modifiant le Registre Windows.

#### <a name="to-disable-just-in-time-debugging-by-editing-the-registry"></a>Pour désactiver le débogage juste-à-temps en modifiant le Registre

1. Dans le menu **Démarrer** , recherchez et exécutez `regedit.exe`

2. Dans la fenêtre de l' **éditeur du Registre** , recherchez et supprimez les entrées de Registre suivantes :

    - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\DbgManagedDebugger

3. Si votre ordinateur exécute un système d’exploitation 64 bits, supprimez également les entrées de Registre suivantes :

    - HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    - HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\DbgManagedDebugger

4. Veillez à ne pas supprimer ou modifier par inadvertance d'autres clés de Registre.

5. Fermez la fenêtre **Éditeur du Registre**.

> [!NOTE]
> Si vous essayez de désactiver le débogage juste-à-temps pour une application côté serveur et que ces étapes ne résolvent pas le problème, désactivez le débogage côté serveur dans les paramètres d’application IIS et réessayez.

#### <a name="to-enable-just-in-time-debugging-of-a-windows-form"></a>Pour activer le débogage juste-à-temps d'un Windows Forms

1. Par défaut, les applications Windows Forms ont un gestionnaire d’exceptions de haut niveau qui permet au programme de continuer à s’exécuter s’il peut être récupéré. Par exemple, si votre application Windows Forms lève une exception non gérée, vous verrez une boîte de dialogue semblable à la suivante :

     ![WindowsFormsUnhandledException](../debugger/media/windowsformsunhandledexception.png "WindowsFormsUnhandledException")

     Pour activer le débogage juste-à-temps d’une application Windows Forms, vous devez effectuer les étapes supplémentaires suivantes :

2. Définissez la `jitDebugging` valeur sur `true` dans la `system.windows.form` section du fichier machine.config ou *\<application name>*.exe.config :

    ```
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

3. Dans une application Windows Forms C++, vous devez également définir `DebuggableAttribute` dans un fichier .config ou dans votre code. Si vous effectuez la compilation avec [/Zi](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) et sans [/Og](https://msdn.microsoft.com/library/d10630cc-b9cf-4e97-bde3-8d7ee79e9435), le compilateur définit cet attribut pour vous. Toutefois, si vous souhaitez déboguer une version Release non optimisée, vous devez le définir vous-même. Pour ce faire, ajoutez la ligne suivante au fichier AssemblyInfo.cpp de votre application :

    ```
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
    ```

     Pour plus d'informations, consultez <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="a-namebkmk_using_jituse-just-in-time-debugging"></a><a name="BKMK_Using_JIT">Utiliser le débogage juste-à-temps
 Cette section montre ce qui se passe lorsqu’un exécutable lève une exception.

 Vous devez avoir installé Visual Studio pour suivre ces étapes. Si vous ne disposez pas de Visual Studio, vous pouvez télécharger la version gratuite de [Visual studio 2015 Community Edition](https://visualstudio.microsoft.com/vs/older-downloads/).

 Lorsque vous installez Visual Studio, le débogage juste-à-temps est activé par défaut.

 Dans le cadre de cette section, nous allons créer une application console C# dans Visual Studio qui lève une exception <xref:System.NullReferenceException> .

 Dans Visual Studio, créez une application console C# (**fichier/nouveau/projet/Visual C#/application console**) nommée **ThrowsNullException**. Pour plus d’informations sur la création de projets dans Visual Studio, consultez [procédure pas à pas : création d’une application simple](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md).

 Lorsque le projet s’ouvre dans Visual Studio, ouvrez le fichier Program.cs. Remplacez la méthode main () par le code suivant, qui imprime une ligne dans la console, puis lève une exception NullReferenceException :

```csharp
static void Main(string[] args)
{
    Console.WriteLine("we will now throw a NullReferenceException");
    throw new NullReferenceException("this is the exception thrown by the console app");
}
```

> [!IMPORTANT]
> Pour que cette procédure fonctionne dans une [configuration Release](../debugger/how-to-set-debug-and-release-configurations.md), vous devez désactiver [uniquement mon code](../debugger/just-my-code.md). Dans Visual Studio, cliquez sur **Outils/Options**. Dans la boîte de dialogue **options** , sélectionnez **débogage**. Désactivez la case à cocher **activer uniquement mon code**.

 Générez la solution (dans Visual Studio, choisissez **générer/régénérer la solution**). Vous pouvez choisir la configuration Debug ou Release. Pour plus d’informations sur les configurations de build, consultez [Présentation des configurations de build](../ide/understanding-build-configurations.md).

 Le processus de génération crée un ThrowsNullException.exe exécutable. Vous pouvez le trouver dans le dossier dans lequel vous avez créé le projet C# : **. ..\ThrowsNullException\ThrowsNullException\bin\Debug** ou **. ..\ThrowsNullException\ThrowsNullException\bin\Release**.

 Double-cliquez sur l' ThrowsNullException.exe. Une fenêtre de commande semblable à celle-ci doit s’afficher :

 ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")

 Après quelques secondes, une fenêtre d’erreur s’affiche :

 ![ThrowsNullExceptionError](../debugger/media/throwsnullexceptionerror.png "ThrowsNullExceptionError")

 Ne cliquez pas sur **Annuler**. Au bout de quelques secondes, vous devez voir deux boutons : **Déboguer** et **Fermer le programme**. Cliquez sur **Déboguer**.

> [!CAUTION]
> Si votre application contient du code non fiable, une boîte de dialogue comportant un avertissement de sécurité s’affiche. Cette boîte de dialogue vous permet de décider s'il faut poursuivre ou non le débogage. Avant de continuer le débogage, déterminez si vous faites confiance au code. Avez-vous écrit le code vous-même ? Faites-vous confiance à l'auteur du code ? Si l'application s'exécute sur un ordinateur distant, reconnaissez-vous le nom du processus ? Même si l'application s'exécute localement, cela ne signifie pas nécessairement qu'elle peut être approuvée. Envisagez la possibilité que du code malveillant s’exécute sur votre ordinateur. Si vous décidez que le code que vous allez déboguer est fiable, cliquez sur **Déboguer**. Sinon, cliquez sur **ne pas déboguer**.

 La fenêtre du **Débogueur juste-à-temps Visual Studio** s’affiche :

 ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")

 Sous les **Débogueurs possibles**, vous devez voir que la **nouvelle instance de Microsoft Visual Studio ligne 2015** est sélectionnée. S’il n’est pas déjà sélectionné, sélectionnez-le maintenant.

 En bas de la fenêtre, sous voulez **-vous effectuer le débogage à l’aide du débogueur sélectionné ?**, cliquez sur **Oui**.

 Le projet ThrowsNullException s’ouvre dans une nouvelle instance de Visual Studio, avec l’exécution arrêtée à la ligne qui lève l’exception :

 ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

 Vous pouvez démarrer le débogage à ce stade. S’il s’agissait d’une application réelle, vous devez déterminer la raison pour laquelle le code a levé l’exception.

## <a name="just-in-time-debugging-errors"></a>Erreurs du débogage juste-à-temps
 Si vous ne voyez pas la boîte de dialogue lorsque le programme se bloque, cela peut être dû à Rapport d’erreurs Windows paramètres sur votre ordinateur. Pour plus d’informations, consultez [. Paramètres WER](https://msdn.microsoft.com/library/windows/desktop/bb513638\(v=vs.85\).aspx).

 Vous pouvez voir s'afficher les messages d'erreur suivants associés au débogage juste-à-temps.

- **Impossible de s’attacher au processus bloqué. Le programme spécifié n’est pas un programme Windows ou MS-DOS.**

     Cette erreur se produit lorsque vous essayez d’attacher un processus s’exécutant en tant qu’autre utilisateur.

     Pour contourner ce problème, démarrez Visual Studio, ouvrez la boîte de dialogue **attacher au processus** dans le menu **Déboguer** , puis recherchez le processus que vous souhaitez déboguer dans la liste **processus disponibles** . Si vous ne connaissez pas le nom du processus, consultez la boîte de dialogue **Débogueur juste-à-temps Visual Studio** et notez l’ID du processus. Sélectionnez le processus dans la liste **processus disponibles** , puis cliquez sur **attacher**. Dans la boîte de dialogue **Débogueur juste-à-temps Visual Studio** , cliquez sur **non** pour fermer la boîte de dialogue.

- **Impossible de démarrer le débogueur, car aucun utilisateur n'est connecté.**

     Cette erreur se produit lorsque le débogage juste-à-temps tente de démarrer Visual Studio sur un ordinateur où aucun utilisateur n'a ouvert de session sur la console. Dans la mesure où aucun utilisateur n'a ouvert de session, il n'y a aucune session utilisateur pour afficher la boîte de dialogue Débogage juste-à-temps.

     Pour résoudre ce problème, ouvrez une session sur l'ordinateur.

- **Classe non inscrite.**

     Cette erreur indique que le débogueur a essayé de créer une classe COM qui n'est pas inscrite, probablement en raison d'un problème d'installation.

     Pour résoudre ce problème, utilisez le disque d'installation pour réinstaller ou réparer votre installation de Visual Studio.

## <a name="see-also"></a>Voir aussi
 [Debugger Security](../debugger/debugger-security.md) [Concepts de base](../debugger/debugger-basics.md) du débogueur sécurité du débogueur [juste-à-temps, débogage, boîte de dialogue Options](../debugger/just-in-time-debugging-options-dialog-box.md) [avertissement de sécurité : l’attachement à un processus appartenant à un utilisateur non fiable peut être dangereux. Si les informations suivantes semblent suspectes ou si vous n’êtes pas sûr, ne vous attachez pas à ce processus](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015)
