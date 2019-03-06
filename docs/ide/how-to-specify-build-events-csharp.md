---
title: 'Procédure : Spécifier des événements de build (C#)'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- pre-build events
- events [Visual Studio], builds
- post-build events
- build events [Visual Studio]
- builds [Visual Studio], events
ms.assetid: b4ce1ad9-5215-4b6f-b6a2-798b249aa335
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: af2329789e5eea4c9b0875f2986181f6d672757c
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55930456"
---
# <a name="how-to-specify-build-events-c"></a>Procédure : Spécifier des événements de build (C#)

Utilisez des événements de build pour spécifier des commandes à exécuter avant que la génération commence ou après qu’elle se termine. Les événements de build sont exécutés uniquement si la build atteint ces étapes du processus de génération.

Quand un projet est généré, les événements prébuild sont ajoutés à un fichier nommé *PreBuildEvent.bat*, et les événements postbuild sont ajoutés à un fichier nommé *PostBuildEvent.bat*. Pour garantir la vérification des erreurs, ajoutez vos propres commandes de vérification d’erreurs aux étapes de génération.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="how-to-specify-pre-build-and-post-build-events"></a>Comment spécifier des événements prébuild et des événements postbuild

### <a name="to-specify-a-build-event"></a>Pour spécifier un événement de build

1.  Dans l’**Explorateur de solutions**, sélectionnez le projet pour lequel vous voulez spécifier l’événement de build.

2.  Dans le menu **Projet**, cliquez sur **Propriétés**.

3.  Sélectionnez l’onglet **Événements de build**.

4.  Dans la zone **Ligne de commande de l’événement pré-build**, spécifiez la syntaxe de l’événement de build.

    > [!NOTE]
    > Les événements pré-build ne fonctionnent pas si le projet est à jour et qu’aucune build n’est déclenchée.

5.  Dans la zone **Ligne de commande de l’événement post-build**, spécifiez la syntaxe de l’événement de build.

    > [!NOTE]
    > Ajoutez une instruction `call` avant toutes les commandes postbuild qui exécutent des fichiers *.bat*. Par exemple, `call C:\MyFile.bat` ou `call C:\MyFile.bat call C:\MyFile2.bat`.

6.  Dans la zone **Exécuter l’événement post-build**, spécifiez sous quelles conditions exécuter l’événement post-build.

    > [!NOTE]
    > Pour ajouter une syntaxe longue, ou pour sélectionner des macros de génération à partir de la [boîte de dialogue Ligne de commande de l’événement prébuild/postbuild](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md), cliquez sur le bouton de sélection (**...**) afin d’afficher une zone d’édition.

     La syntaxe de l’événement de build peut inclure toute commande valide à une invite de commandes ou dans un fichier *.bat*. Le nom d’un fichier de commandes doit être précédé par `call` pour vous assurer que toutes les commandes suivantes sont exécutées.

    > [!NOTE]
    > Si votre événement pré-build ou post-build ne s’exécute pas correctement, vous pouvez terminer la génération en faisant en sorte que l’action d’événement s’achève avec un code autre que zéro (0), qui indique une action réussie.

## <a name="example-how-to-change-manifest-information-by-using-a-post-build-event"></a>Exemple : comment changer des informations de manifeste à l’aide d’un événement postbuild

La procédure suivante montre comment définir la version minimale du système d’exploitation dans le manifeste de l’application à l’aide d’une commande *.exe* appelée à partir d’un événement postbuild (fichier *.exe.manifest* dans le répertoire du projet). La version minimale du système d’exploitation est un nombre en quatre parties, tel que 4.10.0.0. Pour ce faire, la commande modifie la section `<dependentOS>` du manifeste :

```xml
<dependentOS>
   <osVersionInfo>
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   </osVersionInfo>
</dependentOS>
```

### <a name="to-create-an-exe-command-to-change-the-application-manifest"></a>Pour créer une commande .exe afin de modifier le manifeste d’application

1. Créez une application console pour la commande. Dans le menu **Fichier**, pointez sur **Nouveau**, puis cliquez sur **Projet**.

