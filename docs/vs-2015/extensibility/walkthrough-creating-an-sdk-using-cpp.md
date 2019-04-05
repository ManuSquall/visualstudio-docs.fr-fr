---
title: 'Procédure pas à pas : Création d’un kit de développement à l’aide de C++ | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 85af1b15fe6f2b87fbe1f7668fd1610c8595b90c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952820"
---
# <a name="walkthrough-creating-an-sdk-using-c"></a>Procédure pas à pas : Création d’un Kit de développement logiciel (SDK) à l’aide de C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette procédure pas à pas montre comment créer une bibliothèque C++ native mathématiques SDK, package le Kit de développement logiciel comme un Visual Studio Extension (VSIX) et ensuite l’utiliser pour créer une application. La procédure pas à pas est divisée en ces étapes :  
  
-   [Pour créer le natif et les bibliothèques Windows Runtime](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
-   [Pour créer le projet d’extension NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
-   [Pour créer un exemple d’application qui utilise la bibliothèque de classes](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>Prérequis  
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createClassLibrary"></a> Pour créer le natif et les bibliothèques Windows Runtime  
  
1.  Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
2.  Dans la liste des modèles, développez **Visual C++**, **Windows Store**, puis sélectionnez le **DLL (applications du Windows Store)** modèle. Dans le **nom** , spécifiez `NativeMath`, puis choisissez le **OK** bouton.  
  
3.  Mettre à jour NativeMath.h pour faire correspondre le code suivant.  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.h#1)]  
  
4.  NativeMath.cpp de mise à jour pour correspondre à ce code :  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.cpp#2)]  
  
5.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour **Solution 'NativeMath'**, puis choisissez **ajouter**, **nouveau projet**.  
  
6.  Dans la liste des modèles, développez **Visual C++**, puis sélectionnez le **composant d’exécution Windows** modèle. Dans le **nom** , spécifiez `NativeMathWRT`, puis choisissez le **OK** bouton.  
  
7.  Class1.h de mise à jour pour correspondre à ce code :  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.h#3)]  
  
8.  Class1.cpp de mise à jour pour correspondre à ce code :  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.cpp#4)]  
  
9. Dans la barre de menus, choisissez **Générer**, puis **Générer la solution**.  
  
##  <a name="createVSIX"></a> Pour créer le projet d’extension NativeMathVSIX  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour **Solution 'NativeMath'**, puis choisissez **ajouter**, **nouveau projet**.  
  
2.  Dans la liste des modèles, développez **Visual C#**, **extensibilité**, puis sélectionnez **Package VSIX**. Dans le **nom** , spécifiez **NativeMathVSIX**, puis choisissez le **OK** bouton.  
  
3.  Lorsque le Concepteur de manifeste VSIX s’affiche, fermez-la.  
  
4.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour **source.extension.vsixmanifest**, puis choisissez **afficher le Code**.  
  
5.  Utilisez le code XML suivant pour remplacer le document XML.  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]
  
6.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **NativeMathVSIX** de projet, puis choisissez **ajouter**, **un nouvel élément**.  
  
7.  Dans la liste des **éléments Visual c#**, développez **données**, puis sélectionnez **fichier XML**. Dans le **nom** , spécifiez `SDKManifest.xml`, puis choisissez le **OK** bouton.  
  
8.  Utilisez le code XML pour remplacer le contenu du fichier :  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathvsix/sdkmanifest.xml#5)]  
  
9. Dans **l’Explorateur de solutions**, dans le **NativeMathVSIX** projet d’équipe, de créer cette structure de dossiers :  
  
    ```  
  
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
  
10. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour **Solution 'NativeMath'**, puis choisissez **ouvrir le dossier dans l’Explorateur de fichiers**.  
  
11. Dans **Explorateur de fichiers**, copiez \NativeMath\NativeMath.h, puis dans **l’Explorateur de solutions**, dans le **NativeMathVSIX** project, collez-le dans le \DesignTime\ Dossier de CommonConfiguration\Neutral\Include\.  
  
     Copiez \Debug\NativeMath\NativeMath.lib et collez-la dans le dossier \DesignTime\Debug\x86\.  
  
     Copiez \Debug\NativeMath\NativeMath.dll et collez-le dans le dossier \Redist\Debug\x86\.  
  
     Copiez DebugNativeMathWRTNativeMathWRT.dll et collez-le dans le dossier RedistDebugx86.  
  
     Copiez DebugNativeMathWRTNativeMathWRT.winmd et collez-le dans le dossier ReferencesCommonConfigurationNeutral.  
  
     Copiez DebugNativeMathWRTNativeMathWRT.pri et collez-le dans le dossier ReferencesCommonConfigurationNeutral.  
  
12. Dans le dossier \DesignTime\Debug\x86\, créez un fichier texte nommé NativeMathSDK.props, puis collez le contenu suivant dans celui-ci :  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
13. Dans la barre de menus, choisissez **vue**, **Windows autres**, **fenêtre Propriétés** (clavier : Appuyez sur F4).  
  
14. Dans **l’Explorateur de solutions**, sélectionnez le **NativeMathWRT.winmd** fichier. Dans le **propriétés** fenêtre, la modification la **Action de génération** propriété **contenu**, puis modifiez le **inclure dans VSIX** propriété  **True**.  
  
     Répétez ce processus pour le **SimpleMath.pri** fichier.  
  
     Répétez ce processus pour le **NativeMath.Lib** fichier.  
  
     Répétez ce processus pour le **NativeMathSDK.props** fichier.  
  
15. Dans **l’Explorateur de solutions**, sélectionnez le **NativeMath.h** fichier. Dans le **propriétés** fenêtre, de modifier le **inclure dans VSIX** propriété **True**.  
  
     Répétez ce processus pour le **NativeMath.dll** fichier.  
  
     Répétez ce processus pour le **NativeMathWRT.dll** fichier.  
  
     Répétez ce processus pour le **SDKManifest.xml** fichier.  
  
16. Dans la barre de menus, choisissez **Générer**, puis **Générer la solution**.  
  
17. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **NativeMathVSIX** de projet, puis choisissez **ouvrir le dossier dans l’Explorateur de fichiers**.  
  
18. Dans **Explorateur de fichiers**, accédez au dossier \bin\Debug\, puis exécutez NativeMathVSIX.vsix pour commencer l’installation.  
  
19. Choisissez le **installer** bouton, attendez que l’installation se termine, puis redémarrez Visual Studio.  
  
##  <a name="createSample"></a> Pour créer un exemple d’application qui utilise la bibliothèque de classes  
  
1. Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
2. Dans la liste des modèles, développez **Visual C++**, **Windows Store**, puis sélectionnez **application vide**. Dans le **nom** , spécifiez **NativeMathSDKSample**, puis choisissez le **OK** bouton.  
  
3. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **NativeMathSDKSample** de projet, puis choisissez **ajouter**, **référence**.  
  
4. Sur le **propriétés communes**, **structure et références** page de propriétés, dans la liste des types référence, développez **Windows**, puis sélectionnez **Extensions** . Dans le volet détails, sélectionnez le **natif mathématiques SDK** extension, puis choisissez le **ajouter une nouvelle référence** bouton.  
  
5. Dans le **ajouter une référence** boîte de dialogue, sélectionnez le **natif mathématiques SDK** case à cocher, puis choisissez le **OK** bouton.  
  
6. Afficher les propriétés du projet pour NativeMathSDKSample.  
  
    Les propriétés que vous avez défini dans NativeMathSDK.props ont été appliquées lorsque vous avez ajouté la référence. Vous pouvez le vérifier en examinant le **répertoires VC ++** propriété du projet **propriétés de Configuration**.  
  
7. Dans **l’Explorateur de solutions**, ouvrez MainPage.xaml, puis utilisez le XAML suivant pour remplacer son contenu :  
  
    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml#1)]  
  
8. Mainpage.xaml.h de mise à jour pour correspondre à ce code :  
  
    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.h#2)]  
  
9. MainPage.xaml.cpp de mise à jour pour correspondre à ce code :  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.cpp#3)]  
  
10. Appuyez sur la touche F5 pour exécuter l’application.  
  
11. Dans l’application, entrez tous les deux nombres, sélectionnez une opération, puis choisissez le **=** bouton.  
  
     Le résultat correct apparaît.  
  
    Cette procédure pas à pas vous a montré comment créer et utiliser un SDK d’Extension pour appeler un [!INCLUDE[wrt](../includes/wrt-md.md)] bibliothèque et non -[!INCLUDE[wrt](../includes/wrt-md.md)] bibliothèque.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Création d’un à l’aide du Kit de développement logiciel C# ou Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Création d’un Kit de développement logiciel (SDK)](../extensibility/creating-a-software-development-kit.md)
