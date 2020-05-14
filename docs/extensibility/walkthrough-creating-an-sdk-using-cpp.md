---
title: 'Procédure pas à pas : Création d’un SDK à l’aide de C Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65643e65490eacb79eea4d76aa49ff10d6cccf66
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697635"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>Procédure pas à pas : Créez un SDK à l’aide de C
Ce pas-là montre comment créer une bibliothèque de mathématiques native SDK, emballer le SDK comme une extension de studio visuel (VSIX), puis l’utiliser pour créer une application. La procédure pas à pas est divisée en ces étapes :

- [Créer les bibliothèques natives et Windows Runtime](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)

- [Créer le projet d’extension NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)

- [Pour créer une application d’échantillon qui utilise la bibliothèque de classe](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)

## <a name="prerequisites"></a>Prérequis
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, voir [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a>Créer les bibliothèques natives et Windows Runtime

1. Sur la barre de menu, choisissez **File** > **New** > **Project**.

2. Dans la liste des modèles, élargissez **Visual CMD** > **Windows Universal,** puis sélectionnez le modèle **DLL (Windows Universal apps).** Dans la boîte `NativeMath` **nom,** spécifiez, puis choisissez le bouton **OK.**

3. Mise à jour *NativeMath.h* pour correspondre au code suivant.

     [!code-cpp[CreatingAnSDKUsingCpp#1](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]

4. Mise à jour *NativeMath.cpp* pour correspondre à ce code:

     [!code-cpp[CreatingAnSDKUsingCpp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]

5. Dans **Solution Explorer**, ouvrez le menu raccourci pour Solution **'NativeMath'**, puis choisissez **Add** > New**Project**.

6. Dans la liste des modèles, élargissez **Visual CMMD,** puis sélectionnez le modèle **de composant Windows Runtime.** Dans la boîte `NativeMathWRT` **nom,** spécifiez, puis choisissez le bouton **OK.**

7. Mise à jour *Class1.h* pour correspondre à ce code:

     [!code-cpp[CreatingAnSDKUsingCpp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]

8. Mise à jour *Class1.cpp* pour correspondre à ce code:

     [!code-cpp[CreatingAnSDKUsingCpp#4](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]

9. Sur la barre de menu, choisissez **Build** > **Build Solution**.

## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a>Créer le projet d’extension NativeMathVSIX

1. Dans **Solution Explorer**, ouvrez le menu raccourci pour Solution **'NativeMath'**, puis choisissez **Add** > New**Project**.

2. Dans la liste des modèles, élargissez Visual C > **'Extensibility**, puis sélectionnez **VSIX Project**. **Visual C#** Dans la boîte **nomin,** spécifiez **NativeMathVSIX**, puis choisissez le bouton **OK.**

3. Dans **Solution Explorer**, ouvrez le menu raccourci pour **source.extension.vsixmanifest**, puis choisissez View **Code**.

4. Utilisez le XML suivant pour remplacer le XML existant.

    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

5. Dans **Solution Explorer**, ouvrez le menu raccourci pour le projet **NativeMathVSIX,** puis choisissez **Ajouter** > **un nouvel article**.

6. Dans la liste des **éléments visuels C,** élargir les **données,** puis sélectionner **le fichier XML**. Dans la boîte `SDKManifest.xml` **nom,** spécifiez, puis choisissez le bouton **OK.**

7. Utilisez ce XML pour remplacer le contenu du fichier :

     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]

8. Dans **Solution Explorer**, dans le cadre du projet **NativeMathVSIX,** créez cette structure de dossier :

    ```xml
    \DesignTime
          \CommonConfiguration
                \Neutral
                      \Include
          \Debug
                \x86
    \Redist
          \Debug
                \x86
    \References
          \CommonConfiguration
                \Neutral
    ```

9. Dans **Solution Explorer**, ouvrez le menu raccourci pour Solution **'NativeMath'**, puis choisissez Open **Folder in File Explorer**.

10. Dans **File Explorer**, *copiez $SolutionRoot$-NativeMath-NativeMath.h*, puis dans **Solution Explorer**, dans le cadre du projet **NativeMathVSIX,** collez-le dans le *dossier\\ $SolutionRoot$-NativeMathVSIX-DesignTime-CommonConfiguration-Neutral-Inclu.*

     Copiez *$SolutionRoot$-Debug-NativeMath-NativeMath.lib*, puis collez-le dans le dossier *\\ $SolutionRoot$-NativeMathVSIX-DesignTime-Debug-x86.*

     Copiez *$SolutionRoot$-Debug-NativeMath-NativeMath.dll* et collez-le dans le dossier *\\ $SolutionRoot$-NativeMathVSIX-Redist-Debug-x86.*

     *Copiez-$SolutionRoot$-Debug-NativeMathWRT-NativeMathWRT.dll* et collez-le dans le dossier *$SolutionRoot$-NativeMathVSIX-Redist-Debug-x86.*
     Copiez *$SolutionRoot$-Debug-NativeMathWRT-NativeMathWRT.winmd* et collez-le dans le *dossier $SolutionRoot$'NativeMathVSIX-References-CommonConfiguration-Neutral.*

     Copiez *$SolutionRoot$-Debug-NativeMathWRT-NativeMathWRT.pri* et collez-le dans le *dossier $SolutionRoot$'NativeMathVSIX-References-CommonConfiguration-Neutral.*

11. Dans le dossier *$SolutionRoot$-NativeMathVSIX-DesignTime-Debug-x86,\\ * créez un fichier texte qui s’appelle *NativeMathSDK.props,* puis collez le contenu suivant en elle :

    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]

12. Sur la barre de menu, choisissez **View** > **Other Windows** > **Properties Window** (Clavier: Choisissez la clé **F4).**

13. Dans **Solution Explorer**, sélectionnez le fichier **NativeMathWRT.winmd.** Dans la fenêtre **propriété,** changer la propriété **Build Action** en **Contenu**, puis changer **l’inclure dans la** propriété VSIX à **True**.

     Répétez ce processus pour le fichier **NativeMath.h.**

     Répétez ce processus pour le fichier **NativeMathWRT.pri.**

     Répétez ce processus pour le fichier **NativeMath.Lib.**

     Répétez ce processus pour le fichier **NativeMathSDK.props.**

14. Dans **Solution Explorer**, sélectionnez le fichier **NativeMath.h.** Dans la fenêtre **propriété,** changer **l’inclure dans la** propriété VSIX à **True**.

     Répétez ce processus pour le fichier **NativeMath.dll.**

     Répétez ce processus pour le fichier **NativeMathWRT.dll.**

     Répétez ce processus pour le fichier **SDKManifest.xml.**

15. Sur la barre de menu, choisissez **Build** > **Build Solution**.

16. Dans **Solution Explorer**, ouvrez le menu raccourci pour le projet **NativeMathVSIX,** puis choisissez **Open Folder dans File Explorer**.

17. Dans **File Explorer**, naviguez vers le dossier *$SolutionRoot$-NativeMathVSIX-bin-Debug,* puis exécutez *NativeMathVSIX.vsix* pour commencer l’installation.

18. Choisissez le bouton **Installer,** attendez la fin de l’installation, puis ouvrez Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a>Pour créer une application d’échantillon qui utilise la bibliothèque de classe

1. Sur la barre de menu, choisissez **File** > **New** > **Project**.

2. Dans la liste des modèles, élargissez **Visual CMD** > **Windows Universal,** puis sélectionnez **Blank App**. Dans la boîte **nomin,** spécifiez **NativeMathSDKSample,** puis choisissez le bouton **OK.**

3. Dans **Solution Explorer**, ouvrez le menu raccourci pour le projet **NativeMathSDKSample,** puis choisissez **Add** > **Reference**.

4. Dans la boîte de dialogue **Add Reference,** dans la liste des types de référence, étendre **Windows universel**, puis sélectionner **des extensions**. Enfin, Sélectionnez la case à cocher **Native Math SDK,** puis choisissez le bouton **OK.**

5. Affichez les propriétés du projet pour NativeMathSDKSample.

    Les propriétés que vous avez définies dans *NativeMathSDK.props* ont été appliquées lorsque vous avez ajouté la référence. Vous pouvez vérifier que les propriétés ont été appliquées en examinant la propriété **des annuaires VCMD** des **propriétés configuration**du projet.

6. Dans **Solution Explorer**, ouvrez **MainPage.xaml**, puis utilisez le XAML suivant pour remplacer son contenu :

    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]

7. Mise à jour *Mainpage.xaml.h* pour correspondre à ce code:

    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]

8. Mise à jour *MainPage.xaml.cpp* pour correspondre à ce code:

     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]

9. Choisissez la clé **F5** pour exécuter l’application.

10. Dans l’application, entrez deux numéros, sélectionnez une opération, puis choisissez le **=** bouton.

     Le résultat correct apparaît.

    Cette procédure pas à pas a montré comment créer et [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] utiliser un SDK Extension pour appeler dans une bibliothèque et une bibliothèque non-bibliothèque.[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)]

## <a name="next-steps"></a>Étapes suivantes

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : Créez un SDK à l’aide de CMD ou de Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Créer un kit de développement logiciel](../extensibility/creating-a-software-development-kit.md)