2. Dans la boîte de dialogue **Nouveau projet**, développez **Visual C#**, cliquez sur **Windows**, puis cliquez sur le modèle **Application console**. Attribuez un nom au projet `ChangeOSVersionCS`.

3. Dans *Program.cs*, ajoutez la ligne suivante aux autres instructions `using` au début du fichier :

   ```csharp
   using System.Xml;
   ```

4. Dans l’espace de noms `ChangeOSVersionCS`, remplacez l’implémentation de la classe `Program` par le code suivant :

   ```csharp
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

    La commande accepte deux arguments : le chemin du manifeste de l’application (autrement dit, le dossier dans lequel le processus de génération crée le manifeste, en général *Projectname.publish*), et la nouvelle version du système d’exploitation.

5. Générez le projet. Dans le menu **Générer** , cliquez sur **Générer la solution**.

6. Copiez le fichier *.exe* dans un répertoire tel que *C:\TEMP\ChangeOSVersionVB.exe*.

   Ensuite, appelez cette commande dans un événement post-build pour modifier le manifeste d’application.

### <a name="to-invoke-a-post-build-event-to-modify-the-application-manifest"></a>Pour appeler un événement post-build afin de modifier le manifeste d’application

1.  Créez une application Windows pour le projet à publier. Dans le menu **Fichier**, pointez sur **Nouveau**, puis cliquez sur **Projet**.

2.  Dans la boîte de dialogue **Nouveau projet**, développez **Visual C#**, cliquez sur **Bureau Windows**, puis cliquez sur le modèle **Application Windows Forms**. Attribuez un nom au projet `CSWinApp`.

3.  Après avoir sélectionné le projet dans l’**Explorateur de solutions**, dans le menu **Projet**, cliquez sur **Propriétés**.

4.  Dans le **Concepteur de projet**, localisez la page **Publier** et affectez à **Emplacement de publication** la valeur *C:\TEMP*.

5.  Publiez le projet en cliquant sur **Publier maintenant**.

     Le fichier manifeste est généré et placé dans *C:\TEMP\CSWinApp_1_0_0_0\CSWinApp.exe.manifest*. Pour consulter le manifeste, cliquez avec le bouton droit sur le fichier, cliquez sur **Ouvrir avec**, sélectionnez **Sélectionner le programme dans une liste**, puis cliquez sur **Bloc-notes**.

     Recherchez l’élément `<osVersionInfo>` dans le fichier. Par exemple, la version peut être :

    ```xml
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
    ```

6.  Dans le **Concepteur de projet**, cliquez sur l’onglet **Événements de build**, puis sur le bouton **Modifier post-build**.

7.  Dans la zone **Ligne de commande de l’événement post-build**, tapez la commande suivante :

     `C:\TEMP\ChangeOSVersionCS.exe "$(TargetPath).manifest" 5.1.2600.0`

     Quand vous générez le projet, cette commande change la version minimale du système d’exploitation dans le manifeste d’application en 5.1.2600.0.

     Dans la mesure où la macro `$(TargetPath)` exprime le chemin complet du fichier exécutable en cours de création, `$(TargetPath)`*.manifest* spécifie le manifeste de l’application créé dans le répertoire *bin*. La publication copie ce manifeste vers l’emplacement de publication que vous avez défini.

8.  Republiez le projet. Accédez à la page **Publier** et cliquez sur **Publier maintenant**.

     Réaffichez le manifeste. Pour consulter le manifeste, ouvrez le répertoire de publication, cliquez avec le bouton droit sur le fichier, cliquez sur **Ouvrir avec**, sélectionnez **Sélectionner le programme dans une liste**, puis cliquez sur **Bloc-notes**.

     La version doit maintenant se présenter comme suit :

    ```xml
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />
    ```

## <a name="see-also"></a>Voir aussi

- [Événements de build, page du Concepteur de projets (C#)](../ide/reference/build-events-page-project-designer-csharp.md)
- [Ligne de commande de l’événement prébuild/postbuild, boîte de dialogue](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [Guide pratique pour spécifier des événements de build (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md)
- [Compiler et générer](../ide/compiling-and-building-in-visual-studio.md)