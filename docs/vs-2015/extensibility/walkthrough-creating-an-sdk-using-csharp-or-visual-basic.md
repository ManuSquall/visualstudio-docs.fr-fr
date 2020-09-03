---
title: 'Procédure pas à pas : création d’un kit de développement logiciel (SDK) en C# ou Visual Basic | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a604e3500c0ea438c987c4cf07ded98a5e03dd61
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77558208"
---
# <a name="walkthrough-creating-an-sdk-using-c-or-visual-basic"></a>Procédure pas à pas : création d’un SDK en C# ou Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans cette procédure pas à pas, vous allez apprendre à créer un kit de développement logiciel (SDK) de bibliothèque mathématique simple à l’aide de Visual C#, puis à empaqueter le kit de développement logiciel en tant qu’extension Visual Studio (VSIX). Vous allez effectuer les procédures suivantes :  
  
- [Pour créer le composant Windows Runtime SimpleMath](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)  
  
- [Pour créer le projet d’extension SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)  
  
- [Pour créer un exemple d’application qui utilise la bibliothèque de classes](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)  
  
## <a name="prerequisites"></a>Prérequis  
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [Kit de développement logiciel (SDK) Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="to-create-the-simplemath-windows-runtime-component"></a><a name="createClassLibrary"></a> Pour créer le composant Windows Runtime SimpleMath  
  
1. Dans la barre de menus, choisissez **fichier**, **nouveau**, **nouveau projet**.  
  
2. Dans la liste des modèles, développez **Visual C#** ou **Visual Basic**, choisissez le nœud **Windows Store** , puis choisissez le modèle de **composant Windows Runtime** .  
  
3. Dans la zone **nom** , spécifiez **SimpleMath**, puis choisissez le bouton **OK** .  
  
4. Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de projet **SimpleMath** , puis choisissez **Propriétés**.  
  
5. Renommez **Class1.cs** en **Arithmetic.cs** et mettez-le à jour pour qu’il corresponde au code suivant :  
  
     [!code-csharp[CreatingAnSDKUsingWinRT#3](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmath/arithmetic.cs#3)]
     [!code-vb[CreatingAnSDKUsingWinRT#3](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmath/arithmetic.vb#3)]  
  
6. Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud **« SimpleMath »** de la Solution, puis choisissez **Configuration Manager**.  
  
     La boîte de dialogue **Configuration Manager** s’ouvre.  
  
7. Dans la liste Configuration de la **solution active** , choisissez **version**.  
  
8. Dans la colonne **configuration** , vérifiez que **SimpleMath** Row est défini sur **Release**, puis choisissez le bouton **Fermer** pour accepter la modification.  
  
    > [!IMPORTANT]
    > Le kit de développement logiciel (SDK) pour le composant SimpleMath n’intègre qu’une seule configuration. Cette configuration doit être la version Release, ou les applications qui utilisent le composant ne passeront pas la certification pour le [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)] .  
  
9. Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de projet **SimpleMath** , puis choisissez **générer**.  
  
## <a name="to-create-the-simplemathvsix-extension-project"></a><a name="createVSIX"></a> Pour créer le projet d’extension SimpleMathVSIX  
  
1. Dans le menu contextuel du nœud **« SimpleMath »** de la solution, choisissez **Ajouter**, puis **nouveau projet**.  
  
2. Dans la liste des modèles, développez **Visual C#** ou **Visual Basic**, choisissez le nœud **extensibilité** , puis choisissez le modèle de **projet VSIX** .  
  
3. Dans la zone **nom** , spécifiez **SimpleMathVSIX**, puis choisissez le bouton **OK** .  
  
4. Dans **Explorateur de solutions**, choisissez l’élément **source. extension. vsixmanifest** .  
  
5. Dans la barre de menus, sélectionnez **Afficher**, **Code**.  
  
6. Remplacez le code XML existant par le code XML suivant :  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]
  
7. Dans **Explorateur de solutions**, choisissez le projet **SimpleMathVSIX** .  
  
8. Dans la barre de menus, choisissez **projet**, **Ajouter un nouvel élément**.  
  
9. Dans la liste des **éléments communs**, développez **données**, puis choisissez **fichier XML**.  
  
10. Dans la zone **nom** , spécifiez `SDKManifest.xml` , puis cliquez sur le bouton **Ajouter** .  
  
11. Dans **Explorateur de solutions**, ouvrez le menu contextuel de `SDKManifest.xml` , choisissez **Propriétés**, puis remplacez la valeur de la propriété **inclure dans VSIX** par **true**.  
  
12. Remplacez le contenu du fichier par le code XML suivant :  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmathvsix/sdkmanifest.xml#1)]
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmathvsix/sdkmanifest.xml#1)]  
  
13. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet **SimpleMathVSIX** , choisissez **Ajouter**, puis **nouveau dossier**.  
  
14. Renommez le dossier `references` .  
  
15. Ouvrez le menu contextuel du dossier **références** , cliquez sur **Ajouter**, puis choisissez **nouveau dossier**.  
  
16. Renommez le sous-dossier `commonconfiguration` , créez un sous-dossier dans celui-ci, puis nommez-le `neutral` .  
  
17. Répétez les quatre étapes précédentes, en renommant le premier dossier en `redist` .  
  
     Le projet contient maintenant la structure de dossiers suivante :  
  
    ```  
    references\commonconfiguration\neutral  
    redist\commonconfiguration\neutral  
    ```  
  
18. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet **SimpleMath** , puis choisissez **ouvrir le dossier dans l’Explorateur de fichiers**.  
  
19. Dans l' **Explorateur de fichiers**, accédez au dossier bin\Release, ouvrez le menu contextuel du fichier SimpleMath. winmd, puis choisissez **copier**.  
  
20. Dans **Explorateur de solutions**, collez le fichier dans le dossier references\commonconfiguration\neutral du projet **SimpleMathVSIX** .  
  
21. Répétez l’étape précédente, en collant le fichier SimpleMath. pri dans le dossier redist\commonconfiguration\neutral du projet **SimpleMathVSIX** .  
  
22. Dans **Explorateur de solutions**, choisissez **SimpleMath. winmd**.  
  
23. Dans la barre de menus, choisissez **Afficher**, **Propriétés** (clavier : Appuyez sur la touche F4).  
  
24. Dans la fenêtre **Propriétés** , affectez à la propriété **action de génération** la valeur **contenu**, puis remplacez la propriété **inclure dans VSIX** par **true**.  
  
25. Dans **Explorateur de solutions**, répétez ce processus pour **SimpleMath. pri**.  
  
26. Dans **Explorateur de solutions**, choisissez le projet **SimpleMathVSIX** .  
  
27. Dans la barre de menus, choisissez **générer**, **générer SimpleMathVSIX**.  
  
28. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet **SimpleMathVSIX** , puis choisissez **ouvrir le dossier dans l’Explorateur de fichiers**.  
  
29. Dans l' **Explorateur de fichiers**, accédez au dossier \bin\release, puis exécutez SimpleMathVSIX. VSIX pour l’installer.  
  
30. Choisissez le bouton **installer** , attendez que l’installation se termine, puis redémarrez Visual Studio.  
  
## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> Pour créer un exemple d’application qui utilise la bibliothèque de classes  
  
1. Dans la barre de menus, choisissez **fichier**, **nouveau**, **nouveau projet**.  
  
2. Dans la liste des modèles, développez **Visual C#** ou **Visual Basic**, puis choisissez le nœud **Windows Store** .  
  
3. Choisissez le modèle **application vide** , nommez le projet **ArithmeticUI**, puis choisissez le bouton **OK** .  
  
4. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet **ArithmeticUI** , puis choisissez **Ajouter**, **référence**.  
  
5. Dans la liste des types de référence, développez **Windows**, puis choisissez **Extensions**.  
  
6. Dans le volet d’informations, choisissez l’extension **Math SDK simple** .  
  
    Des informations supplémentaires sur votre kit de développement logiciel (SDK) s’affichent. Vous pouvez choisir le lien **plus d’informations** à ouvrir https://docs.microsoft.com , comme vous l’avez spécifié dans le fichier SDKManifest.xml plus haut dans cette procédure pas à pas.  
  
7. Dans la boîte de dialogue **Gestionnaire de références** , activez la case à cocher **simple Math SDK** , puis cliquez sur le bouton **OK** .  
  
8. Dans la barre de menus, choisissez **Afficher**, **Explorateur d’objets**.  
  
9. Dans la liste **Parcourir** , choisissez **Math simple**.  
  
     Vous pouvez maintenant explorer ce qui se trouve dans le kit de développement logiciel (SDK).  
  
10. Dans **Explorateur de solutions**, ouvrez MainPage. xaml et remplacez son contenu par le code XAML suivant :  
  
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml#1)]
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml#1)]  
  
11. Mettez à jour MainPage.xaml.cs pour qu’il corresponde au code suivant :  
  
     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml.cs#2)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml.vb#2)]  
  
12. Appuyez sur la touche F5 pour exécuter l’application.  
  
13. Dans l’application, entrez deux nombres, choisissez une opération, puis cliquez sur le **=** bouton.  
  
     Le résultat correct s’affiche.  
  
    Vous avez créé et utilisé avec succès un kit de développement logiciel (SDK) d’extension.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : création d’un SDK à l’aide de C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [Procédure pas à pas : création d’un SDK à l’aide de JavaScript](walkthrough-creating-an-sdk-using-javascript.md)   
 [Création d’un Kit de développement logiciel (SDK)](../extensibility/creating-a-software-development-kit.md)
