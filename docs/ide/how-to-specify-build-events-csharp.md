---
title: "Comment&#160;: sp&#233;cifier des &#233;v&#233;nements de build (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "événements de build (Visual Studio)"
  - "générations (Visual Studio), événements"
  - "événements (Visual Studio), builds"
  - "événements post-build"
  - "événements pré-build"
ms.assetid: b4ce1ad9-5215-4b6f-b6a2-798b249aa335
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Comment&#160;: sp&#233;cifier des &#233;v&#233;nements de build (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilisez des événements de build pour spécifier des commandes à exécuter avant que la génération commence ou après qu'elle se termine.  Les événements de build sont exécutés uniquement si la génération atteint ces étapes du processus de génération.  
  
 Lorsqu'un projet est généré, les événements pre\-build sont ajoutés à un fichier nommé PreBuildEvent.bat et les événements post\-build sont ajoutés à un fichier nommé PostBuildEvent.bat.  Si vous souhaitez garantir la vérification des erreurs, ajoutez vos propres commandes de vérification d'erreurs aux étapes de build.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Comment : spécifier des événements pre\-build et post\-build  
  
#### Pour spécifier un événement de build  
  
1.  Dans l'**Explorateur de solutions**, sélectionnez le projet pour lequel vous voulez spécifier l'événement de build.  
  
2.  Dans le menu **Projet**, cliquez sur **Propriétés**.  
  
3.  Sélectionnez l'onglet **Événements de build**.  
  
4.  Dans la zone **Ligne de commande de l'événement pre\-build**, spécifiez la syntaxe de l'événement de build.  
  
    > [!NOTE]
    >  Les événements avant génération ne s'exécutent pas si le projet est à jour et si aucune génération n'est déclenchée.  
  
5.  Dans la zone **Ligne de commande de l'événement près génération**, spécifiez la syntaxe de l'événement de build.  
  
    > [!NOTE]
    >  Ajoutez une instruction `call` avant toutes les commandes post\-build qui exécutent des fichiers .bat.  Par exemple, `call C:\MyFile.bat` ou `call C:\MyFile.bat call C:\MyFile2.bat`.  
  
6.  Dans la zone **Exécuter l'événement post\-build**, spécifiez sous quelles conditions exécuter l'événement post\-build.  
  
    > [!NOTE]
    >  Pour ajouter une syntaxe longue ou sélectionner des macros de génération à partir de [Ligne de commande de l’événement pré\-build\/post\-build, boîte de dialogue](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md), cliquez sur le bouton de sélection \(**…**\) pour afficher une zone d'édition.  
  
     La syntaxe de l'événement de build peut inclure toute commande valide sur l'invite de commandes ou dans un fichier .bat.  Le nom d'un fichier batch doit être précédé de `call` pour garantir l'exécution de toutes les commandes suivantes.  
  
     **Remarque** Si votre événement pre\-build ou post\-build ne se termine pas correctement, vous pouvez terminer la génération en quittant l'action d'événement avec un code autre que zéro \(0\), qui indique une action réussie.  
  
## Exemple : comment modifier les informations de manifeste à l'aide d'un événement post\-build  
 La procédure suivante montre comment définir la version minimale du système d'exploitation dans le manifeste de l'application à l'aide d'une commande .exe appelée à partir d'un événement post\-build \(le fichier .exe.manifest dans le répertoire du projet\).  La version minimale du système d'exploitation est un nombre en quatre parties, tel que 4.10.0.0.  À cette fin, la commande modifie la section `<dependentOS>` du manifeste :  
  
```  
<dependentOS>  
   <osVersionInfo>  
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
   </osVersionInfo>  
</dependentOS>  
```  
  
#### Pour créer une commande .exe afin de modifier le manifeste de l'application  
  
1.  Créez une application console pour la commande.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
2.  Dans la boîte de dialogue **Nouveau projet**, développez **Visual C\#**, cliquez sur **Windows**, puis sur le modèle **Application console**.  Nommez le projet `ModifierVersionSECS`.  
  
3.  Dans Program.cs, ajoutez la ligne suivante aux autres instructions `using` en haut du fichier :  
  
    ```  
    using System.Xml;  
    ```  
  
