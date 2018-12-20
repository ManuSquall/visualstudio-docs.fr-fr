---
title: 'Procédure pas à pas : Création d’un kit de développement à l’aide de c# ou Visual Basic | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3e0bc88c8581b29f43e7efc55ee86019e1f1c3fb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736755"
---
# <a name="walkthrough-creating-an-sdk-using-c-or-visual-basic"></a>Procédure pas à pas : création d’un SDK en C# ou Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans cette procédure pas à pas, vous allez apprendre à créer un kit de développement de bibliothèque mathématique simple à l’aide de Visual c#, puis d’empaqueter le Kit de développement logiciel en tant qu’une Extension Visual Studio (VSIX). Vous allez effectuer les procédures suivantes :  
  
-   [Pour créer le composant SimpleMath Windows Runtime](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)  
  
-   [Pour créer le projet d’extension SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)  
  
-   [Pour créer un exemple d’application qui utilise la bibliothèque de classes](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)  
  
## <a name="prerequisites"></a>Prérequis  
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createClassLibrary"></a> Pour créer le composant SimpleMath Windows Runtime  
  
1.  Dans la barre de menus, choisissez **fichier**, **New**, **nouveau projet**.  
  
2.  Dans la liste des modèles, développez **Visual C#** ou **Visual Basic**, choisissez le **Windows Store** nœud, puis choisissez le **composant d’exécution Windows** modèle.  
  
3.  Dans le **nom** , spécifiez **SimpleMath**, puis choisissez le **OK** bouton.  
  
4.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **SimpleMath** nœud de projet, puis choisissez **propriétés**.  
  
