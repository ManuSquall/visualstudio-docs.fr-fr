---
title: "V&#233;rifier votre environnement Xamarin | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fd39882e-06d1-4b39-80d2-4d07b6e4f8f5
caps.latest.revision: 13
caps.handback.revision: 7
ms.author: "crdun"
manager: "crdun"
---
# V&#233;rifier votre environnement Xamarin
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Une fois les programmes d’installation terminés \(voir [Configurer et installer](../cross-platform/setup-and-install.md)\), passez quelques minutes à vérifier que tout est prêt pour expérimenter le développement Xamarin.  
  
## Toutes les plateformes  
 Créez une solution Xamarin dans Visual Studio en utilisant **Fichier \> Nouveau projet** puis, dans la boîte de dialogue, développez **Modèles \> Autres langages \> Visual C\# \>    Multiplateforme**, sélectionnez **Application vide \(Portable native\)**, puis cliquez sur OK. Ceci crée une solution avec un projet de bibliothèque de classes portable partagée et des projets individuels pour Android, iOS et Windows :  
  
 ![Résultats de la création d’un projet à partir du modèle Blank App &#40;Native Portable&#41;](../cross-platform/media/crossplat-xamarin-verify-1.png "CrossPlat Xamarin Verify 1")  
  
> [!NOTE]
>  Si les modèles ne sont pas présents, consultez [Procédure à suivre si les modèles de projet Xamarin sont manquants](#missing) en bas de cette page.  
  
## Android  
  
1.  Vérifiez le concepteur Android : dans le projet Android, dans l’Explorateur de solutions, ouvrez **Ressources \> Disposition \> Main.axml**.  
  
    -   Si vous recevez une erreur indiquant que « Le Kit de développement logiciel Android est trop ancien », cliquez sur **Open Android SDK** dans ce message, puis sélectionnez la dernière version du Kit de développement logiciel disponible. Notez que vous devez exécuter Visual Studio en tant qu’administrateur pour mettre à jour le Kit de développement logiciel.  
  
2.  Vérifiez la génération et le débogage dans l’émulateur \(ou l’appareil\) :  
  
    -   Cliquez avec le bouton droit sur le projet Android dans l’Explorateur de solutions et sélectionnez **Définir comme projet de démarrage**.  
  
         ![Option Définir comme projet de démarrage dans Visual Studio](../cross-platform/media/crossplat-xamarin-verify-2.png "CrossPlat Xamarin Verify 2")  
  
    -   Sélectionnez un émulateur approprié pour votre système d’exploitation. Si vous disposez d’un appareil de développement Android attaché à votre machine, cet appareil est également répertorié ici avec les émulateurs :  
  
        -   Windows 8\+ : sélectionnez une cible **Émulateur Visual Studio** dans le menu déroulant de débogage de Visual Studio comme illustré ci\-dessous, et démarrez le débogueur en appuyant sur **F5**. Pour plus d’informations, consultez [Introducing Visual Studio’s Emulator for Android](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/12/introducing-visual-studio-s-emulator-for-android.aspx) \(blog ALM Visual Studio\). Si vous avez des difficultés à faire fonctionner l’émulateur, consultez [Dépannage de l'émulateur Visual Studio pour Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md). Vous pouvez aussi créer de nouveaux profils d’appareil pour l’émulateur en sélectionnant **Outils \> Émulateur Visual Studio pour Android...**.  
  
             ![Sélection de l’émulateur Visual Studio pour Android comme cible de débogage](../cross-platform/media/crossplat-xamarin-verify-3.png "CrossPlat Xamarin Verify 3")  
  
        -   Pour Windows 7 et antérieur : sélectionnez à la place Xamarin Player pour Android dans la liste déroulante et appuyez sur F5 pour exécuter. Pour plus d’informations sur le lecteur Xamarin Player, son gestionnaire d’appareils et son dépannage, consultez [Xamarin Android Player](http://developer.xamarin.com/guides/android/getting_started/installation/android-player/) \(xamarin.com\).  
  
> [!NOTE]
>  Dans Visual Studio, vous pouvez remarquer la présence du bouton Gestionnaire d'émulateur Android \(AVD\) dans la barre d’outils \(illustrée ci\-dessous\). Ce bouton permet d’ouvrir le Gestionnaire d’appareils qui s’utilise en particulier pour configurer l’émulateur Android de Google.  Cela n’a aucun impact sur l’émulateur Visual Studio pour Android ou le lecteur Xamarin Player, chacun utilisant son propre gestionnaire d’appareils pour configurer des profils.  Pour plus d’informations, consultez [Introducing Visual Studio’s Emulator for Android](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/12/introducing-visual-studio-s-emulator-for-android.aspx) \(blog ALM Visual Studio\) et [Xamarin Android Player](http://developer.xamarin.com/guides/android/getting_started/installation/android-player/) \(xamarin.com\).  
> ![CrossPlat Xamarin Verify 7](../cross-platform/media/crossplat-xamarin-verify-7.png "CrossPlat Xamarin Verify 7")  
  
## Windows Phone  
  
1.  Vérifiez le concepteur Windows Phone : dans le projet Windows Phone, dans l’Explorateur de solutions, ouvrez le fichier **MainPage.xaml**.  
  
2.  Vérifiez la création et le débogage dans l’émulateur ou sur un appareil \(remarque : pour cette étape, vous devez avoir installé l’émulateur Windows Phone via le programme d’installation de Visual Studio, ou disposer d’un appareil attaché\) :  
  
    -   Cliquez avec le bouton droit sur le projet Windows Phone dans l’Explorateur de solutions et sélectionnez **Définir comme projet de démarrage**.  
  
    -   Sélectionnez une cible **Émulateur 8.1** ou un appareil attaché dans le menu déroulant du débogage de Visual Studio comme illustré ci\-dessous, et démarrez le débogueur en appuyant sur F5.  
  
         ![Sélection d’un émulateur Windows Phone comme cible de débogage](../cross-platform/media/crossplat-xamarin-verify-4.png "CrossPlat Xamarin Verify 4")  
  
    -   Si vous avez des difficultés à faire fonctionner l’émulateur, consultez [Dépannage de l’émulateur Windows Phone 8](https://msdn.microsoft.com/library/windows/apps/jj681694.aspx).  
  
## iOS  
  
1.  Assurez\-vous que votre Mac est disponible sur le réseau et apparié à Visual Studio, comme décrit dans [Connecting to the Mac](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/xamarin-mac-agent/) \(xamarin.com\).  
  
2.  Vérifiez le concepteur de plan conceptuel : dans le projet iOS, dans l’Explorateur de solutions, ouvrez le fichier **Main.storyboard**. Ici, Visual Studio héberge le concepteur qui s’exécute à distance sur le Mac.  
  
3.  Vérifiez la génération et le débogage :  
  
    1.  Cliquez avec le bouton droit sur le projet iOS dans l’Explorateur de solutions et sélectionnez **Définir comme projet de démarrage**.  
  
    2.  Sélectionnez la cible **iPhoneSimulator** dans la liste déroulante des builds de Visual Studio, comme illustré ci\-dessous, ou la cible **iPhone** si vous utilisez un appareil attaché. Si aucun simulateur ne figure dans la liste, lancez Xcode sur votre Mac, sélectionnez **Xcode \-\> Preferences**, puis cliquez sur **Download**. Sous **Components**, vous devez voir les versions de simulateur qui sont disponibles en téléchargement. Vous trouverez des instructions supplémentaires pour le débogage sur la page [Debugging](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/#Debugging_on_the_Simulator) de Xamarin \(xamarin.com\).  
  
         ![Sélection de la cible de génération iPhoneSimulator](../cross-platform/media/crossplat-xamarin-verify-5.png "CrossPlat Xamarin Verify 5")  
  
    3.  Sélectionnez une cible iPhone dans le menu déroulant du débogage de Visual Studio comme illustré ci\-dessous, et démarrez le débogueur en appuyant sur F5. Ceci lance le simulateur sur le Mac, où vous allez interagir avec l’application, alors que le débogage se fait dans Visual Studio. Si vous avez un iPhone ou iPad physique connecté au Mac, il apparaît ici. Vous pouvez le sélectionner à la place. Si aucun appareil ou simulateur ne figure dans la liste, vérifiez la connexion au Mac en consultant la rubrique liée à l’étape 1 ci\-dessus, ou en accédant à **Outils** \>**iOS** \>**Xamarin Mac Agent**.  
  
         ![Sélection d’une cible de débogage iPhone](../cross-platform/media/crossplat-xamarin-verify-6.png "CrossPlat Xamarin Verify 6")  
  
    4.  Si vous rencontrez des problèmes pour vous connecter au Mac, consultez [Connection Troubleshooting](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/xamarin-mac-agent/xma-troubleshooting/) \(xamarin.com\).  
  
    5.  Si vous recevez un message d’erreur indiquant qu’aucun profil de configuration installé ne correspond aux clés de signature iOS installées, procédez comme suit :  
  
        -   Vérifiez que votre compte ID Apple est ajouté à Xcode sur votre Mac, comme décrit dans [Adding Your Account to Xcode](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html) \(apple.com\).  Si vous ajoutez votre compte, redémarrez ensuite Visual Studio et Xcode.  
  
             ![CrossPlat Xamarin Verify 8](../cross-platform/media/crossplat-xamarin-verify-8.png "CrossPlat Xamarin Verify 8")  
  
        -   Vérifiez que, dans les propriétés de votre projet iOS, sous l’onglet iOS Bundle Signing, le champ Custom entitlements est vide pour la configuration Debug activée.  Remarque : vous pouvez essayer de supprimer ce paramètre uniquement si vous avez rencontré le message d’erreur ci\-dessus.  
  
##  <a name="missing"></a> Procédure à suivre si les modèles de projet Xamarin sont manquants  
 Un modèle peut être manquant si vous installez Xamarin directement depuis le site web de Xamarin, et que Visual Studio 2013 et Visual Studio 2015 sont installés côte à côte. C’est cependant facile à résoudre : activez simplement la fonctionnalité **Xamarin for Visual Studio 2015** dans le programme d’installation de Xamarin.  
  
1.  Dans le Panneau de configuration, ouvrez **Programmes et fonctionnalités**, sélectionnez l’élément **Xamarin** et cliquez sur **Modifier**.  
  
2.  Dans l’Assistant Installation pour Xamarin qui s’affiche, cliquez sur **Suivant**, puis sur **Modifier**.  
  
3.  Dans la liste des fonctionnalités facultatives à installer, développez **Xamarin for Visual Studio 2015**, choisissez **will be installed on local drive**, puis cliquez sur **Suivant** pour procéder à l’ajout de la fonctionnalité.