4.  Dans l'espace de noms `ChangeOSVersionCS`, remplacez l'implémentation de la classe `Program` par le code suivant :  
  
    ```  
    class Program  
    {  
       /// <summary>  
       /// This function will set the minimum operating system version for a ClickOnce application.  
       /// </summary>  
       /// <param name="args">  
       /// Command Line Arguments:  
       /// 0 - Path to application manifest (.exe.manifest).  
       /// 1 - Version of OS  
       ///</param>  
       static void Main(string[] args)  
       {  
          string applicationManifestPath = args[0];  
          Console.WriteLine("Application Manifest Path: " + applicationManifestPath);  
  
          // Get version name.  
          Version osVersion = null;  
          if (args.Length >=2 ){  
             osVersion = new Version(args[1]);  
          }else{  
             throw new ArgumentException("OS Version not specified.");  
          }  
          Console.WriteLine("Desired OS Version: " + osVersion.ToString());  
  
          XmlDocument document;  
          XmlNamespaceManager namespaceManager;  
          namespaceManager = new XmlNamespaceManager(new NameTable());  
          namespaceManager.AddNamespace("asmv1", "urn:schemas-microsoft-com:asm.v1");  
          namespaceManager.AddNamespace("asmv2", "urn:schemas-microsoft-com:asm.v2");  
  
          document = new XmlDocument();  
          document.Load(applicationManifestPath);  
  
          string baseXPath;  
          baseXPath = "/asmv1:assembly/asmv2:dependency/asmv2:dependentOS/asmv2:osVersionInfo/asmv2:os";  
  
          // Change minimum required operating system version.  
          XmlNode node;  
          node = document.SelectSingleNode(baseXPath, namespaceManager);  
          node.Attributes["majorVersion"].Value = osVersion.Major.ToString();  
          node.Attributes["minorVersion"].Value = osVersion.Minor.ToString();  
          node.Attributes["buildNumber"].Value = osVersion.Build.ToString();  
          node.Attributes["servicePackMajor"].Value = osVersion.Revision.ToString();  
  
          document.Save(applicationManifestPath);  
       }  
    }  
    ```  
  
     La commande prend deux arguments : le chemin d'accès du manifeste de l'application \(autrement dit, le dossier dans lequel le processus de génération crée le manifeste, en général NomProjet.publish\), et la nouvelle version du système d'exploitation.  
  
5.  Générez le projet.  Dans le menu **Générer**, cliquez sur **Générer la solution**.  
  
6.  Copiez le fichier .exe vers un répertoire tel que `C:\TEMP\ModifierVersionSEVB.exe`.  
  
 Ensuite, appelez cette commande dans un événement post\-build pour modifier le manifeste de l'application.  
  
#### Pour appeler un événement post\-build afin de modifier le manifeste de l'application  
  
1.  Créez une application Windows pour le projet à publier.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
2.  Dans la boîte de dialogue **Nouveau projet**, développez **Visual C\#**, cliquez sur **Windows**, puis sur le modèle **Application Windows Forms**.  Nommez le projet `AppWinCS`.  
  
3.  Un projet étant sélectionné dans l'**Explorateur de solutions**, cliquez dans le menu **Projet** sur **Propriétés**.  
  
4.  Dans le Concepteur de projets, accédez à la page **Publier** et définissez **Emplacement de publication** avec la valeur `C:\TEMP\`.  
  
5.  Publiez le projet en cliquant sur **Publier maintenant.**  
  
     Le fichier manifeste est généré et placé dans `C:\TEMP\CSWinApp_1_0_0_0\CSWinApp.exe.manifest`.  Pour consulter le manifeste, cliquez avec le bouton droit sur le fichier et cliquez sur **Ouvrir avec**, puis sur **Sélectionner le programme dans une liste**, puis cliquez sur **Bloc\-notes**.  
  
     Recherchez l'élément `<osVersionInfo>` dans le fichier.  Par exemple, la version peut être la suivante :  
  
    ```  
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
    ```  
  
6.  Dans le Concepteur de projets, cliquez sur l'onglet **Événements de build** et cliquez sur le bouton **Modifier après génération**.  
  
7.  Dans la zone **Ligne de commande de l'événement post\-build**, tapez la commande suivante :  
  
     `C:\TEMP\ModifierVersionSECS.exe "$ (TargetPath).manifest" 5.1.2600.0`  
  
     Lorsque vous générez le projet, cette commande change la version minimale du système d'exploitation dans le manifeste de l'application en 5.1.2600.0.  
  
     Dans la mesure où la macro `$(TargetPath)` exprime le chemin d'accès complet pour le fichier exécutable en cours de création, `$(TargetPath)`.manifest spécifie le manifeste de l'application créé dans le répertoire bin.  La publication copie ce manifeste vers l'emplacement de publication que vous définissez précédemment.  
  
8.  Publiez à nouveau le projet.  Allez à la page **Publier** et cliquez sur **Publier maintenant.**  
  
     Consultez à nouveau le manifeste.  Pour consulter le manifeste, accédez au répertoire de publication, cliquez avec le bouton droit sur le fichier et cliquez sur **Ouvrir avec**, puis sur **Sélectionner le programme dans une liste** et sur **Bloc\-notes**.  
  
     La version doit maintenant être :  
  
    ```  
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />  
    ```  
  
## Voir aussi  
 [Événements de build, page du Concepteur de projets \(C\#\)](../ide/reference/build-events-page-project-designer-csharp.md)   
 [Ligne de commande de l’événement pré\-build\/post\-build, boîte de dialogue](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)   
 [Comment : spécifier des événements de build \(Visual Basic\)](../Topic/How%20to:%20Specify%20Build%20Events%20\(Visual%20Basic\).md)   
 [Génération d'applications dans Visual Studio](../ide/compiling-and-building-in-visual-studio.md)