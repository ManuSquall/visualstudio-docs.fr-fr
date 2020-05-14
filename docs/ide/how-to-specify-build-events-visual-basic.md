---
title: Guide pratique pour spécifier des événements de build (Visual Basic)
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- pre-build events
- events [Visual Studio], builds
- post-build events
- build events [Visual Studio]
- builds [Visual Studio], events
ms.assetid: 40dc83bf-a7c5-4a14-816a-fa0980b6e4c3
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33cf9cadc8fbf091fb213926fb25b232d14dc0d7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115105"
---
# <a name="how-to-specify-build-events-visual-basic"></a>Guide pratique pour spécifier des événements de build (Visual Basic)

Vous pouvez utiliser des événements de build en Visual Basic pour exécuter des scripts, des macros ou d’autres actions dans le cadre du processus de compilation. Les événements pré-build se produisent avant la compilation, tandis que les événements post-build se produisent après la compilation.

Les événements de build sont spécifiés dans la boîte de dialogue **Événements de build**, disponible à partir de la page **Compiler** du **Concepteur de projets**.

> [!NOTE]
> Visual Basic Express ne prend pas en charge l’entrée d’événements de build. Celle-ci n’est prise en charge que dans le produit Visual Studio complet.

## <a name="how-to-specify-pre-build-and-post-build-events"></a>Comment spécifier des événements prébuild et des événements postbuild

### <a name="to-specify-a-build-event"></a>Pour spécifier un événement de build

1. Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.

2. Cliquez sur l’onglet **Compiler**.

3. Cliquez sur le bouton **Événements de build** pour ouvrir la boîte de dialogue **Événements de build**.

4. Entrez les arguments de ligne de commande pour votre action pré-build ou post-build, puis cliquez sur **OK**.

    > [!NOTE]
    > Ajoutez `call` une déclaration avant toutes les commandes post-build qui exécutent des fichiers *.bat.* Par exemple, `call C:\MyFile.bat` ou `call C:\MyFile.bat call C:\MyFile2.bat`.

    > [!NOTE]
    > Si votre événement pré-build ou post-build ne s’exécute pas correctement, vous pouvez terminer la génération en faisant en sorte que l’action d’événement s’achève avec un code autre que zéro (0), qui indique une action réussie.

## <a name="example-how-to-change-manifest-information-using-a-post-build-event"></a>Exemple : comment changer des informations de manifeste à l’aide d’un événement postbuild

La procédure suivante montre comment définir la version minimale du système d’exploitation dans le manifeste de l’application à l’aide d’une commande *.exe* appelée à partir d’un événement post-construction (le fichier *.exe.manifest* dans l’annuaire du projet). La version minimale du système d’exploitation est un nombre en quatre parties, tel que 4.10.0.0. Pour ce faire, la commande modifie la section `<dependentOS>` du manifeste :

```xml
<dependentOS>
   <osVersionInfo>
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   </osVersionInfo>
</dependentOS>
```

### <a name="to-create-an-exe-command-to-change-the-application-manifest"></a>Pour créer une commande .exe afin de modifier le manifeste d’application

1. Créez une application console pour la commande. Dans le menu **Fichier**, cliquez sur **Nouveau**, puis sur **Projet**.

2. Dans la boîte de dialogue **Nouveau projet**, dans le nœud **Visual Basic**, sélectionnez **Windows**, puis le modèle **Application console**. Nommez le projet `ChangeOSVersionVB`.

3. Dans *Module1.vb*, ajoutez la `Imports` ligne suivante aux autres instructions en haut du fichier :

   ```vb
   Imports System.Xml
   ```

