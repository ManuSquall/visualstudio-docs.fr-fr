---
title: 'Procédure pas à pas : création d’un SDK à l’aide de C++ | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1312d61b2d287a5dd8cb757b73e818a9e9cb2241
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202070"
---
# <a name="walkthrough-creating-an-sdk-using-c"></a>Procédure pas à pas : création d’un SDK en C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette procédure pas à pas montre comment créer un kit de développement logiciel (SDK) de bibliothèque mathématique C++ natif, empaqueter le kit de développement logiciel (SDK) en tant qu’extension Visual Studio (VSIX), puis l’utiliser pour créer une application. La procédure pas à pas est divisée en étapes :  
  
- [Pour créer les bibliothèques natives et Windows Runtime](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
- [Pour créer le projet d’extension NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
- [Pour créer un exemple d’application qui utilise la bibliothèque de classes](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>Prérequis  
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [Kit de développement logiciel (SDK) Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a> Pour créer les bibliothèques natives et Windows Runtime  
  
1. Dans le menu principal, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
2. Dans la liste des modèles, développez **Visual C++**, **Windows Store**, puis sélectionnez le modèle **dll (applications du Windows Store)** . Dans la zone **nom** , spécifiez `NativeMath` , puis choisissez le bouton **OK** .  
  
3. Mettez à jour NativeMath. h pour qu’il corresponde au code suivant.  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.h#1)]  
  
4. Mettez à jour NativeMath. cpp pour qu’il corresponde à ce code :  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.cpp#2)]  
  
5. Dans **Explorateur de solutions**, ouvrez le menu contextuel de la **solution’NativeMath'**, puis choisissez **Ajouter**, **nouveau projet**.  
  
6. Dans la liste des modèles, développez **Visual C++**, puis sélectionnez le modèle de **composant Windows Runtime** . Dans la zone **nom** , spécifiez `NativeMathWRT` , puis choisissez le bouton **OK** .  
  
7. Mettez à jour Class1. h pour qu’il corresponde à ce code :  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.h#3)]  
  
8. Mettez à jour Class1. cpp pour qu’il corresponde à ce code :  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.cpp#4)]  
  
9. Dans la barre de menus, choisissez **Générer**, puis **Générer la solution**.  
  
## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a> Pour créer le projet d’extension NativeMathVSIX  
  
1. Dans **Explorateur de solutions**, ouvrez le menu contextuel de la **solution’NativeMath'**, puis choisissez **Ajouter**, **nouveau projet**.  
  
2. Dans la liste des modèles, développez **Visual C#**, **extensibilité**, puis sélectionnez **package VSIX**. Dans la zone **nom** , spécifiez **NativeMathVSIX**, puis choisissez le bouton **OK** .  
  
3. Lorsque le concepteur de manifeste VSIX apparaît, fermez-le.  
  
4. Dans **Explorateur de solutions**, ouvrez le menu contextuel de **source. extension. vsixmanifest**, puis choisissez **afficher le code**.  
  
5. Utilisez le code XML suivant pour remplacer le XML existant.  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]
  
6. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet **NativeMathVSIX** , puis choisissez **Ajouter**, **nouvel élément**.  
  
7. Dans la liste des **éléments Visual C#**, développez **données**, puis sélectionnez **fichier XML**. Dans la zone **nom** , spécifiez `SDKManifest.xml` , puis choisissez le bouton **OK** .  
  
8. Utilisez ce code XML pour remplacer le contenu du fichier :  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathvsix/sdkmanifest.xml#5)]  
  
9. Dans **Explorateur de solutions**, dans le projet **NativeMathVSIX** , créez la structure de dossiers suivante :  
  
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
  
10. Dans **Explorateur de solutions**, ouvrez le menu contextuel de la **solution’NativeMath'**, puis choisissez **ouvrir le dossier dans l’Explorateur de fichiers**.  
  
11. Dans l' **Explorateur de fichiers**, copiez \NativeMath\NativeMath.h, puis dans **Explorateur de solutions**, dans le projet **NativeMathVSIX** , collez-le dans le dossier \DesignTime\CommonConfiguration\Neutral\Include\  
  
     Copiez \Debug\NativeMath\NativeMath.lib, puis collez-le dans le dossier \DesignTime\Debug\x86\.  
  
     Copiez \Debug\NativeMath\NativeMath.dll et collez-la dans le dossier \Redist\Debug\x86\.  
  
     Copiez DebugNativeMathWRTNativeMathWRT.dll et collez-la dans le dossier RedistDebugx86.  
  
     Copiez DebugNativeMathWRTNativeMathWRT. winmd et collez-le dans le dossier ReferencesCommonConfigurationNeutral  
  
     Copiez DebugNativeMathWRTNativeMathWRT. PRI et collez-le dans le dossier ReferencesCommonConfigurationNeutral.  
  
12. Dans le dossier \DesignTime\Debug\x86\, créez un fichier texte nommé NativeMathSDK. props, puis collez-y le contenu suivant :  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
13. Dans la barre de menus, choisissez **affichage**, **autres fenêtres**, **fenêtre Propriétés** (clavier : Appuyez sur la touche F4).  
  
14. Dans **Explorateur de solutions**, sélectionnez le fichier **NativeMathWRT. winmd** . Dans la fenêtre **Propriétés** , affectez à la propriété **action de génération** la valeur **contenu**, puis remplacez la propriété **inclure dans VSIX** par **true**.  
  
     Répétez ce processus pour le fichier **SimpleMath. pri** .  
  
     Répétez ce processus pour le fichier **NativeMath. lib** .  
  
     Répétez ce processus pour le fichier **NativeMathSDK. props** .  
  
15. Dans **Explorateur de solutions**, sélectionnez le fichier **NativeMath. h** . Dans la fenêtre **Propriétés** , affectez à la propriété **inclure dans VSIX** la **valeur true**.  
  
     Répétez ce processus pour le fichier **NativeMath.dll** .  
  
     Répétez ce processus pour le fichier **NativeMathWRT.dll** .  
  
     Répétez ce processus pour le fichier **SDKManifest.xml** .  
  
16. Dans la barre de menus, choisissez **Générer**, puis **Générer la solution**.  
  
17. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet **NativeMathVSIX** , puis choisissez **ouvrir le dossier dans l’Explorateur de fichiers**.  
  
18. Dans l' **Explorateur de fichiers**, accédez au dossier \bin\Debug\, puis exécutez NativeMathVSIX. VSIX pour commencer l’installation.  
  
19. Choisissez le bouton **installer** , attendez que l’installation se termine, puis redémarrez Visual Studio.  
  
## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> Pour créer un exemple d’application qui utilise la bibliothèque de classes  
  
1. Dans le menu principal, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
2. Dans la liste des modèles, développez **Visual C++**, **Windows Store**, puis sélectionnez **application vide**. Dans la zone **nom** , spécifiez **NativeMathSDKSample**, puis choisissez le bouton **OK** .  
  
3. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet **NativeMathSDKSample** , puis choisissez **Ajouter**, **référence**.  
  
4. Dans la page **Propriétés communes**, **structure et références** , dans la liste des types de référence, développez **Windows**, puis sélectionnez **Extensions**. Dans le volet d’informations, sélectionnez l’extension **Native Math SDK** , puis cliquez sur le bouton **Ajouter une nouvelle référence** .  
  
5. Dans la boîte de dialogue **Ajouter une référence** , activez la case à cocher **Kit de développement logiciel (SDK) Math natif** , puis choisissez le bouton **OK** .  
  
6. Affichez les propriétés du projet pour NativeMathSDKSample.  
  
    Les propriétés que vous avez définies dans NativeMathSDK. props ont été appliquées lorsque vous avez ajouté la référence. Vous pouvez le vérifier en examinant la propriété **Répertoires VC + +** des **Propriétés de configuration**du projet.  
  
7. Dans **Explorateur de solutions**, ouvrez MainPage. xaml, puis utilisez le code XAML suivant pour remplacer son contenu :  
  
    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml#1)]  
  
8. Mettez à jour MainPage. Xaml. h pour qu’il corresponde à ce code :  
  
    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.h#2)]  
  
9. Mettez à jour MainPage. Xaml. cpp pour qu’il corresponde à ce code :  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.cpp#3)]  
  
10. Appuyez sur la touche F5 pour exécuter l’application.  
  
11. Dans l’application, entrez deux nombres, sélectionnez une opération, puis cliquez sur le **=** bouton.  
  
     Le résultat correct s’affiche.  
  
    Cette procédure pas à pas a montré comment créer et utiliser un kit de développement logiciel (SDK) d’extension pour appeler une [!INCLUDE[wrt](../includes/wrt-md.md)] bibliothèque et une non- [!INCLUDE[wrt](../includes/wrt-md.md)] bibliothèque.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : création d’un kit de développement logiciel à l’aide de C# ou Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Création d’un Kit de développement logiciel (SDK)](../extensibility/creating-a-software-development-kit.md)
