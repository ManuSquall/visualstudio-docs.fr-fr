---
title: "D&#233;bogage just-in-time dans Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "CSharp"
  - "VB"
helpviewer_keywords: 
  - "déboguer (Visual Studio), Juste-à-temps"
  - "débogage juste-à-temps"
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
caps.latest.revision: 48
caps.handback.revision: 40
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# D&#233;bogage just-in-time dans Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le débogage juste\-à\-temps lance Visual Studio automatiquement lorsqu'une exception ou un incident se produit dans une application qui s'exécute hors de Visual Studio.  Cela vous permet de tester votre application lorsque Visual Studio n'est pas en cours d'exécution et de démarrer le débogage avec Visual Studio lorsqu'un problème se produit.  
  
 Le débogage juste\-à\-temps ne fonctionne pas pour les applications Windows Store.  Le débogage juste\-à\-temps ne fonctionne pas pour le code managé hébergé dans une application native, par exemple les visualiseurs.  
  
## Utilisation du débogage juste\-à\-temps  
 Lorsque vous installez Visual Studio, le débogage juste\-à\-temps est activé par défaut.  Si vous devez désactiver ou réactiver le débogage juste\-à\-temps, consultez [Restreindre le pas à pas jusqu'à Uniquement mon code](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code).  
  
 Lorsque le débogage juste\-à\-temps est activé, vous pouvez tester votre application hors de Visual Studio.  Lorsqu'un incident ou une exception se produit, vous voyez une boîte de dialogue s'afficher avec un message similaire à ceci :  
  
 Une exception non gérée \('System.TypeInitializationException'\) s'est produite dans terrarium.exe \[3384\]  
  
 Lorsque cette boîte de dialogue s'affiche, vous pouvez commencer le débogage à l'aide de la procédure suivante.  
  
#### Pour commencer le débogage juste\-à\-temps lorsqu'une erreur se produit  
  
1.  Dans la boîte de dialogue Débogage juste\-à\-temps, dans la liste **Débogueurs possibles**, cliquez sur **Nouvelle instance de Visual Studio 2015** ou sur une instance de Visual Studio déjà en cours d'exécution.  
  
2.  Pour utiliser automatiquement Visual Studio pour tous les incidents futurs, cliquez sur **Utiliser par défaut le débogueur sélectionné actuellement**.  
  
3.  Si vous voulez choisir les types de code que vous pourrez déboguer, cliquez sur **Choisir manuellement les moteurs de débogage**.  Si vous ne choisissez pas cette option, Visual Studio sélectionne automatiquement les moteurs de débogage qui conviennent au type de code de votre programme.  
  
4.  Cliquez sur **OK**.  
  
5.  Si votre application contient un assembly avec du code non fiable, une boîte de dialogue comportant un avertissement de sécurité s'affiche.  Cette boîte de dialogue vous permet de décider s'il faut poursuivre ou non le débogage.  Avant de continuer le débogage, déterminez si vous faites confiance au code.  Avez\-vous écrit le code vous\-même ?  Faites\-vous confiance à l'auteur du code ?  Si l'application s'exécute sur un ordinateur distant, reconnaissez\-vous le nom du processus ?  Même si l'application s'exécute localement, cela ne signifie pas nécessairement qu'elle peut être approuvée.  Dans Internet Explorer, par exemple, un contrôle ActiveX malveillant peut s'exécuter.  Envisagez la possibilité que du code malveillant s'exécute sur votre ordinateur.  Si vous décidez que le code que vous allez déboguer est fiable, cliquez sur **Déboguer**.  Sinon, cliquez sur **Ne pas déboguer**.  
  
##  <a name="BKMK_Enabling"></a> Activation ou désactivation du débogage juste\-à\-temps  
 Vous pouvez activer ou désactiver le débogage juste\-à\-temps dans la boîte de dialogue **Options**.  
  
#### Pour activer ou désactiver le débogage juste\-à\-temps  
  
1.  Dans le menu **Outils**, cliquez sur **Options**.  
  
2.  Dans la boîte de dialogue **Options**, sélectionnez le dossier **Débogage**.  
  
3.  Dans le dossier **Débogage**, sélectionnez la page **Juste\-à\-temps**.  
  
4.  Dans la zone **Activer le débogage juste\-à\-temps** de ces types de code, sélectionnez ou désactivez les types de programmes adéquats : **Managé**, **Natif** ou **Script**.  
  
     Pour désactiver le débogage juste\-à\-temps, vous devez travailler avec des privilèges de niveau administrateur.  L'activation du débogage juste\-à\-temps définit une clé de Registre, que vous ne pouvez modifier que si vous disposez des privilèges d'administrateur.  
  
5.  Cliquez sur **OK**.  
  
 Par défaut, les applications Windows Forms ont un gestionnaire d'exceptions de haut niveau qui permet au programme de continuer à s'exécuter  s'il peut être récupéré.  Par conséquent, vous devez procéder comme suit pour activer le débogage juste\-à\-temps d'une application Windows Forms.  
  
#### Pour activer le débogage juste\-à\-temps d'un Windows Forms  
  
1.  Définissez la valeur de `jitDebugging` sur `true` dans la section `system.windows.form` du fichier machine.config ou *application*.exe.config :  
  
    ```  
    <configuration>  
        <system.windows.forms jitDebugging="true" />  
    </configuration>  
    ```  
  
2.  Dans une application Windows Forms C\+\+, vous devez également définir `DebuggableAttribute` dans un fichier .config ou dans votre code.  Si vous effectuez la compilation avec [\/Zi](/visual-cpp/build/reference/z7-zi-zi-debug-information-format) et sans [\/Og](/visual-cpp/build/reference/og-global-optimizations), le compilateur définit cet attribut pour vous.  Toutefois, si vous souhaitez déboguer une version Release non optimisée, vous devez le définir vous\-même.  Pour ce faire, ajoutez la ligne suivante au fichier AssemblyInfo.cpp de votre application :  
  
    ```  
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];   
    ```  
  
     Pour plus d'informations, consultez <xref:System.Diagnostics.DebuggableAttribute>.  
  
 Le débogage juste\-à\-temps peut toujours être activé même si Visual Studio n'est plus installé sur votre ordinateur.  Lorsque Visual Studio n'est pas installé, vous ne pouvez pas désactiver le débogage juste\-à\-temps dans la boîte de dialogue **Options** de Visual Studio.  Dans ce cas, vous pouvez désactiver le débogage juste\-à\-temps en modifiant le Registre Windows.  
  
#### Pour désactiver le débogage juste\-à\-temps en modifiant le Registre  
  
1.  Dans le menu **Démarrer**, recherchez et exécutez le fichier `regedit.exe`  
  
2.  Dans la fenêtre **Éditeur du Registre**, recherchez et supprimez les clés de Registre suivantes :  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Windows NT\\CurrentVersion\\AeDebug\\Debugger  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\.NETFramework\\DbgManagedDebugger  
  
3.  Si votre ordinateur exécute un système d'exploitation 64 bits, supprimez également les clés de Registre suivantes :  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\Windows NT\\CurrentVersion\\AeDebug\\Debugger  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\.NETFramework\\DbgManagedDebugger  
  
4.  Veillez à ne pas supprimer ou modifier par inadvertance d'autres clés de Registre.  
  
5.  Fermez la fenêtre **Éditeur du Registre**.  
  
## Erreurs du débogage juste\-à\-temps  
 Vous pouvez voir s'afficher les messages d'erreur suivants associés au débogage juste\-à\-temps.  
  
-   **Impossible de s'attacher au processus bloqué.  Le programme spécifié n'est pas un programme Windows ou MS\-DOS.**  
  
     Cette erreur se produit lorsque vous essayez de vous attacher à un processus qui s'exécute comme un autre utilisateur sous Windows 2000.  
  
     Pour contourner ce problème, démarrez Visual Studio, ouvrez la boîte de dialogue **Attacher au processus** à partir du menu **Déboguer**, puis recherchez le processus à déboguer dans la liste **Processus disponibles**.  Si vous ne connaissez pas le nom du processus, consultez la boîte de dialogue **Débogueur juste\-à\-temps Visual Studio** et notez l'ID de processus.  Sélectionnez le processus dans la liste **Processus disponibles** et cliquez sur **Attacher**.  Dans la boîte de dialogue **Débogueur juste\-à\-temps Visual Studio**, cliquez sur **Non** pour fermer la boîte de dialogue.  
  
-   **Impossible de démarrer le débogueur car aucun utilisateur n'est connecté.**  
  
     Cette erreur se produit lorsque le débogage juste\-à\-temps tente de démarrer Visual Studio sur un ordinateur où aucun utilisateur n'a ouvert de session sur la console.  Dans la mesure où aucun utilisateur n'a ouvert de session, il n'y a aucune session utilisateur pour afficher la boîte de dialogue Débogage juste\-à\-temps.  
  
     Pour résoudre ce problème, ouvrez une session sur l'ordinateur.  
  
-   **Classe non inscrite.**  
  
     Cette erreur indique que le débogueur a essayé de créer une classe COM qui n'est pas inscrite, probablement en raison d'un problème d'installation.  
  
     Pour résoudre ce problème, utilisez le disque d'installation pour réinstaller ou réparer votre installation de Visual Studio.  
  
## Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Principes de base du débogueur](../debugger/debugger-basics.md)   
 [Juste\-à\-temps, Débogage, boîte de dialogue Options](../debugger/just-in-time-debugging-options-dialog-box.md)   
 [Avertissement de sécurité : L'attachement à un processus appartenant à un utilisateur non fiable peut être dangereux. Si les informations suivantes semblent suspectes ou en cas de doutes, n'attachez pas ce processus.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md)