4. Ajoutez le code suivant dans `Sub Main` :

   ```vb
   Sub Main()
      Dim applicationManifestPath As String
      applicationManifestPath = My.Application.CommandLineArgs(0)
      Console.WriteLine("Application Manifest Path: " & applicationManifestPath.ToString)

      'Get version name
      Dim osVersion As Version
      If My.Application.CommandLineArgs.Count >= 2 Then
         osVersion = New Version(My.Application.CommandLineArgs(1).ToString)
      Else
         Throw New ArgumentException("OS Version not specified.")
      End If
      Console.WriteLine("Desired OS Version: " & osVersion.ToString())

      Dim document As XmlDocument
      Dim namespaceManager As XmlNamespaceManager
      namespaceManager = New XmlNamespaceManager(New NameTable())
      With namespaceManager
         .AddNamespace("asmv1", "urn:schemas-microsoft-com:asm.v1")
         .AddNamespace("asmv2", "urn:schemas-microsoft-com:asm.v2")
      End With

      document = New XmlDocument()
      document.Load(applicationManifestPath)

      Dim baseXPath As String
      baseXPath = "/asmv1:assembly/asmv2:dependency/asmv2:dependentOS/asmv2:osVersionInfo/asmv2:os"

      'Change minimum required OS Version.
      Dim node As XmlNode
      node = document.SelectSingleNode(baseXPath, namespaceManager)
      node.Attributes("majorVersion").Value = osVersion.Major.ToString()
      node.Attributes("minorVersion").Value = osVersion.Minor.ToString()
      node.Attributes("buildNumber").Value = osVersion.Build.ToString()
      node.Attributes("servicePackMajor").Value = osVersion.Revision.ToString()

      document.Save(applicationManifestPath)
   End Sub
   ```

   La commande prend deux arguments. Le premier argument est le chemin vers le manifeste de l’application (c’est-à-dire le dossier dans lequel le processus de construction crée le manifeste, typiquement * \<ProjectName>.publish*). Le second argument est la nouvelle version du système d’exploitation.

5. Dans le menu **Générer**, cliquez sur **Générer la solution**.

6. Copiez le fichier *.exe* dans un répertoire tel que *C:\TEMP\ChangeOSVersionVB.exe*.

   Ensuite, appelez cette commande dans un événement post-build pour modifier le manifeste d’application.

### <a name="to-invoke-a-post-build-event-to-change-the-application-manifest"></a>Pour appeler un événement post-build afin de modifier le manifeste d’application

1. Créez une application Windows pour le projet à publier. Dans le menu **Fichier**, cliquez sur **Nouveau**, puis sur **Projet**.

2. Dans la boîte de dialogue **Nouveau projet**, dans le nœud **Visual Basic**, sélectionnez **Bureau Windows**, puis le modèle **Application Windows Forms**. Nommez le projet `VBWinApp`.
3. Après avoir sélectionné le projet dans l’**Explorateur de solutions**, dans le menu **Projet**, cliquez sur **Propriétés**.

4. Dans le **Concepteur de projet**, accédez à la page **Publier** et affectez à **Emplacement de publication** la valeur *C:\TEMP*.

5. Publiez le projet en cliquant sur **Publier maintenant**.

     Le fichier manifeste est généré et placé dans *C:\TEMP\VBWinApp_1_0_0_0\VBWinApp.exe.manifest*. Pour consulter le manifeste, cliquez avec le bouton droit sur le fichier, puis cliquez successivement sur **Ouvrir avec**, **Sélectionner le programme dans une liste** et **Bloc-notes**.

     Recherchez l’élément `<osVersionInfo>` dans le fichier. Par exemple, la version peut être :

    ```xml
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
    ```

6. Dans le **Concepteur de projet**, accédez à l’onglet **Compiler**, puis cliquez sur le bouton **Événements de build** pour ouvrir la boîte de dialogue **Événements de build**.

7. Dans la zone **Ligne de commande de l’événement post-build**, entrez la commande suivante :

     `C:\TEMP\ChangeOSVersionVB.exe "$(TargetPath).manifest" 5.1.2600.0`

     Quand vous générez le projet, cette commande change la version minimale du système d’exploitation dans le manifeste d’application en 5.1.2600.0.

     La macro `$(TargetPath)` exprime le chemin complet de l’exécutable en cours de création. Ainsi, *$(TargetPath).manifest* spécifie le manifeste de l’application créé dans le répertoire *bin*. La publication copie ce manifeste vers l’emplacement de publication que vous avez défini.

8. Republiez le projet. Accédez à la page **Publier** et cliquez sur **Publier maintenant**.

     Réaffichez le manifeste. Pour consulter le manifeste, accédez au répertoire de publication, cliquez avec le bouton droit sur le fichier, puis cliquez successivement sur **Ouvrir avec**, **Sélectionner le programme dans une liste** et **Bloc-notes**.

     La version doit maintenant se présenter comme suit :

    ```xml
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />
    ```

## <a name="see-also"></a>Voir aussi

- [Page Compile, Concepteur de projet (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)
- [Page Publier, Concepteur de projet](../ide/reference/publish-page-project-designer.md)
- [Ligne de commande de l’événement prébuild/postbuild, boîte de dialogue](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [Guide pratique pour spécifier des événements de build (C#)](../ide/how-to-specify-build-events-csharp.md)
