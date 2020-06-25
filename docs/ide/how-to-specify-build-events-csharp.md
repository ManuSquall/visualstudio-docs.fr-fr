---
title: Guide pratique pour spécifier des événements de build (C#)
ms.date: 03/21/2019
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- pre-build events
- events [Visual Studio], builds
- post-build events
- build events [Visual Studio]
- builds [Visual Studio], events
ms.assetid: b4ce1ad9-5215-4b6f-b6a2-798b249aa335
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e1a3083b59ad0cec727f753395768a214ff571b7
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283994"
---
# <a name="how-to-specify-build-events-c"></a>Guide pratique pour spécifier des événements de build (C#)

Utilisez des événements de build pour spécifier des commandes à exécuter avant que la génération commence ou après qu’elle se termine. Les événements de build ne s’exécutent que si la build atteint ces étapes du processus de génération.

Quand un projet est généré, les événements pré-build sont ajoutés à un fichier nommé *PreBuildEvent.bat*, et les événements post-build sont ajoutés à un fichier nommé *PostBuildEvent.bat*. Pour garantir la vérification des erreurs, ajoutez vos propres commandes de vérification d’erreurs aux étapes de génération.

## <a name="specify-a-build-event"></a>Spécifier un événement de build

1. Dans l’**Explorateur de solutions**, sélectionnez le projet pour lequel vous voulez spécifier l’événement de build.

2. Dans le menu **Projet** , cliquez sur **Propriétés**.

3. Sélectionnez l’onglet **Événements de build**.

4. Dans la zone **Ligne de commande de l’événement pré-build**, spécifiez la syntaxe de l’événement de build.

   > [!NOTE]
   > Les événements pré-build ne fonctionnent pas si le projet est à jour et qu’aucune build n’est déclenchée.

5. Dans la zone **Ligne de commande de l’événement post-build**, spécifiez la syntaxe de l’événement de build.

   > [!NOTE]
   > Ajoutez une `call` instruction avant toutes les commandes postérieures à la génération qui exécutent des fichiers *. bat* . Par exemple, `call C:\MyFile.bat` ou `call C:\MyFile.bat call C:\MyFile2.bat`.

6. Dans la zone **Exécuter l’événement post-build**, spécifiez sous quelles conditions exécuter l’événement post-build.

   > [!NOTE]
   > Pour ajouter une syntaxe longue, ou pour sélectionner des macros de génération à partir de la [boîte de dialogue Ligne de commande de l’événement prébuild/postbuild](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md), cliquez sur le bouton de sélection (**...**) afin d’afficher une zone d’édition.

   La syntaxe de l’événement de build peut inclure toute commande valide à une invite de commandes ou dans un fichier *.bat*. Le nom d’un fichier de commandes doit être précédé par `call` pour vous assurer que toutes les commandes suivantes sont exécutées.

   > [!NOTE]
   > Si votre événement pré-build ou post-build ne s’exécute pas correctement, vous pouvez terminer la génération en faisant en sorte que l’action d’événement s’achève avec un code autre que zéro (0), qui indique une action réussie.

## <a name="example"></a>Exemple

La procédure suivante montre comment définir la version minimale du système d’exploitation dans le manifeste de l’application à l’aide d’une commande *.exe* appelée à partir d’un événement postbuild (fichier *.exe.manifest* dans le répertoire du projet). La version minimale du système d’exploitation est un nombre en quatre parties, tel que 4.10.0.0. Pour définir la version minimale du système d’exploitation, la commande modifie la section `<dependentOS>` du manifeste :

```xml
<dependentOS>
   <osVersionInfo>
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   </osVersionInfo>
</dependentOS>
```

### <a name="create-an-exe-command-to-change-the-application-manifest"></a>Créer une commande .exe pour changer le manifeste d’application

1. Créez un projet **Application console** pour la commande. Nommez le projet **ChangeOSVersionCS**.

2. Dans *Program.cs*, ajoutez la ligne suivante aux autres `using` directives en haut du fichier :

   ```csharp
   using System.Xml;
   ```

3. Dans l’espace de noms `ChangeOSVersionCS`, remplacez l’implémentation de la classe `Program` par le code suivant :

   ```csharp
   class Program
   {
      /// <summary>
      /// This function sets the minimum operating system version for a ClickOnce application.
      /// </summary>
      /// <param name="args">
      /// Command Line Arguments:
      /// 0 - Path to application manifest (.exe.manifest)
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

4. Créez le projet.

5. Copiez le fichier *.exe* dans un répertoire tel que *C:\TEMP\ChangeOSVersionVB.exe*.

Ensuite, appelez cette commande dans un événement post-build pour modifier le manifeste d’application.

### <a name="invoke-a-post-build-event-to-modify-the-application-manifest"></a>Appeler un événement post-build pour modifier le manifeste d’application

1. Créez un projet **Application Windows Forms** et nommez-le **CSWinApp**.

2. Après avoir sélectionné le projet dans l’**Explorateur de solutions**, dans le menu **Projet**, choisissez **Propriétés**.

3. Dans le **Concepteur de projet**, localisez la page **Publier** et affectez à **Emplacement de publication** la valeur *C:\TEMP*.

4. Publiez le projet en cliquant sur **Publier maintenant**.

   Le fichier manifeste est généré et enregistré dans *C:\TEMP\CSWinApp_1_0_0_0\CSWinApp.exe.manifest*. Pour consulter le manifeste, cliquez avec le bouton droit sur le fichier, cliquez sur **Ouvrir avec**, sélectionnez **Sélectionner le programme dans une liste**, puis cliquez sur **Bloc-notes**.

   Recherchez l’élément `<osVersionInfo>` dans le fichier. Par exemple, la version peut être :

   ```xml
   <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   ```

5. De retour dans le **Concepteur de projet**, cliquez sur l’onglet **Événements de build**, puis sur **Modifier post-build**.

6. Dans la zone **Ligne de commande de l’événement post-build**, entrez la commande suivante :

   `C:\TEMP\ChangeOSVersionCS.exe "$(TargetPath).manifest" 5.1.2600.0`

   Quand vous générez le projet, cette commande change la version minimale du système d’exploitation dans le manifeste d’application en 5.1.2600.0.

   Dans la mesure où la macro `$(TargetPath)` exprime le chemin complet du fichier exécutable à créer, `$(TargetPath).manifest` spécifie le manifeste de l’application créé dans le répertoire *bin*. La publication copie ce manifeste à l’emplacement de publication que vous avez défini.

7. Republiez le projet.

   La version du manifeste doit maintenant se présenter comme suit :

   ```xml
   <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />
   ```

## <a name="see-also"></a>Voir aussi

- [Événements de build, page du concepteur de projets (C#)](../ide/reference/build-events-page-project-designer-csharp.md)
- [Ligne de commande de l’événement pré-build/après génération (boîte de dialogue)](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [Guide pratique pour spécifier des événements de build (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md)
- [Compilation et génération](../ide/compiling-and-building-in-visual-studio.md)