5.  Renommer **Class1.cs** à **Arithmetic.cs** et mettre à jour pour correspondre à ce qui suit :  
  
     [!code-csharp[CreatingAnSDKUsingWinRT#3](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmath/arithmetic.cs#3)]
     [!code-vb[CreatingAnSDKUsingWinRT#3](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmath/arithmetic.vb#3)]  
  
6.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **Solution 'SimpleMath'** nœud, puis choisissez **Configuration Manager**.  
  
     Le **Configuration Manager** boîte de dialogue s’ouvre.  
  
7.  Dans le **configuration de solution Active** , choisissez **version**.  
  
8.  Dans le **Configuration** colonne, vérifiez que **SimpleMath** ligne est définie sur **version**, puis choisissez le **fermer** bouton pour accepter le modifier.  
  
    > [!IMPORTANT]
    >  Le Kit de développement pour le composant SimpleMath ne comprend qu’une seule configuration. Cette configuration doit être la version Release, ou les applications qui utilisent le composant ne sont pas passer la certification le[!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)].  
  
9. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **SimpleMath** nœud de projet, puis choisissez **Build**.  
  
##  <a name="createVSIX"></a> Pour créer le projet d’extension SimpleMathVSIX  
  
1.  Dans le menu contextuel pour le **Solution 'SimpleMath'** nœud, choisissez **ajouter**, **nouveau projet**.  
  
2.  Dans la liste des modèles, développez **Visual C#** ou **Visual Basic**, choisissez le **extensibilité** nœud, puis choisissez le **projet VSIX** modèle.  
  
3.  Dans le **nom** , spécifiez **SimpleMathVSIX**, puis choisissez le **OK** bouton.  
  
4.  Dans **l’Explorateur de solutions**, choisissez le **source.extension.vsixmanifest** élément.  
  
5.  Dans la barre de menus, sélectionnez **Afficher**, **Code**.  
  
6.  Remplacez le code XML existant par le code XML suivant :  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]
  
7.  Dans **l’Explorateur de solutions**, choisissez le **SimpleMathVSIX** projet.  
  
8.  Dans la barre de menus, choisissez **projet**, **ajouter un nouvel élément**.  
  
9. Dans la liste des **éléments communs**, développez **données**, puis choisissez **fichier XML**.  
  
10. Dans le **nom** , spécifiez `SDKManifest.xml`, puis choisissez le **ajouter** bouton.  
  
11. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour `SDKManifest.xml`, choisissez **propriétés**, puis modifiez la valeur de la **inclure dans VSIX** propriété **True**.  
  
12. Remplacez le contenu du fichier par le code XML suivant :  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmathvsix/sdkmanifest.xml#1)]
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmathvsix/sdkmanifest.xml#1)]  
  
13. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **SimpleMathVSIX** de projet, choisissez **ajouter**, puis choisissez **nouveau dossier**.  
  
14. Renommez le dossier `references`.  
  
15. Ouvrez le menu contextuel pour le **références** dossier, choisissez **ajouter**, puis choisissez **nouveau dossier**.  
  
16. Renommez le sous-dossier à `commonconfiguration`, créez un sous-dossier qu’il contient et nommez le sous-dossier `neutral`.  
  
17. Répétez les quatre étapes précédentes, cette fois le premier dossier à renommé `redist`.  
  
     Le projet contient maintenant la structure de dossiers suivante :  
  
    ```  
    references\commonconfiguration\neutral  
    redist\commonconfiguration\neutral  
    ```  
  
18. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **SimpleMath** de projet, puis choisissez **ouvrir le dossier dans l’Explorateur de fichiers**.  
  
19. Dans **Explorateur de fichiers**, accédez au dossier bin\Release, ouvrez le menu contextuel pour le fichier SimpleMath.winmd, puis choisissez **copie**.  
  
20. Dans **l’Explorateur de solutions**, collez le fichier dans le dossier references\commonconfiguration\neutral dans le **SimpleMathVSIX** projet.  
  
21. Répétez l’étape précédente, en collant le fichier SimpleMath.pri dans le dossier redist\commonconfiguration\neutral dans le **SimpleMathVSIX** projet.  
  
22. Dans **l’Explorateur de solutions**, choisissez **SimpleMath.winmd**.  
  
23. Dans la barre de menus, choisissez **vue**, **propriétés** (clavier : appuyez sur la touche F4).  
  
24. Dans le **propriétés** fenêtre, la modification la **Action de génération** propriété **contenu**, puis modifiez le **inclure dans VSIX** propriété  **True**.  
  
25. Dans **l’Explorateur de solutions**, répétez ce processus pour **SimpleMath.pri**.  
  
26. Dans **l’Explorateur de solutions**, choisissez le **SimpleMathVSIX** projet.  
  
27. Dans la barre de menus, choisissez **Build**, **SimpleMathVSIX Build**.  
  
28. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **SimpleMathVSIX** de projet, puis choisissez **ouvrir le dossier dans l’Explorateur de fichiers**.  
  
29. Dans **Explorateur de fichiers**, accédez au dossier \bin\Release, puis exécutez SimpleMathVSIX.vsix pour l’installer.  
  
30. Choisissez le **installer** bouton, attendez que l’installation se termine, puis redémarrez Visual Studio.  
  
##  <a name="createSample"></a> Pour créer un exemple d’application qui utilise la bibliothèque de classes  
  
1. Dans la barre de menus, choisissez **fichier**, **New**, **nouveau projet**.  
  
2. Dans la liste des modèles, développez **Visual C#** ou **Visual Basic**, puis choisissez le **Windows Store** nœud.  
  
3. Choisissez le **application vide** modèle, nommez le projet **ArithmeticUI**, puis choisissez le **OK** bouton.  
  
4. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **ArithmeticUI** de projet, puis choisissez **ajouter**, **référence**.  
  
5. Dans la liste des types référence, développez **Windows**, puis choisissez **Extensions**.  
  
6. Dans le volet de détails, choisissez le **Simple mathématiques SDK** extension.  
  
    Des informations supplémentaires sur votre Kit de développement logiciel s’affiche. Vous pouvez choisir le **plus d’informations** lien pour ouvrir http://www.msdn.microsoft.com, que vous avez spécifié dans le fichier SDKManifest.xml plus haut dans cette procédure pas à pas.  
  
7. Dans le **Gestionnaire de références** boîte de dialogue, sélectionnez le **Simple mathématiques SDK** case à cocher, puis choisissez le **OK** bouton.  
  
8. Dans la barre de menus, choisissez **vue**, **Explorateur d’objets**.  
  
9. Dans le **Parcourir** , choisissez **mathématiques simples**.  
  
     Vous pouvez maintenant Explorer Nouveautés dans le Kit de développement.  
  
10. Dans **l’Explorateur de solutions**, ouvrez MainPage.xaml et remplacez son contenu par le XAML suivant :  
  
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml#1)]
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml#1)]  
  
11. Mettre à jour de MainPage.xaml.cs pour faire correspondre le code suivant :  
  
     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml.cs#2)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml.vb#2)]  
  
12. Appuyez sur la touche F5 pour exécuter l’application.  
  
13. Dans l’application, entrez tous les deux numéros, choisissez une opération, puis le **=** bouton.  
  
     Le résultat correct apparaît.  
  
    Vous avez correctement créé et utilisé un SDK d’Extension.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Création d’un kit de développement à l’aide de C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [Procédure pas à pas : Création d’un kit de développement à l’aide de JavaScript](http://msdn.microsoft.com/en-us/6195ff56-4a27-45fc-bd29-4b0451225f4b)   
 [Création d’un Kit de développement logiciel (SDK)](../extensibility/creating-a-software-development-kit.md)

